// Copyright (c) 2014, the Dart project authors.  Please see the AUTHORS file
// for details. All rights reserved. Use of this source code is governed by a
// BSD-style license that can be found in the LICENSE file.

# org.dartlang.phonegap.gyroscope

This plugin provides access to the device's gyroscope.

## Installation

    cordova plugin add org.dartlang.phonegap.gyroscope

## Supported Platforms

- Android

## Methods

- navigator.gyroscope.getCurrentAngularSpeed
- navigator.gyroscope.watchAngularSpeed
- navigator.gyroscope.clearWatch

## Objects

- AngularSpeed

## navigator.gyroscope.getCurrentAngularSpeed

Get the current angular speed.

The speed values are returned to the `gyroscopeSuccess`
callback function.

    navigator.gyroscope.getCurrentAngularSpeed(gyroscopeSuccess, gyroscopeError);


### Example

    function onSuccess(speed) {
        alert('AngularSpeed:\n'
              'x: ' + speed.x + '\n' +
              'y: ' + speed.y + '\n' +
              'z: ' + speed.z + '\n' +
              'Timestamp: ' + speed.timestamp + '\n');
    };

    function onError() {
        alert('onError!');
    };

    navigator.gyroscope.getCurrentAngularSpeed(onSuccess, onError);

## navigator.gyroscope.watchAngularSpeed

Retrieves the device's current `AngularSpeed` at a regular interval, executing
the `gyroscopeSuccess` callback function each time. Specify the interval in
milliseconds via the `gyroscopeOptions` object's `frequency` parameter.

The returned watch ID references the gyroscopes's watch interval,
and can be used with `navigator.gyroscope.clearWatch` to stop watching the
gyroscope.

    var watchID = navigator.gyroscope.watchAngularSpeed(gyroscopeSuccess,
                                                        gyroscopeError,
                                                       [gyroscopeOptions]);

- __gyroscopeOptions__: An object with the following optional keys:
- __frequency__: How often to retrieve the `AngularSpeed` in milliseconds. _(Number)_ (Default: 10000)


###  Example

    function onSuccess(speed) {
        alert('AngularSpeed:\n'
              'x: ' + speed.x + '\n' +
              'y: ' + speed.y + '\n' +
              'z: ' + speed.z + '\n' +
              'Timestamp: ' + speed.timestamp + '\n');
    };

    function onError() {
        alert('onError!');
    };

    var options = { frequency: 3000 };  // Update every 3 seconds

    var watchID = navigator.gyroscope.watchAngularSpeed(onSuccess, onError, options);

## navigator.gyroscope.clearWatch

Stop watching the `AngularSpeed` referenced by the `watchID` parameter.

    navigator.gyroscope.clearWatch(watchID);

- __watchID__: The ID returned by `navigator.gyroscope.watchAngularSpeed`.

###  Example

    var watchID = navigator.gyroscope.watchAngularSpeed(onSuccess, onError, options);

    // ... later on ...

    navigator.gyroscope.clearWatch(watchID);

## AngularSpeed

Contains `AngularSpeed` data captured at a specific point in time.

### Properties

- __x__: Angular speed around the x-axis. _(Number)_
- __y__: Angular speed around the y-axis. _(Number)_
- __z__: Angular speed around the z-axis. _(Number)_
- __timestamp__: Creation timestamp in milliseconds. _(DOMTimeStamp)_
