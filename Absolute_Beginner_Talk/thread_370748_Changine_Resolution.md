---
title: "Changine Resolution"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by osofast on 2007-02-26
Hey guys

I just started Using ubuntu, and I am very impressed. this is my first linux install ever (well i did try linspire, didnt like it too much)

I am having some problems though mainly with chanign the resolution on my averatec 1020 laptop.

Whenever I go to the chaning resolution screen the max I can go is 1078, I want to go to 1268x800 or something close to that at least

I have a Intel gfx card in my laptop, however Im not sure of the exact model number. I dont know if maybe I need new drivers, but i hear its quite difficult to install new drivers.

Any help would be appreciated.

PS, does anyone know how to make it such that my trackpad is disabled when im typing.

---

### Post by Kateikyoushi on 2007-02-26
Copy the following line to terminal that wil lreconfigure X.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by osofast on 2007-02-27
Hey, thanks for the help, but i think I may have ruined my install or something
I copied that command into terminal and a bunch screens came up, i didnt know what to write for them so i started messing around, and then i restarted my computer, now it will get to the log in screen but it wont let me login, like ill type my password then it will go to a black screen and then it will go back to the login page.

Does anyone know how to get fix this? or how to format unbuntu without deleting everything on the HD

PS. I have a dual boot going on so im writing this from windows.

thanks

---

### Post by Kateikyoushi on 2007-02-27
There is a recovery mode option at boot choose that it will log you in to terminal and try to set up X correctly if necessary search for your hardware details on the web or post them here maybe we can help with the settings.

---

### Post by Mozork on 2007-02-27
Ok, you do the following:
You messed up the xserver configuration, but there should have also been a backup file created, so you can just run ubuntu in recovery mode and replace the xserver config file with the backup.

So you start under recovery mode, and go to the xserver directory by typing:
```
cd /etc/X11
```Then you look at the files there by typing
```
ls -l
```You should now see a list of files. There should be a xorg.conf file, and also a xorg.conf.'weird number' file, this is your backup.
Now you just have to replace the normal file with the backup and everything should be exactly as before.
To replace the file you type:
```
mv xorg.conf.'weird number' xorg.conf -b
```

€dit:
Or you can do what Kateikyoushi suggests.

---

### Post by osofast on 2007-02-27
Wow, that was extremely quick and quite detailed. This ubuntu experience is becoming better and better. Thanks guy, Ill have to give that a try as soon as I finish writing this report.

I really don't know how to thanks you guys enough.

---

### Post by osofast on 2007-02-27
Wow that worked like a charm, I am back into Ubuntu, now i just need to figure out how to change the resolution.

Heres some details i have found on another forum about some guy how has the same problem as me. Maybe someone can help me decipher this.

"Generally, you need to use 915resolution with Intel chipsets unless the resolution you want is in the VESA BIOS. If you don't already have 915resolution, you can install it -- it has been packaged by Ubuntu.

Theory: the intel X server can only use resolutions in the VESA BIOS (this limitation is going to go away, probably in the next year). The VESA BIOS supplied by Averatec does not include the 1280x768 resolution. 915resolution is a hack that patches the copy of the VESA BIOS that is in RAM to replace some unused setting with one you'd like to have. 915resolution is to be run before X starts so that X will see the new resolution.

How 915resolution is run in 6.06 probably differs from how it is run in 6.10. The architecture of startup and runlevels changed drastically."

---

### Post by OldTimeTech on 2007-02-27
So, that says go to synaptic, find the 915 intel and install it, if it screws the resolution up more uninstall it.....can't say if it will work or not, I'm not using an intel chipset.

---

### Post by osofast on 2007-02-27
Hey, Old timetech, I tried that, i went to the synaptic thing put the 915resolution, and installed it, restarted, however it still didnt change my reosultion to the naitive one.

---

### Post by osofast on 2007-02-27
Hey guys,

Im trying to follow the instructions on this webpage

[http://absolutebeginner.wordpress.com/2006/08/20/absolute-beginner-guide-915resolution/](http://absolutebeginner.wordpress.com/2006/08/20/absolute-beginner-guide-915resolution/)

However when i put in the first command it is suppoused to show me a list of all the resoultions instead i get this:

Intel 800/900 Series VBIOS Hack : version 0.5.2

Unable to obtain the proper IO permissions: Operation not permited

I think if I follow the instuctions on that page it will work. I just need to get past the first step

---

### Post by osofast on 2007-02-28
I figured out how to get past the first step, and I went through them all, however still no luck.

Iv attached an image of the device I have as it is listed in the device manager, maybe this will help.

---

### Post by osofast on 2007-02-28
I figured it out, you have to configure your xorg, and then you have to press space bar at the resolution you want!!1

thanks everyone

---

