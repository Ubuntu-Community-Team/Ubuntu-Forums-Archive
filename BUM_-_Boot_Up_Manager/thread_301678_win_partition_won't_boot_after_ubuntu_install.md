---
title: "win partition won't boot after ubuntu install"
date: 2006-11-17
forum: BUM - Boot Up Manager
---

### Post by rusyear04 on 2006-11-17
hi there people!
i hope that you can help me...

here my problem:

i've installed edgy on my laptop as second OS. now edgy runs fine, but the original OS (winXP) does not start any more.
after selecting win in the boot-manager i'm getting following ERROR-message:

>Error 29: Disk write error
>Press any key to continue

after key i get back to the boot-menu.

i'm pretty sure, that the problem is somehow related to a previously installed "QuickPlay"-OS which should have been an operating system that allows to view DVD and listen to music without booting the notebook (never got it to work).

another thing that irritates me is, that the partitions are not numbered by their order on the HDD.

the WIN partition looks undamaged and is located at /dev/hda1

if you know anything that might help me, i'd be glad to hear it :D
thanx

---

### Post by ajgreeny on 2006-11-17
What is the content of your /boot/grub/menu.lst file?  There should be an entry at the bottom with:-

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1

If it is missing add it yourself as root (gksudo gedit /boot/grub/menu.lst) and see if that helps.

---

### Post by rusyear04 on 2006-11-17
i do have that exact same entry...

i tried to change it to
root (hd0,0)
root (hd0,1)
root (hd1,0)
root (hd1,1)

with no effect. it seems to me, that this damned win-partition is somehwere else. but as i said: it is definitely (?) on the firs partition of my HDD.

(ps: i'm quite new to lin ;))

---

### Post by ajgreeny on 2006-11-17
Sorry but I'm foxed.  If windows is really on hda1, your grub menu should work OK.
Perhaps you need to repair your MBR with the windows install CD; that will at least find windows for you again and tell you if it's really on hda1, and then go from there. Anyone else got any ideas.

---

### Post by rusyear04 on 2006-11-17
well, thats the next thing i'll try :) thanx.

just need to wait until i get my win-disc back. i hope that this will solve the issue, because unfortunatelly i still need that win-crap... :-|

---

### Post by rusyear04 on 2006-11-19
so... i inserted the XP disc, started and that retard started installing winXP a *second* time...
i was able to break the process and now i do have a WIN-boot-manager that gives me 2 winXP boot-options:
1) continue install
2) old winXP (working)

...now i just need to know: how do i acces my ubuntu-partition and how do i get rid of the XP-install "part" (i don't even have a clue where to the files of/for the install have been copied!!)

---

### Post by rusyear04 on 2006-11-19
i don't know if this helps:
this is the content of the boot.ini (of the working windows)

```

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional" /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
```

so, if anyone could tell me:
1) how to "delete" the (pre)install-files of the second XP
and
2) how to get my (ubuntu) boot-manager to work properly WITH the working windows as an option...

i would be really glad and thankful :KS 
:rolleyes:

---

### Post by rusyear04 on 2006-11-21
fixed it :D !!

there is also a program for "professionally messing" with your MBR: [super grub disc]("http://adrian15.raulete.net/grub/tiki-index.php"). unfortunatelly it didn't work for me in sense of installing a working MBR, but it did help to access both OS -which i couldn't otherwise!

**anyhow...**
...i'm not quite sure if it was/is the most elegant way to do it, but this is how i succeeded:

1)
i started installing winXP a second time and broke off the install-process (still don't know where the install-files are and how to remove them). after this i only had the win-boot-loader (with my working win and the installation-process).

2)
next i used the edgy-eft install disc to get into the knoppix.
there i went into the terminal:

> 
a) Type "grub" which makes a GRUB prompt appear.

b) Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

c) Type "root (hd0,3)".


d) then "setup (hd0)" to write GRUB into the MBR (master boot record).
[another instructions used "setup (hd0,3)" this writes it to your linux root partition.]

e) type "quit".

f) restart.

now basically you're done. you do have a fresh GRUB which might be working.

