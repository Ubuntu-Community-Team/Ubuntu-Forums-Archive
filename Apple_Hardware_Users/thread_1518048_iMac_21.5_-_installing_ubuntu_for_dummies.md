---
title: "iMac 21.5 - installing ubuntu for dummies"
date: 2010-06-26
forum: Apple Hardware Users
---

### Post by ashwindatye on 2010-06-26
Update: read my last reply below to this for ubuntu 10.10.... works even better than 10.04 on iMac

-----------------------

I have managed to install ubuntu 10.04 (linux mint 9) on my new iMac 21.5" machine. I think i got everything working. Here's how:

1. Main installation: Run boot camp and make a new partition. Then I booted from CD by holding the "option" key down at the start. After a few basic checks like Wifi I decided to install. I had no issues with the installation. I managed to boot into linux by holding the "option" key at start. so far so good. The wireless keyboard works after a 2 sec initial delay. didnt try magic mouse, since i am comfortable with my MS mouse.

2. Audio: No sound initially. so I opened a command window and ran "alsamixer". a crude window opens up and you have to navigate using the arrow keys. unmute the "front" and other speakers using the "m" key. use up arrow to increase out put level to about 80%. and the sound is on!

3. Brightness: You need the latest Nvidia driver. Go to Custom driver settings where it prompted me to download the NVidia driver. I did that. re-boot. after that go to display/monitor setting again. choose to use the driver's settings. you should see "NVidia X server settings"
Choose X server color correction and then on the right adjust the brightness and contrast etc.
unfortunately the brightness buttons on the keyboard didnt work for me. neither did the various hacks found all over the net. this was the only way it worked. but none the less my eyes are saved now.

4. rEFIt: this program shows a cute menu at startup which allows you to choose your OS at boot. install this program via OSX. it start working for some reason after 2 re-boots.

5. iSight: camera worked without any trouble.

6. Mic: its a little weak i felt. In skype,  uncheck allow skype to decide my audio levels and set mic to max in the desktop audio settings.

[update]
7. Bluetooth magic mouse: this does not work because of the bluetooth issue. The solution offered is that you totally disable the Mac's Bluetooth handling and install a new bluetooth module. If you do this, you have to Map the keyboard again manually.
*I didnt do this. In any case, i am not comfortable with the flat mac mouse. I like my large USB MS mouse which fits my big palm. I love to click with my index finger swinging up and coming down hard smack on the left click :)

---

### Post by ZeroLinux on 2010-06-26
It isn't everething working
1) Mic. Muffled very mich. Need to be tweak up to 300%. Still mono
2) Bluetooth - doesn't work at all, bluez need to be patched
3) Consiquence from prev point Scroll in MagicMouse and "Fn" in the keyboard dont work
4) Reboot doesn't work  - line in /etc/default/grub need to be changed into GRUB_CMDLINE_LINUX_DEFAULT="quit splash reboot=pci"

That's all.

---

### Post by ashwindatye on 2010-06-29
damn right. I dont care much about the fn keys but bluetooth is a b***h. If you are a "man v/s wild" kind of guy with linux :-) then i suggest the following to fix blueT for you:
[http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/](http://idebian.wordpress.com/2008/07/06/manage-hid-bluetooth-devices-in-linux/)

I didnt try it. let me know if it worked for u.

---

### Post by ZeroLinux on 2010-08-01
[Here]("http://ubuntuforums.org/showthread.php?t=1541357") is the solution of this problem also

---

### Post by ashwindatye on 2010-10-30
Ubuntu 10.10: I back with a report this time using ubuntu 10.10. 
This time I formatted the entire 500GB harddrive. so there is no more OSX at the moment.
1. Display: Ubuntu promted me to download NVIDIA driver which i did and adjusted the brightness.
2. Sound: run "alsamixer" unmute front, increace volume to max
3. Bluetooth: good news, i could successfully setup both keyboard and magic mouse and my Nokia E71

The rest is same as above; no trouble.

Overall i felt much better with 10.10 than with 10.04. Ubuntu is moving up :-)

---

