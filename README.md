# Ricoh-Theta-S-Cordova
##IF YOU VALUE YOUR SANITY AT ALL MAKE SURE YOUR RICOH FIRMWARE IS UP TO DATE!
###Also, this code really sucks and probably shouldn't be used in a production environemt, it hasn't been tested other than me making sure I think it does what it should do. It's just a proof of concept.I'm putting this out there because I really just couldn't find anyone else doing anything like this other than some hints that it was possible. 

This requires 2 Cordova Plugins: 

http-advanced-2 (allows us to set JSON data in a post request instead of FORM data)
https://github.com/silkimen/cordova-plugin-advanced-http


wifiwizard to do cool wifiy stuff. This isn't IOS compatible as far as I can tell...who knows apple sucks.
Wifi Wizard Plugin from here: https://github.com/hoerresb/WifiWizard

This really just helps simplify the connection process. In the code, it searches for the Theta wifi SSID, pulls out the serial number and uses that for the password. This won't work if the password or SSID has been changed (not sure if it is possible to change the SSID). 

2) I'm using Sencha EXTJS 6 Modern framework for building the app UI. So you'll see some references below on those pieces. (Ext.VIewport and stuff, totally not needed for most people).


So whats my thought process here on this code step by step:

1a) simply scan for the Wifi (Theta.connectToTheta())

1b) Find a Theta wifi (Theta.ScaForWiFiAPs())

1c) Connect To Theta Wifi. Grab the serial number for the password. Connect to the Theta Wifi (Theta.connectToThetaWifi())


2)Start the camera session (Theta.initCameraConnection() calls Theta.startCameraSession())

3) Set the API level (Theta.setThetaAPILevel(), this always set to level 2)

4) Grab a picture (Theta.takePhoto())

5) List the files into a view (Theta.getThetaFileList())

6) Get a selected photo onto the device(Theta.downloadCameraPhotoToDevice(file_url))

7) Remove the photo from the Theta (Theta.deleteFileFromTheta(file))

In theory this should connect with more than the Ricoh Theta S, it's not really doing much Theta S specific. And the Theta conforms to Googles OSC Open Spherical Camera API. So maybe Bubbler and Samsung Gear 360 can be made to work with relative ease (I had the Gear 360 and didn't really like how it had to be put into OSC mode every start up...wasn't very "tool" friendly so much as a neat gadget. Also the gear 360 doesn't do on device stiching I don't think, so you have to figure that out your self.)
