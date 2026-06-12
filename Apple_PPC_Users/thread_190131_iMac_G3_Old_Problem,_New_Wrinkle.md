---
title: "iMac G3: Old Problem, New Wrinkle"
date: 2006-06-05
forum: Apple PPC Users
---

### Post by linear on 2006-06-05
The Dapper Live CD is unable to correctly detect the video on an iMac G3, so the fixes posted in the past for Breezy still apply.

There is one new problem. After dropping to a shell prompt, the command
sudo /etc/init.d/gdm restart gives the following response:

* Stopping GNOME Display Monitor                              [ ok ]
* Starting GNOME Display Monitor                                [ **fail** ]

**stop** followed by **start** has the same (lack of) effect as **restart**

The problem is that **stop** _doesn't_ stop gdm. **ps -A** before and after will show that that the process is still there.

This works:

**sudo killall gdm**

followed by:

**sudo /etc/init.d/gdm start**

Anyone else find the same problem?

---

### Post by Mike_N on 2006-06-05
I have a G3 iMac too and here's what i did...

While the live version has display issues, the installer does not. Catch, the standard Dapper disc uses a live installer. So, i installed Breezy and then typed this command to upgrade to Dapper...

gksudo "update-manager"

... However, i think that the "alternate" version of Dapper should offer a traditional installer, who needs to reconfigure... :)

---

### Post by ebeyer on 2006-06-06
[QUOTE=Mike_N]I have a G3 iMac too and here's what i did...

While the live version has display issues, the installer does not. Catch, the standard Dapper disc uses a live installer. So, i installed Breezy and then typed this command to upgrade to Dapper...

gksudo "update-manager"

... However, i think that the "alternate" version of Dapper should offer a traditional installer, who needs to reconfigure... :)[/QUOTE]


This is my first attempt at installing Linux, so please forgive me if my question is a little basic.

I am attempting to launch Ubuntu 5.10 live on an iMac G3/233.

I get as far as the Ubuntu logo.  The progress bar scrolls along, then the screen clears and there is a blinking prompt on the top left for a minute or so.  Then the display goes blank and stays that way - I let it go nearly 30 minutes, at which point the CD drive seemed quiet - still blank display, though.

Is this what you are talking about?  If not, have you run into this problem before?

Any help with this vexing problem is greatly appreciated.

---

### Post by linear on 2006-06-06
> I get as far as the Ubuntu logo. The progress bar scrolls along, then the screen clears and there is a blinking prompt on the top left for a minute or so. Then the display goes blank and stays that way - I let it go nearly 30 minutes, at which point the CD drive seemed quiet - still blank display, though.
 
Is this what you are talking about? If not, have you run into this problem before?
Yes, this is exactly the problem. The fix, after you get to that blank screen, is to drop to a shell prompt and edit xorg.conf.
 
If you don't know how to do this:
 
After booting is complete,
1. ctrl-option-F1 (should give you a command prompt, may take a couple of tries)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/gdm restart (return) to restart Gnome
 
At the very least you'll need to modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.
 
If you restart Gnome and everything is in extreme slo-mo, you'll also need to edit xorg.conf to disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

---

### Post by slink on 2006-06-12
> The progress bar scrolls along, then the screen clears and there is a blinking prompt on the top left for a minute or so. Then the display goes blank and stays that way


I have the same issue than eyeber but with a black screen at the end of the process. 

I tried what linear said:

1.ctrl+alt+F1
2.modify "HorizSync" to 60-60 and "VertRefresh" to 75-117 on /etc/X11/xorg.conf

That led me to gdm's desktop, but it was still misconfigured (it filled only about  66% of the screen) and there was no mouse response, so I tried other values such as VertRefresh 75-75. But those tries only made me watch scary unsettled desktop screens. 

Maybe some right values would do the job but I just can't guess what to change on xorg.conf.

---

### Post by linear on 2006-06-12
You have an iMac G3, right? Did you disable dri? (if not, do it.)

---

