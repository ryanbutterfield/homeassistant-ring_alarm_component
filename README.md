# Ring alarm component
Custom Component for integration with Home Assistant

# Installation
1. Open the directory for your HA configuration where the configuration.yaml file exists
2. If you do not have a custom_components directory there, you need to create it
3. In the custom_components directory create a new folder called ring_alarm
4. Download the zip from this repository
5. Place the files you downloaded in the new directory (ring_alarm) you created
6. Restart Home Assistant
 
# Configuration
To be added in the configuration.yaml file, username/password is the ring alarm username and password

    # configuration.yaml entry
    ring_alarm:     
      username: 'username'
      password: 'password'

# Features
These are the devices supported in the Ring Alarm:
- Ring lighting
    - Floodlight wired
        - Creates 1 binary sensor for motion detection and 1 switch for the lights
    - Motion sensor
    - Transformer
    - Others might work but can't test
- Ring security
    - Ring Contact and Motion Sensors
    - Ring Flood/Freeze Sensor 
    - Ring Smoke/CO Listener - Possibly supports, can't test
    - First Alert Z-Wave Smoke/CO Detector - more testing needed
    - Ring Alarm integrated door locks (status and lock control)
    - Ring Alarm Panel (Arm, Disarm, Home)

In addition the following attributes are available:
- Battery level, if available
- Tamper status for supported devices 
- Location name
- ZID (its a unique id that each Ring device has)
- Last update received from the device
 
# Issues
1. This component uses some other python modules, all of them install automatically except for python-socketio which I install within the component. 
Once I trace the problem will try to remove the manual installation. Not sure if this creates problems in Hassio since i use the installed python to install the pip modules
2. All components need more extensive error checking
3. Recoverability is not good, when for example the Ring Alarm goes into cellular back or is offline when initially trying to connect
4. Assume there needs to be more extensive testing and not be dependent solely on the status produced by this compoonent
5. While I have support for multiple locations/alarms have not tested it out. 
6. This is first attempt at Home Assistant component programming and learning python at the same time, so I expect coding standards will be terrible!

# Credits
There are multiple people out there from whose code I learnt a lot especially on the ring api. Specifically, would like to call out:
- https://github.com/dgreif/ring