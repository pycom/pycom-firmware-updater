# Snap

##Installation

1. `sudo snap install pycom-firmware-updater`

2. `sudo snap set system experimental.hotplug=true`

3. `sudo systemctl restart snapd`

4. type `snap interface serial-port`. In the output you will see slots 
   section. For example:
   
   name: serial-port

   summary: allows accessing a specific serial port

   plugs:
   - pycom-firmware-updater
   
   slots:
   - snapd:expansion3 (allows accessing a specific serial port)

5. `sudo snap connect pycom-firmware-updater:serial-port snapd:expansion3`.
   snapd:expansion3 is the name of the hotplug slot from 
   the command above. If you have some other name paste it instead.
6. `snap connect pycom-firmware-updater:raw-usb`
7. run `snap connections pycom-firmware-updater` in the 3d(Slot) column on 
   the raw-usb and serial-port lines shouldn't be '-'.
8. run the app by typing `pycom-firmware-updater`.


##Common Problems
If you have the `[Errno 1] Operation not permitted: '/tmp/fwUpdater.pem'` 
error log do next:
`sudo rm -rf /tmp/snap.pycom-firmware-updater/tmp/fwUpdater.pem`
