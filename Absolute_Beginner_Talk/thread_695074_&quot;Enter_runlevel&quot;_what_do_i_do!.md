---
title: "&quot;Enter runlevel:&quot; what do i do?!"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by strang3r on 2008-02-12
one day i attempted to update on the synaptic package manager and when i restarted it, it went to a black screen saying "enter runlevel:". what do i do to get back to ubuntu? if  must reinstall it wont be too much trouble for me.

---

### Post by strang3r on 2008-02-12
is this like dos for linux?

---

### Post by strang3r on 2008-02-12
any ideas?

---

### Post by taurus on 2008-02-12
Does it ask you to type in your username or does it already drop you into a shell, prompt?

---

### Post by strang3r on 2008-02-12
no all it says is enter runlevel

---

### Post by 1875 on 2008-02-12
Type in 5

---

### Post by Oldster on 2008-02-12
For Gutsy, I think runlevel 2 is correct to run the xserver.

---

### Post by Rocket2DMn on 2008-02-12
Runlevel 5 is multiuser GUI, this is what you want.

---

### Post by 1875 on 2008-02-12
> **Oldster said:**
> For Gutsy, I think runlevel 2 is correct to run the xserver.

I think we both may be correct.

[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html]("http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html")

---

### Post by Rocket2DMn on 2008-02-12
Fair enough!

---

### Post by 1875 on 2008-02-12
> **Rocket2DMn said:**
> Fair enough!

Just found it out myself.:)

---

### Post by strang3r on 2008-02-13
5 didn't seem to work nor did 2 
*INIT: Entering runlevel:(2 or 5)
*INIT: no more processes in this runlevel

---

### Post by strang3r on 2008-02-13
i pressed s for recovery. it says:
root@(none):~#

now what?

---

### Post by Rocket2DMn on 2008-02-13
Do you have access to a terminal under a normal boot?  i.e. Can you log in to a text interface?  If you can't on that screen, try doing CTRL+ALT+F1 to get to a tty.  If you can login to a tty, try running
```
startx
```

---

### Post by strang3r on 2008-02-13
doesn't look like it.

---

### Post by Rocket2DMn on 2008-02-13
Strange.  Get back to recovery mode and let's tell it to reconfigure X (the GUI).  At the "root@(none):~#" prompt, type in
```
dpkg-reconfigure -phigh xserver-xorg
```
This command usually requires "sudo" at the beginnig, but you are at a root prompt, so it is not necessary.  Then reboot the computer into the normal startup.

---

### Post by strang3r on 2008-02-13
it basicly tried and failed

---

### Post by Rocket2DMn on 2008-02-13
That was fast.  What did it tell you?

---

### Post by strang3r on 2008-02-13
give me a sce refresh every minute

---

### Post by strang3r on 2008-02-13
Starting up ...
loading please wait ....
kinit:name_to_dev_t(/dev/disk/by-uuid/98a5ece8-b8b1-413b-ae80-51fffae80-51fff8e35bad)
kinit:trying to resume from/dev/disk/by-uuid/98a5ece8-b8b1-413b-ae80-51fffae80-51fff8e35bad
kinit: no resume image, doing normal boot...

From there it simply sits there nothing happens

---

### Post by Rocket2DMn on 2008-02-13
At that screen, can you really not do CTRL+ALT+F1 (or F2, F3...., F6) and get to a tty (a text login area)?  This is under a normal boot, not recovery mode.

---

### Post by strang3r on 2008-02-13
im sorry i misread the forum im recovering the videocard now and pressed enter to nvidia now that?

---

### Post by Rocket2DMn on 2008-02-13
You're running the dpkg-reconfigure command then?  If your done with the reconfiguration, reboot the PC into normal mode and see if it lets you get to the GUI.

---

### Post by strang3r on 2008-02-13
well now that i select nvidia it says:
In: creating symbolic link `/etc/x11/x.dpkg-new' to `/usr/bin/xorg': Read-only file system

---

### Post by Rocket2DMn on 2008-02-13
OK, we're not on the same page, let's slow down.
Did you run the dpkg-reconfigure command?  If so, is that the error it gave you when you did?

---

### Post by strang3r on 2008-02-13
command not found

---

### Post by Rocket2DMn on 2008-02-13
So, at the recovery mode terminal, you ran this exactly as I typed it:
```
dpkg-reconfigure -phigh xserver-xorg
```
and it said command not found?

---

### Post by strang3r on 2008-02-13
yes i did and i select nvidia as my video card. it says:
In: creating symbolic link `/etc/x11/x.dpkg-new' to `/usr/bin/xorg': Read-only file system

---

### Post by Rocket2DMn on 2008-02-13
OK, I really don't understand why it's doing that, but it sounds like it's not mounting your root partition as read/write (with errors it remounts as read only).  At the recovery console, run
```
cat /etc/fstab | grep ext3
```
You should see the entry for your root partition ( at / ).  Remember what device this is (like is it sda2, or hda1, whatever).  Then you need to boot from the LiveCD and run a disk check.  Once the LiveCD is loaded, open a terminal and run
```
sudo fsck /dev/*hda1*
```
replacing *hda1* with the correct device.  If you get any errors, post them back here, otherwise a reinstall might be the next order of business.
By the time that disk check is finished running, I will most likely not be at my computer, so I will check back with you later today.  Best of luck.

---

### Post by strang3r on 2008-02-13
maybe god is telling me to start over because it says there is no such directory

---

### Post by strang3r on 2008-02-13
perhaps i can use my disk?

---

### Post by strang3r on 2008-02-13
i think im gonna use my disk

---

### Post by Rocket2DMn on 2008-02-13
You can certainly reinstall if you want, I tend to only suggest that only as a last resort.  If you have data on the hard drive you want to save, you can mount the drive from the LiveCD and transfer your files to an external hard drive or USB flash drive before you reinstall.

---

