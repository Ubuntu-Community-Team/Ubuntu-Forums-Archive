---
title: "user switching"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Chris2169 on 2008-01-20
Hi again, 

I may be being really dense but frustration is starting to set in !  I have fouled my new install of ubuntu so it won't boot.  I understand from other posts how and why and potentially how to fix it, however....

I can use a live cd, that boots fine and I can 'see' the damaged file.  When I try and fix it I'm not allowed to save the changes.  I assume this is because I'm logged in as 'live session user' instead of 'me'.  So my question is from where I am now how do I log in as myself or gain sufficient privileges to fix the damaged file.  Or will it be easier just to reinstall the whole thing ?

Thanks

---

### Post by forestpixie on 2008-01-20
you should be able to do it as root/sudo

perhaps if you gave a bit more information you might get some help, what is it you need to achieve in the livecd?

---

### Post by Chris2169 on 2008-01-20
apologies, lest haste more speed.....

Some more info.

I need to edit the boot/grub/menu.lst of the original installation.  As this installation now hangs when trying to boot.  So I've booted the machine up with the live CD.  I can find the file I need to edit using places, disk, boot, grub however when I try and save the changes I'm told i don't have permission.  Does that help ?

Thanks

---

### Post by forestpixie on 2008-01-20
much :)

easiest way in the live cd would be to open naultilus through terminal

gksudo nautilus

then navigate to the correct file - it will be unmounted to begin with - and open 

it should then be open with root rights and you can change it 

you need to make sure that it is actually the menu.lst that lives on your installation partition

hope that's a more useful answer

---

### Post by frup on 2008-01-20
You can also use chroot to log in as you on the LiveCD. Command line only though.

---

### Post by Chris2169 on 2008-01-20
Hi again,

I've opened nautilus fine, but it can only 'see' file system not the other partitions, including the one I need access too !!!!! grrrrrrr

---

### Post by frup on 2008-01-20
try sudo fdisk -l.

try mounting them.

---

### Post by forestpixie on 2008-01-20
double click the drive that corresponds to your installation on the desktop it'll open in nautilus - it'll likely be called 5Gb volume or however big it actually is

then close the file manager and then open it again with gksudo nautilus

frup - never needed to do chroot, so can't explain to the op - perhaps you could :) if you think it's easier

---

### Post by Chris2169 on 2008-01-20
The drive is on my desktop, its called disk.  I can double click it and find the file I need to edit, when I try and save it I get 'You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.'  When I do gksudo nautilus the window that opens appears only to see the files on the CD ? 

apologies if this is user stupidity, I know thats what got me into this mess, well trying to run before I could crawl safely anyway !

---

### Post by forestpixie on 2008-01-20
when you do gksudo .. go to /media - in there you'll see the partitions I think - perhaps try changing the left pane to tree or if it is places - it might seem more logical 

I know you can do it - I had to do exactly the same thing as you're trying to do - you can definetly navigate to the right partition and open the file from nautilus

I don't very often use the livecd so I' trying to remember how to get there

---

### Post by frup on 2008-01-20
if you do gksudo nautilus and then click file system can you see the drives again?

To chroot: basically type chroot /path/to/mounted/root you may want to add your user account if dealing with files in /home

SYNOPSIS

     chroot [-u -user] [-g -group] [-G -group,group,...] newroot [command]



DESCRIPTION

     The chroot command changes its root directory to the supplied directory
     newroot and exec's command, if supplied, or an interactive copy of your
     shell.

     If the -u, -g or -G options are given, the user, group and group list of
     the process are set to these values after the chroot has taken place.
     See setgid(2), setgroups(2), setuid(2), getgrnam(3) and getpwnam(3).

     Note, command or the shell are run as your real-user-id.

What chroot will do is mount your drives / as the liveCD's / but use the LiveCD's Gnome and GNU utils to allow you to fix and edit as if you running a working / 

I have only ever used it to change passwords though through <Alt> F1

---

### Post by Chris2169 on 2008-01-20
yes I finally got access to the file I thought was casuing the problem.  Sadly the orignal problem still exists but your info did help me do what I thought might solve it ! Many thanks for your help.  I'm going to sleep on the problem.  I think I may just reinstall it, it might be simpler !

---

### Post by forestpixie on 2008-01-21
if you let us know what the problem is we might be able to help,

---

### Post by Chris2169 on 2008-01-21
I've carried out a re-install which has fixed the secondary problem, I can now boot ubuntu on my laptop (and even with all the grief I think I'm slowly falling for Linux !).  The original problem I was trying to solve was slow boot.  But I'll search through the forums etc first and then if I can't find a solution I'll start a new thread rather than confuse this one.  Thank you everyone for the help I've had so far !  I suspect the real fun will start when I try to port my palm pilot and dive manager applications across !!!!!

Chris

---

