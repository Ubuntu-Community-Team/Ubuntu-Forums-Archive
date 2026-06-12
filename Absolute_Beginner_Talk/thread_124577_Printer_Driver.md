---
title: "Printer Driver"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by advoss on 2006-02-01
So im trying to install the driver for the network printer (Brother HL-1440) and i downloaded the Debian package from Brother but i can't get it to install.

What happens is:

:~/Desktop$ sudo dpkg -i hl1440lpr-1.1.2-1.i386.deb
(Reading database ... 69295 files and directories currently installed.)
Preparing to replace hl1440lpr 1.1.2-1 (using hl1440lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl1440lpr ...
/var/lib/dpkg/info/hl1440lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1440lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr-1.1.2-1.i386.deb


The --force-all tag doesn't help

Idk what its trying to replace, would it work if i went through and created the directories it is looking for by hand, or what do I do?

It also wont let apt do anything now because it says:
```
E: The package hl1440lpr needs to be reinstalled, but I can't find an archive for it.
```

I have tried to remove the package a few ways and it won't let me.

```
dpkg - warning: ignoring request to remove hl1440pr which isn't installed.
```
AND
```
dpkg: error processing hl1440lpr (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 hl1440lpr

```


Please help!

---

### Post by Herman on 2006-02-01
Wow! 
Another way to do it, (I'm not sure whether you already tried or not), is just to click 'System', on your top panel, then go: 'Administration','Printing'.
A small window should open with a nice icon on it titled 'New Printer'.
You right-click on that icon, and it will give you a small rectangle with '+ add' on it.
Click on that to start the add printer wizard.
I already checked and your Brother HL-1440 printer driver is already there, just follow the prompts in the wizard. It should do everything for you a lot easier than the way you are trying. :-D (Herman)

---

### Post by advoss on 2006-02-01
Yeah i had done that, it actually used the HL-1240 (i think im on windows now) driver and since Brother had put out a driver for the 1440 i thought while i was trying to get my printer to work i may as well use the driver that was designed for the printer.

Anyways can i fix may package problem, becuase i seriously can't install anything short of manually copying and pasting the files, or did i break Linux and am going to have to reinstall it?

____
Seperate Idea and i was going to look around google more to try to figure it out yet but the printer is on the network through a routher that has a printer port on it.

In Windows:
I add new printer, create a local port of the type IP,  It gets called IP_192.168.0.101, and I put 192.168.0.101 as the address i press the radio button to set it to LPD and call the Queue LPT1.

On linux:
I selected UNIX (LPD)  Put 192.168.0.101 in the first blank, and LPT1 in the second and it told me it was connected but when ever i would try to print it would say the printer was stopped.  It would also blank the second field which i typed LPT1 in everytime i cloesed the properties on the printer

---

### Post by Herman on 2006-02-02
> Anyways can i fix may package problem, becuase i seriously can't install anything short of manually copying and pasting the files, or did i break Linux and am going to have to reinstall it?I haven't really had so much experience with installing printers, but is Ubuntu not working okay still?
Here's what I think: If Ubuntu is still working okay, just install the HL-1240 printer driver by the easy method suggested earlier and if the printer works satisfactorily, be happy with that. At least it's the right printer driver for Ubuntu. The other printer driver is for Debian, you said. It's the right driver for the printer if you are using Debain, but it obviously isn't the right one for Ubuntu.
If your Ubuntu system is not working properly anymore, (you mentioned you were typing from Windows), then I don't know. Re-installing takes maybe half an hour. How long will fixing take? For most people re-installing is easier and cleaner. But I still hope you won't need to re-install. Regards, (Herman).

---

### Post by lol on 2006-02-02
first install lpr (apt-get install lpr), and then try again to install your package.

---

### Post by galgoz on 2006-02-02
[QUOTE=lol]first install lpr (apt-get install lpr), and then try again to install your package.[/QUOTE]

What is lpr and what does it do?  Why would this help?  Not trying to be coy (did I spell that right) but I am not sure about installing things randomly so to speak.

---

### Post by lol on 2006-02-02
I should have explained a little bit more...

The installation of the hl1440lpr package fails because of the following error :
/var/lib/dpkg/info/hl1440lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory

Because the error occurs in the postrm script, I suppose it fails when trying to remove the previous installation. I would try 2 ways to solve this:

1 - the script is looking for /etc/init.d/lpd and doesn't find it. Why not install a package providing the file and see what happens? That's why I suggested to install lpr, which provides /etc/init.d/lpd. But it wouldn't be too surprising that lpr conflict with hl1440lpr, and in this case you may have troubles installing lpr (because you still cannot remove hl1440lpr...).

2 - the file could also have been provided by the hl1440lpr package in the first place (you can check this with 'dpkg-deb -c hl1440lpr-1.1.2-1.i386.deb'). If that's the case, then maybe the best solution would rather be to unpack the package manually. That should take care of this missing file issue. This time, you do it with 'dpkg-deb -x hl1440lpr-1.1.2-1.i386.deb'

hope this can help.

---

### Post by lol on 2006-02-02
> What is lpr and what does it do? Why would this help? Not trying to be coy (did I spell that right) but I am not sure about installing things randomly so to speak.

When not sure about what a package does, have a look at it's description in synaptic.

```
lpr - BSD lpr/lpd line printer spooling system
```

And by the way, I am not sure about what the hl1440lpr-1.1.2-1.i386.deb package is providing. But if it's not related to CUPS, you might as well forget about it. lpr and related tools are the old way to print in Linux. Although you probably can still use them, they are not as easy to setup and to use than CUPS.

Anyway, installing lpr is not going to put your pc on fire, and you can always remove it after cleaning the hl1440lpr mess.

---

### Post by galgoz on 2006-02-02
Thanks for the clarification.  Being a win user for the last 12+ years can make a person nervous :)

---

### Post by advoss on 2006-02-03
So i reinstalled Ubuntu.
Then I installed the lpr package
It uninstalled a couple packages which worried me a bit because i thought one of them was called gnome-desktop but gnome is still running so far anyways.
Then I entered the printer information as I had before and now it works.
I dont think I should take my chances by trying to install Brothers driver again.

Also anyone reading this if you think you could help with my other problem of getting my microphone to work, pleace visit the thread [here](http://ubuntuforums.org/showthread.php?t=124551)

---

### Post by SJ_Whitefang on 2006-02-04
I am brand new to Linux (from 10+ years on windoze machines)  so i am not totally familiar with how everything works.  Can someone please help me in installing a brother mfc 210c in ubuntu?  ive got a driver, im just not sure what to do next.

---

