---
title: "Sane not recognising my digital camera"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by LPLPACA on 2008-04-04
Hi, v noob here, 

dell d630 - running 8.04 beta

previous I have 7.10 on the same machine and could attach the usb HP 945 digital camera without any problems, automatically recognised and asking if I wanted to grab the images off the camera.

I am purely M$ before this apart from a small amount of red hat setup but that is all.

I was advised by my colleague to try the new beta version 8.04 so wiped what I had already played around with and did a fresh install of it. I have come across a few problems with display and with wifi but following threads in this great forum have fixed the problems without too much hassle

The problem I have, and this is not mega urgent as I found a workaround, is that when I plug the camera in, I get a message up saying no scanner detected - I click on help and it advises me about SANE, I have checked and it is loaded, it does has USB support loaded and if trying to detect in terminal using the sudo command it still cannot find the camera.

I installed gthumb and this can grab the images off the camera without a prblem, so I know it is not hardware, so can only think I don't have something with SANE quite right - a little bit of guidance or advise would be much appreciated.

Just an afterthought, I am wondering because this is the beta version that the drivers for this camera are not loaded or made yet?

rgds

Paul C

---

### Post by aeiah on 2008-04-04
im confused. your digital camera shouldnt need any drivers; ubuntu should see it just as an external storage device, or perhaps recognise it as a camera, but the file transfer will always be the same as if it was a usb stick, or a memory card in a memory card reader.

sane is for scanners. i dont know why its popping up with your camera, but there should be a way to stop it, since its a problem with sane mistaking your camera for a scanner. what do you do when you plug your camera in? is there an option on the camera to 'push' the photos onto the pc? (as opposed to the normal mode of having it as a usb storage device). perhaps selecting that is causing an issue

---

### Post by LPLPACA on 2008-04-04
standard usb connection for the camera, I plug in the cable to the usb port, and into the camera, power on the camera and I get a 'scanning devices' window popup, this changes to 'no devices found' with a close and help button to click.

CLOSE is the obvious, HELP gives another window with the following text

no devices available

Possible Reasons:
1) There really is no device that is supported by SANE
2) Supported devices are busy
3) The permissions for the device file do not allow you to use it - try as root
4) The backend is not loaded by SANE(man sane-dll)
5) The backend is not configuredcorrectly (man sane-"backendname")
6) Possibly there is more than one SANE version installed

And a CLOSE button at the bottom

Am I missing another detector that should be picking up the camera?

rgds

---

### Post by aeiah on 2008-04-04
does it auto-mount as normal as well?

---

### Post by LPLPACA on 2008-04-04
Yes it mounts, I just checked, and I can either manually take the pics off or launch gthumb to take them off for me, I guess I worded my question wrong, what happened in 7.10 was that it also automatically came up to ask me if I wanted to get the pictures off the camera, I guess I need to set an app to come up like this, the SANE popup box is what has thrown me tho.

rgds

---

### Post by MrFSL on 2008-04-04
> what happened in 7.10 was that it also automatically came up to ask me if I wanted to get the pictures off the camera, I

I do believe that in  Hardy, the default GThumb method of retrieving pictures by default:
```
gnome-volume-manager-gthumb %h
```

..was replaced by f-spot's import function. You can check this by going System > Preferences > Removable Drives And Media     then clicking on the "Camera" Tab.

Not sure why this is like this. Personally I hate F-Spot and uninstall it.

---

### Post by LPLPACA on 2008-04-04
The preferences for camera had nothing set, I have set the camera action so that gthumb will automatically come up to retrieve the pictures

one more question I have is why would SANE think my camera is a scanner?

thanks peeps

great help

---

### Post by philinux on 2008-04-04
> **MrFSL said:**
> I do believe that in  Hardy, the default GThumb method of retrieving pictures by default:
```
gnome-volume-manager-gthumb %h
```

..was replaced by f-spot's import function. You can check this by going System > Preferences > Removable Drives And Media     then clicking on the "Camera" Tab.

Not sure why this is like this. Personally I hate F-Spot and uninstall it.

In Hardy some of this is now in Nautilus. Why it's been split up i dont know.

When file browsing - edit > Preferences now has a media tab. I unistalled f-spot and now under photos it says no application found. :confused: Like gimp and gthumb are installed.

---

### Post by LPLPACA on 2008-04-04
> **philinux said:**
> In Hardy some of this is now in Nautilus. Why it's been split up i dont know.

When file browsing - edit > Preferences now has a media tab. I unistalled f-spot and now under photos it says no application found. :confused: Like gimp and gthumb are installed.

Right, as above, I changed the system media manager to import photos with GThumb, and then I changed the nautilus option to ask what to do.

It nows comes up as it used to in 7.10, ie it detects the camera, and then asks do I want to import the pics - yeah BUT

I still get the NO DEVICES AVAILABLE window from SANE - so my next question is - how do I stop that?

rgds

Paul C

---