in my case i still did have to change the entries of the GRUB a bit (you can do this immediatelly at boot up (directly in GRUB). but this is only temporary (good for experimenting :)).

i did have to change the WIN entry to

```
root  **(hd0,0)**
```

and the ubuntu-entry
```

title  Ubuntu, kernel 2.6.17-10-*whatever*
root   **(hd0,1)**
kernel /boot/vmlinuz-2.6.17-10-*whatever* root=**correct_hdd_name** ro quiet splash
initrd /boot/initrd.img-2.6.17-10-*whatever*
savedefault
boot
```
to the appropriate disc...

the only thing that is not "clean" is, that i do get the win-boot-loader after choosing win (in GRUB). in win-boot-loader i then have to choose between the working win and the install-process *(i hope to get rid of the install thingie somehow)*.
**if you know HOW, please tell me :)**

well... i have no clue if you understood this (it's my first "how-to"...i'm quite a newbie)
if something is unclear, feel free to ask (write a message).

---

### Post by adrian15 on 2006-11-23
> **rusyear04 said:**
> fixed it :D !!

there is also a program for "professionally messing" with your MBR: [super grub disc]("http://adrian15.raulete.net/grub/tiki-index.php"). unfortunatelly it didn't work for me in sense of installing a working MBR, but it did help to access both OS -which i couldn't otherwise!

Which options did you use? Did you see "SGD has succeed" but it did not?

About the error 29... I supose that putting: rootnoverify instead of root or just removing the savedefault line will have solved the error.

adrian15

---

### Post by Rhubarb on 2006-11-23
The win boot loader thing can quite easily be fixed up ... it's just finding where it's hidden in windows that can be quite annoying.

As I'm infront of my work pc here (win2k not xp), and don't have access to that option, and don't run windows at home, I'm going off memory here:

Right click on "my computer" or in the control panel double click on "system".
In one of those tabs there you'll find something that allows you to change the boot order "Startup and recovery" is what it's called in win2k - it's probably called something else in xp.
There you should be able to find a button or something there that allows you to edit the boot list.
From there you simply can delete the "continue install", and make the "old winXP (working)" the default.  Save and quit and reboot.
Then in grub select windows, then windows should just boot up like it should.

---

### Post by mrfelker on 2006-12-02
You need to open a terminal and go to directory /boot/grub.  First sudo cp menu.lst menu.lst.bak (or use a root login if you have one and are a "bad boy".  Then sudo gedit menu.lst.

If is is  not commented out already remove the # in front of the statement #hiddenmenu.

Then (again if this isn't this file already, add these statements after the last menu item

 title         Windows XP
 root          (hd0,0)
 makeactive
 chainloader   +1


When you next boot the system you should see a menu choice Windows XP and scroll to that entry and press enter.  You should boot your XP.

---

### Post by adrian15 on 2006-12-04
> **mrfelker said:**
>  Then (again if this isn't this file already, add these statements after the last menu item

 title         Windows XP
 root          (hd0,0)
 makeactive
 chainloader   +1

The correct piece of code is:
```

 title         Windows XP
 rootnoverify  (hd0,0)
 makeactive
 chainloader   +1
 boot

```

The root statement have problems with ntfs partitions.


adrian15

---

### Post by rusyear04 on 2006-12-07
thanks for the help... in the meantime i did manage to solve the problems on my own -after letting them rest for (quite!) a while :)

...the half-installed win-thing was located on C: drive along to the fully installed win. it was simply called *windows.0*. i don't know anymore if it was maybe hidden.
anyhow, there was also an entry *documents and settings.0* (mine is set german so i don't know the exac english name). and that was deleted as well.

afterwards i only changed the WIN-boot entry and since then it's running fine :)

thanx again to all of you who helped though the forum!!!
:D

---

### Post by Towapken on 2007-01-02
noi, but for those who want to do the same as you did, it is better to use the win-cd to boot to the recovery module:

then you will get something that looks like an old dos prompt. (or for linux adepts: a very basic terminal ;-) ) Then use the command FIXMBR this should rewrite the windows bootloader to your masterboot record.

Still no luck, then maybe boot.ini has been damaged, this can be repared by typing FIXBOOT. Both tricks have proved their value to me more then once.

---