### Post by Sav on 2006-06-13
[QUOTE=linear]You have an iMac G3, right? Did you disable dri? (if not, do it.)[/QUOTE]

Sadly that's true.
There is no way to get hardware acceleration, even setting the default depth to 16 bit.
I don't know why, but at 16 bit X loads extremely slow.

By the way, I resolved al my X probolems doing "sudo dpkg-reconfigure xserver-xorg"
At the end, I changed the video frequencies as you know:
"HorizSync" to 60-60 and "VertRefresh" to 75-117

---

### Post by nkbj on 2006-06-13
[QUOTE=slink]
2.modify "HorizSync" to 60-60 and "VertRefresh" to 75-117 on /etc/X11/xorg.conf

That led me to gdm's desktop, but it was still misconfigured (it filled only about  66% of the screen) and there was no mouse response, so I tried other values such as VertRefresh 75-75. But those tries only made me watch scary unsettled desktop screens.[/QUOTE]

Try setting HorizSync to 60-60 and VertRefresh to 43-117 in /etc/X11/xorg.conf as shown in [http://pingswept.org/xorgconf-for-xubuntu-on-g3-imac/](http://pingswept.org/xorgconf-for-xubuntu-on-g3-imac/).

---

### Post by emgee on 2006-06-17
I had the same problems as all of you.
This is what I did:

1) Inserted CD while in OSX. Rebooted
2) Typed "live-powerpc" at boot-image-menu. Hit enter
3) Waited for the nice, welcoming Ubuntu start sound, indicating that the live interface was running.
4) hit alt + ctrl + F1 to get a console up (Did not have to try multiple times)
5) Then I did the following:
```


sudo nano /etc/X11/xorg.conf

<change>
HorizSync       60-60
VertRefresh     43-117
</change>
```

The <change>section</change> are values I made sure replaced existing ones in /etc/X11/xorg.conf, just like everyone else suggests.

After that I tried:
```


sudo /etc/init.d/gdm restart
```
Note that it did NOT work for me! It simply didn't have any effect what so ever.

Instead, I did:

```


sudo killall gdm
sudo /etc/init.d/gdm start
```

I am now in the process of choosing keyboard layouts in the live installation interface of Ubuntu 6.06.

Mike

---

### Post by fraterf93 on 2006-06-22
This is the same peroblem I've been harping about for over six months.  since Breezy.  It's been documented many times over by myself, and others.  Please refer to my previous posts.  The same xorg problem.  It's really funny that I'm trying to use Xubuntu, touted as being the perfect distro for older hardware.  Apparently not older Mac hardware with an ATI Rage 128 Pro 16mb graphics card.  In any event My iMac G3 Triple boots(Mac OS X, Mac OS 9, Kubuntu 5.10).  My Mac mini runs Xubuntu Dapper Drake just fine though! :)   But I really want Xubuntu on my iMac G3!

---

### Post by Sav on 2006-06-23
[QUOTE=fraterf93]This is the same peroblem I've been harping about for over six months.  since Breezy.  It's been documented many times over by myself, and others.  Please refer to my previous posts.  The same xorg problem.  It's really funny that I'm trying to use Xubuntu, touted as being the perfect distro for older hardware.  Apparently not older Mac hardware with an ATI Rage 128 Pro 16mb graphics card.  In any event My iMac G3 Triple boots(Mac OS X, Mac OS 9, Kubuntu 5.10).  My Mac mini runs Xubuntu Dapper Drake just fine though! :)   But I really want Xubuntu on my iMac G3![/QUOTE]

Did you modified the xorg.conf file, adding the proper refresh frequencies?

---

### Post by fraterf93 on 2006-06-23
Well, I looked at the refresh frequencies, and compared them to the frequencies in my Mac OS X 10.4.6 Preferences pane, and they are correct.  That was the first thing I thought of after I  checked /etc/modules, and /etc/X11/xorg.conf to see if the changes I made in Breezy were still there(they were).  As far as I can tell the /etc/modules file, and the /etc/X11/xorg.config file appear to be the same after I upgrade to Dapper.  And yet I still have the same symptoms I had in Breezy before editing those files.  I'm not experienced with Linux at all, and basically am following instructions I get from others in this forum, however I'm sure this has something to do with the ATI Rage 128 Pro video card, and the xorg.conf file.

