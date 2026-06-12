---
title: "Unable to mount iPhone unhandled lockdown error"
date: 2014-06-09
forum: Any Other OS
---

### Post by shota2 on 2014-06-09
Hi guys I need your help, have some problem here with iPhone 
[COLOR=#333333][FONT=UbuntuRegular]I get this error when plugging in my iPhone:
[/FONT][/COLOR]Unable to mount iPhone unhandled lockdown error (-20)
I allready have installed libimobiledevice4 gvfs libimobiledevice-utils ifuse
I tryed idevicepair unpair && idevicepair pair but
ERROR: Device bfa4a4e976231cb442f69559fea4838955446660 is not paired with this host
and still have problem
any ideas?

---

### Post by nadarockyraccoon on 2014-06-22
What version of ubuntu are you using?
What method did you use to install libmobiledevice?
Any how the standard libimobiledevice4 doesn't work with ios7+. Check out [http://itsfoss.com/mount-iphone-ipad-ios-7-ubuntu-13-10/]("http://itsfoss.com/mount-iphone-ipad-ios-7-ubuntu-13-10/"), there is a tutoriol for ubuntu 13.10 and previous. I'm finding out if compiling from [https://github.com/libimobiledevice/libimobiledevice]("https://github.com/libimobiledevice/libimobiledevice") works in 14.04. curious if the .deb package works though.

---

### Post by nadarockyraccoon on 2014-06-22
Well the compile got a bit messy, too many unsatisfied dependencies. Likely would have been easy to get around, but why muck it up when there is a ready to use debian package? 

In 14.04 I had to install libtans1-3 found at [http://packages.ubuntu.com/saucy/libtasn1-3]("http://packages.ubuntu.com/saucy/libtasn1-3"). Then I installed the pre-packaged .deb from [https://launchpadlibrarian.net/161677269/libimobiledevice4_1.1.6-git20140105_amd64.deb]("https://launchpadlibrarian.net/161677269/libimobiledevice4_1.1.6-git20140105_amd64.deb") for ubuntu 13.10. There may be a newer version, but this worked great for me. 

If you are confused about how to manually install a .deb check out [http://askubuntu.com/questions/40779/how-do-i-install-a-deb-file-via-the-command-line]("http://askubuntu.com/questions/40779/how-do-i-install-a-deb-file-via-the-command-line"). You also could use gdebi found in the package manager. Once installed right click the package to open with gdebi and install.

If however you have done these things and it is still not working then you are part of what appears to be an ongoing bug that some how isn't fixed for you and you should plug the device in, open a terminal and type ubuntu-bug linux and follow the ongoing bug report [https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/1215098]("https://bugs.launchpad.net/ubuntu/+source/libimobiledevice/+bug/1215098").

Also filemanager available in the app store on your device allows wifi syncing, obnoxious i know, but you can get files on and off the device with out plugging in.

---

### Post by Dthrill on 2014-12-02
Plug your iphone while unlocked (unlock lockscreen) ,Or try to Unlock your Iphone if u have passcode, after that a dialog box should pop on you iphone click Trust then it should work... 
If not try this command on terminal
sudo chmod 777 /var/lib/lockdown

if the folder doesnt exist

sudo mkdir /var/lib/lockdown    and then chmod it to 777 with the above command...

---

### Post by Scarbs on 2014-12-24
> **Dthrill said:**
> Plug your iphone while unlocked (unlock lockscreen) ,Or try to Unlock your Iphone if u have passcode, after that a dialog box should pop on you iphone click Trust then it should work... 
If not try this command on terminal
sudo chmod 777 /var/lib/lockdown

if the folder doesnt exist

sudo mkdir /var/lib/lockdown    and then chmod it to 777 with the above command...

Hi, iPhone 5 connects to Ubuntu 14 but gives error 'Unhandled Lockdown error (-3)'  Using Banshee Media Player I can copy music files and see how much data is on my phone but cannot get music to be recognised by phone once it's disconnected.

Any suggestions please?

---

### Post by d4m1r on 2015-01-25
If you get “lock down error”, try using the following commands:

 ```
sudo mkdir /var/lib/lockdown
sudo chmod 777 /var/lib/lockdown
```

---

### Post by vigyani on 2015-06-06
Hi
This worked.
Thanks

> **d4m1r said:**
> If you get “lock down error”, try using the following commands:

 ```
sudo mkdir /var/lib/lockdown
sudo chmod 777 /var/lib/lockdown
```

---

### Post by ben-ronlund on 2016-01-22
Just thought I'd let you guys know, I had an issue with Linux Mint 17.3 and iPhone 4S/IOS 8.1. I haven't installed any packages just vanilla. I got error:
unable to mount iphone unhandled lockdown error (-21)

I tried to run
idevicepair unpair && idevicepair pair

This however only changed the error code, same message different number, i.e. (-x)

Once I turned off hotspot it was able to connect automatically. This was however with the phone screen unlocked while plugging it then clicking trust then browsing to drive within nemo.

---

### Post by darrellakitchen on 2016-03-30
> **d4m1r said:**
> If you get “lock down error”, try using the following commands:

```
sudo mkdir /var/lib/lockdown
sudo chmod 777 /var/lib/lockdown
```

If you have successfully completed the above suggestion and am able to use your iOS device, but after some time error (-20) pops up again, delete the contents of /var/lib/lockdown, ensure your iOS device is on and at the home screen, plug the iOS device into your computer, answer the prompt on your device to allow your computer access to your device. Either unplug the device and plug it back in or at a command prompt type "idevicepair pair".

---

