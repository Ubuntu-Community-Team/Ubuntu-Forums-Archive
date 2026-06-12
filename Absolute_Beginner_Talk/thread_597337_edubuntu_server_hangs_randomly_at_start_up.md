---
title: "edubuntu server hangs randomly at start up"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by gnw23 on 2007-10-30
I have an edubuntu server 7.10 with P4 2.6 GHZ with 2 GB ram and 160 GB SATA HDD

edubuntu server 7.10 works fine 

but some time while starting after it passess the grub loading menu

it says 

"starting up"

and it hangs there itself 

then i had to restart to get it working  times 

what could be the problem other wise once it starts it works without any problem

i am using edubuntu server 7.10 bcoz it has got ltsp in built 

is edubuntu 6.06 has got the same inbuild ltsp support so that i can use the same 

bcoz i had a great experiance with ubuntu 6.06 its very stable and never gave me any problems



thanx and regards 

Plz help me with this 

Shashikant

---

### Post by SpiritIsReality on 2007-11-10
howdy
you could try choosing recovery mode at the grub menu, or
zless /usr/share/doc/upstart/README.Debian.gz 
> 
How can I see boot messages on the console?
-------------------------------------------
This is nothing to do with upstart, but I'll answer this anyway.
Remove "quiet" from the kernel command-line.

To make this permanent, edit /boot/grub/menu.lst and edit the line
that begins "# defoptions=" (yes, it looks like a comment).

This will change both usplash and the LSB init logging.

I removed quiet and splash.
If it hangs at the fsck check, [http://ubuntuforums.org/showthread.php?t=607183](http://ubuntuforums.org/showthread.php?t=607183)
I looked in /var/log and there is a boot file but it is empty. Has to be turned on somehow?
zless /usr/share/doc/upstart/README.Debian.gz 
> 
Where are the boot messages logged?
-----------------------------------
Messages output by the rc scripts can be found in /var/log/boot, if
you have the upstart-logd package installed.

There is also a /var/log/messages that might help.
[http://www.google.ca/search?hl=en&q=linux+%2Fvar%2Flog&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=linux+%2Fvar%2Flog&btnG=Search&meta=)
[http://www.ibm.com/developerworks/linux/library/l-roadmap5/](http://www.ibm.com/developerworks/linux/library/l-roadmap5/)
trails

---