As another side note, I have learned how to make use of lynx because of this "freeze" issue and the GUI being unusable!  I can surf the net, and check the forums in text!  lol :D!yay frater!:D

---

### Post by slink on 2006-07-04
> You have an iMac G3, right? Did you disable dri? (if not, do it.)

Disabling dri has worked well. I've managed to start Ubuntu either with VertRefresh to 75-117 or 43-117. 

I misunderstood that disabling dri was only necessary if Gnome succeeded to start but it was running slow.


> If you restart Gnome and everything is in extreme slo-mo, you'll also need to edit xorg.conf to disable DRI


Thanks a lot for help !

---

### Post by fraterf93 on 2006-07-12
Yep it was the dri.  I didn't have to comment it out in Breezy though, so I still don't really understand the problem.  But at least I'm running Xubuntu on my old iMac!  Tripple boot yo!:mrgreen:

---

### Post by darion on 2006-07-14
I will admit that I know nothing about linux and would like to learn. Hence why I am trying to load this on my G3. Everything loads and I hear the sound at the end and have the black screen. I bring up the prompt just I can't get the anything I type in to work right. Don't know if I'm typing everything wrong or not. Please help on how to type it in.  :confused:

---

### Post by RHTopics on 2006-07-15
darion,

Are you trying to use Ubuntu running from the Live CD?  Or have you installed Ubuntu?

---

### Post by darion on 2006-07-15
Right now all I have is the live cd but I would like to get it installed. Was able to get server version to install, just don't know anything with the commands or how to use it so I removed it.

---

### Post by RHTopics on 2006-07-15
Have you looked at this thread?

[http://www.ubuntuforums.org/showthread.php?t=75604](http://www.ubuntuforums.org/showthread.php?t=75604)

It addresses how to fix the blank screen problem with the Live CD.

What are the specifications for your iMac?  That is, model, memory size, hard drive, etc..

---

### Post by darion on 2006-07-15
It is an iMac G3 400mhz, 10 gig HD, either 250 or 500MB for the mem. don't quite remeber thinking it's the 500. Right now I don't have any OS loaded but would like to get this loaded  so that I don't have to try using the cd every time. It seems to try excepting the changes but since it is on cd it don't work. How can I get this loaded to the system so that I do not need the cd and so it will hold the change?

---

### Post by RHTopics on 2006-07-15
Just to make sure, were you able to get past the blank screen problem by editing the /etc/X11/xorg.conf file and then restarted X server to bring up the graphical user interface?

Also, if you are trying to install Ubuntu with the Live CD, then you need at least 256MB of memory.

To check your memory, enter the following at the command line:
```
free
```

Press the keys "control", "alt", "F1" to get to the command line if you are not there already.

You should get something like displayed back to you:

```
              total       used       free     shared    buffers     cached
Mem:        385236     350360      34876          0      19452     194240
-/+ buffers/cache:     136668     248568
Swap:       309796          0     309796

```

Let me know the number under "total".

---

### Post by darion on 2006-07-15
Total is showing 514872 so I should have enough, I just need to figure out how to do the install

---

### Post by RHTopics on 2006-07-16
You are right.  You have plenty of memory to do an install from the Live CD.

Still, not certain from your reply that you are now able to bring up the graphical user interface after changing /etc/X11/xorg.conf.

But if you are, then you should be able to double-click the "Install" icon on the desktop to start the install process.

What happens after double-clicking the "Install" icon.  Provide as much information as you can so I or someone else can help you debug your problem.

Another approach, would be to download the "alternate" CD and see if you have better luck with it.  I have not used it, so someone else will have to help you with it.

---

