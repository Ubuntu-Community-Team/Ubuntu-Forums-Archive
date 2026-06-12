---
title: "MacBook (mid-2007) iSight not working"
date: 2010-01-25
forum: Apple Hardware Users
---

### Post by Tycho59 on 2010-01-25
I can't seem to get my built-in isight camera to work with ubuntu.  I'm currently running Ubuntu 9.10.  What can I do step for step to get ubuntu to actually enable isight??  Any help is appreciated.

---

### Post by linuxopjemac on 2010-01-25
[https://help.ubuntu.com/community/MacBook2-1/Karmic#iSight](https://help.ubuntu.com/community/MacBook2-1/Karmic#iSight)

---

### Post by Tycho59 on 2010-01-25
Thanks, I tried that, but somehow I messed up the process and it won't install. error message states:

error processing isight-firmware-tools (--config):
  subprocess installed post-installation script returned error exit status 134 
Errors were encountered while processing:
isight-firmware-tools

E: sub-process /usr/bin/dpkg returned an error code (1),


what do i do from here.  Much thanks in advance.

---

### Post by linuxopjemac on 2010-01-25
> Then install the firmware extractor and let it do the work for you:

```
sudo apt-get install isight-firmware-tools
```

Check that the path begins with /media/MacOSX/System... and then click OK.

If the path is incorrect, you will not be prompted for another location. You must purge the installation before trying again. 

I would remove the package isight-firmware-tools

```
sudo apt-get --purge remove isight-firmware-tools
```

---

### Post by Tycho59 on 2010-01-25
After clearing everything out that I've already tried to uninstall then reinstall the isight firmware and then going back and installing it following the instructions listed in the link above, and I still get the same error message.

---

### Post by Tycho59 on 2010-01-25
I really don't get what's happening.  I keep going through the all the commands that will let me install the isight firmware and the commands that'll let me go back and start over, but it's not working.  Does anyone have any suggestions as to another method other than whats suggested in the help section??

---

### Post by linuxopjemac on 2010-01-25
did you read this:

> NOTE: The following firmware extraction currently works with the AppleUSBVideoSupport file from OSX 10.4 (Tiger) and 10.5 (Leopard). It will fail with OSX 10.6 (Snow Leopard).

What does the following give you?
```

sudo ls /lib/firmware | grep isight
```

it should give you the firmware of your isight, if all is right.

---

### Post by Tycho59 on 2010-01-26
I did see that, thing is I'm running 10.5.

When i run that code nothing happens.  When I try using the code provided by the link above I keep getting the same error message.  It is quite frustrating.

---

### Post by linuxopjemac on 2010-01-26
If I have time, I can give you my fw file, if that works...

---

### Post by Tycho59 on 2010-01-26
sure, that'll be great.

---

### Post by Tycho59 on 2010-01-26
Thanks linuxopjemac, putting the isight.fw file you sent me into the firmware folder worked like a charm.

---

### Post by linuxopjemac on 2010-01-26
Great.

---

### Post by new-num-order on 2011-01-29
I'm having the same problem. I have MacBookPro 2,1 (late 2006) and have Karmic installed. iSight worked fine right after install, but after installing some other packages it doesn't work anymore. I tried purging and installing again and it still doesn't work. I've got the AppleUSBVideoSupport file from [here]("http://www.mediafire.com/?81xtkqyttjt").

I hope you can upload somewhere the **isight.fw** file for me and others as well.

Thanks in advance!

---

### Post by new-num-order on 2011-01-29
I've solved it. I've been searching for isight.fw file on Internet and I've come across [HOWTO: Fix iSight in Hardy]("http://ubuntuforums.org/showthread.php?t=764616"). I've just typed in this command:
```
$ sudo modprobe -r uvcvideo
```
Mouse stopped working properly and everything froze a few seconds later. After hard shutdown and boot Cheese is working fine again.
As I understand it the command above is supposed to just test the camera. I don't know why it actually fixed it. I've tried rebooting before, it really must've been this command that did it.

---

