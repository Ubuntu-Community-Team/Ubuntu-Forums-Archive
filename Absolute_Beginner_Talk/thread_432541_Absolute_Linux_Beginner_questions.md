---
title: "Absolute Linux Beginner questions"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by alamandrax on 2007-05-04
I've just installed Ubuntu 7.04 Feisty on an old desktop at home and would appreciate any help with the following

Issue 1:
I seem to have an AGP SiS 305 video graphics card. I'm not sure if the drivers have been installed properly. Upshot is, I cannot enable Desktop Effects or increase the resolution above 1024x768.

Issue 2:
I have a Sound Blaster Live! sound card and it looks like the drivers were installed fine (the audio worked the first time I booted up in Ubuntu (at the login screen)). There is no audio output right now. I tried playing the example files from the home folder and no sound can be heard from the speakers. I did try this with some earphones but no such luck.

Issue 3:
I did a dumb thing. I accidentally removed the Network Manager applet from my Notification Area panel. I can't seem to find it again. How do I find it? The Network Monitor from the "Add New Panel" dialog isn't the same one.

Please help.

---

### Post by Kobalt on 2007-05-04
1. Check in you xorg.conf file if this resolution you want available is present first (in the last parts of the file) : ```
cat /etc/X11/xorg.conf
```
If it's not, type in a Terminal ```
sudo dpkg-reconfigure xserver-xorg
```
Select the resolutions you want as available by hitting the spacebar and then validate with Enter. Restart your X with Ctrl+Alt+Backspace and it should be ok.

2. Have you checked the volume control center if anything was muted ?

3. If you don't even see your applet comming back after a reboot then you need to add it back in System > Pref. > Session : programs at startup. Simply add *nm-applet --sm-disable* for the command line and name it Network-Manager...

---

### Post by igknighted on 2007-05-04
> **alamandrax said:**
> I've just installed Ubuntu 7.04 Feisty on an old desktop at home and would appreciate any help with the following

Issue 1:
I seem to have an AGP SiS 305 video graphics card. I'm not sure if the drivers have been installed properly. Upshot is, I cannot enable Desktop Effects or increase the resolution above 1024x768.

Issue 2:
I have a Sound Blaster Live! sound card and it looks like the drivers were installed fine (the audio worked the first time I booted up in Ubuntu (at the login screen)). There is no audio output right now. I tried playing the example files from the home folder and no sound can be heard from the speakers. I did try this with some earphones but no such luck.

Issue 3:
I did a dumb thing. I accidentally removed the Network Manager applet from my Notification Area panel. I can't seem to find it again. How do I find it? The Network Monitor from the "Add New Panel" dialog isn't the same one.

Please help.

1) Open a terminal and run "sudo dpg-reconfigure -phigh xserver-xorg" and add the extra resolutions you want in the dialog it opens.  I'm not sure what 3d capabilities the SiS cards have in linux on the other front.

2) Try running the command "alsamixer" and making sure none of the important channels are muted.  Also, try plugging your sound into your mobo's sound jack instead of the sound card.  If that works, you should turn off the mobo sound in your bios.

3) Oh dear, I know nothing of network manager... I think you can run it from the terminal (network-manager or nm-applet are the commands... i think).  If this doesn't work someone else will have to answer this part.

---

### Post by alamandrax on 2007-05-04
Thanks a lot. I'll get working on these. Am also trying to run a Linksys wireless router from the Linux box, but I think that's for a different thread.

---

### Post by alamandrax on 2007-05-04
ok. Now:

1. I ran the configuration and now am running at 1280x1024. Brilliant :D.
But I still can not enable desktop effects. System>Prefs>Desktop Effects>Enable  gives me an error "Desktop Effects could not be enabled". Is it the graphics card?

2. I ran alsamixer and checked all the volume controls. They seem to be set at comfortable levels (all above 50%). I did plug-in my earphones (which work) into the mobo audio jack instead of the Sound Blaster audio jack. Jack. No sound. I tried all the ports available. Nothing. I tried different files. Nothing there either.

3. The Network Manager applet ***is*** installed in the startup programs in the sessions manager. Multiple reboots seem to have no effect on the notification panel though. It refuses to show up. However, interestingly it shows up in the other users' notification areas. Just not in the one I deleted it from. Weird stuff.

So, to sum up, no grafix. no sound. and could do without the notification area icon (or simply delete this username and make a new one - should fix that) but I'd like to know how it works.

---

### Post by cpdave on 2007-05-04
I had a similar problem with the network manager icon. I fixed it by: right click on the top panel "Add to Panel...", then under "Utilities" add "Notification Area".

CPDave.

---

### Post by alamandrax on 2007-05-04
d'oh!

I did delete the Notification Area Panel didn't I? Thanks a lot!

Any problems with your sound too? ](*,)

---

### Post by alamandrax on 2007-05-04
bump!

---

### Post by Pisi-Deff on 2007-05-04
> **alamandrax said:**
> ok. Now:

1. I ran the configuration and now am running at 1280x1024. Brilliant :D.
But I still can not enable desktop effects. System>Prefs>Desktop Effects>Enable  gives me an error "Desktop Effects could not be enabled". Is it the graphics card?

The default drivers in ubuntu don't support 3D accleration. You'd need properiaty(or whatever the spelling is) drivers for it to work.

---

