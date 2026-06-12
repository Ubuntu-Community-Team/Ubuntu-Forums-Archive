---
title: "Copying data between Nokia and Ubuntu..."
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by Stickymaddness on 2007-04-14
I'm having issues connecting my Nokia 6630 to my pc...

The most important thing for me is the ability to backup received messages and to copy data to and from my phone, photo's, vid clips, mp3's etc... I'm using a data cable and don't care about using bluetooth or using my phone to go online.... 

I've tried all the apps I could find, but still haven't had any luck.

KMobileTools detects my phone fine, it can see my battery & signal level fine and I can use it to dial numbers. But it cannot retrieve messages, and of course I can't use it to copy data.

xgnokki starts up and says "connecting" till it crashes.

Wammu detects my phone fine and calls up all the info (Model, Serial num, etc) but cannot do anything else, it randomly crashes with

```
Error while communicating with phone

Description: Unknown error.
Function: GetNextMemory
Error code: 27

```

:confused: As always, any help would be greatly appreciated!

---

### Post by hoheszeh on 2007-04-15
First of all i am having issues with my Nokia 6233 as well. I didnt try all these apps. I connected my phone with the PC via USB. Then i switched the phone to "usb-mode" and ubuntu finds and mounts it.

Everything is still fine. Trying to copy files from the phone to the harddisk make nautilus crash. Even the Terminal freezes when i try it there.

trying a 

```
dmesg
```

after the crash/freeze of nautilus/terminal gave me lots of I/O errors. Funnily enough i CAN create directories on the phone and remove them again without problems.

Maybe there is a similar issue with your phone?

---

### Post by Stickymaddness on 2007-04-15
Possibly...

Where does Ubuntu mount your phone to though? I cannot even see the folders/anything on my phone...

---

### Post by Stickymaddness on 2007-05-02
After much fiddling I have managed to get things half working. I followed the guide at [http://wiki.splitbrain.org/nokia_6630]("http://wiki.splitbrain.org/nokia_6630") Using the packages from [Hendriks]("http://www.stud.uni-karlsruhe.de/~ubq7/debian/").

Everything seemed to install fine, but I cannot get obextool working. I have tried editing 
```

/etc/obextool/obextool.cfg 

```
and setting it to one of the following:

```

set ObexConfig(obexftp,command) "$OBEXCFG/obexwrap.sh"

or

set ObexConfig(obexftp,command) "obexftp -u 1"

or

set ObexConfig(obexftp,command) "obexftp -t /dev/ttyACM0

```

But in all the cases it says

```

Using obexftp command: /usr/bin/obexftp -t /dev/ttyS0

```

When obextool does run, it either freezes, or loads but / is empty.

I've noticed that I can

```

sudo obexfs -u 1 /mnt/6630
sudo -H nautilus /mnt/6630/

```

Which allows me to view all the files on the phone, but I cannot copy anything to or from the phone.

So close, but so far! Can anyone point me in the right direction?

---

### Post by Stickymaddness on 2007-05-03
Well I re-installed everything, and it works!! :D Using
```

obexftp -u 1

```

I can get obextool working! Now just to conquer exporting sms's and contacts....

---

### Post by msayed2004 on 2008-04-26
Sorry for bump-ing this topic.> **Stickymaddness said:**
> Well I re-installed everything, and it works!! :D Using
```

obexftp -u 1

```I can get obextool working! Now just to conquer exporting sms's and contacts....
Can the *ObexTool* do [COLOR=Red]Backup/Restore[/COLOR] tasks for _contacts, SMS & calendar_ ?

---

