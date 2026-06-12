---
title: "Kernel Panic -- not syncing: No init found."
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by LarryJ2 on 2008-02-06
If you get a ***"Failed to execute /init....Kernel Panic -- not syncing: No init found.  Try passing init= option to kerne***l" error message,  give this a try before you give up and reinstall:

1 Reboot by holding the power on/off button or powering the PC off and then on again.

2 When you see *Ubuntu 7.10, kernel 2.6.22.14-generic*,  hit a key to stop the count down.

3 Use your cursor keys to highlite the line  [I]Ubuntu 7.10, kernel 2.6.22.14-generic
[/I]
4 Hit e to edit the line

5 Hit the down arrow to move the highlite  to the third line which reads
> initrd /boot/initrd.img-2.6.22-14-generic.

6 Change that line to read
> initrd /boot/initrd.img-2.6.22-14-generic.bak
using your cursor keys and keyboard.

7 Hit enter to make the change

8 Then hit b  to continue the boot sequence.

With any luck your PC will boot normally.   I don't know what happened to the original file*** Ubuntu 7.10, kernel 2.6.22.14-generic***  but obviously it is corrupted since the backup works. 
Now if I can figure out how to get a fresh copy installed.

You'll have to edit this line each time you boot until you fix the corrupted file. (At least that's current theory!)   :(

---

### Post by LarryJ2 on 2008-02-06
A little more digging revealed that  an update of kismet apparently did the dirty work.  Either I interrupted the upgrade or the Kismet upgrade script is faulty.  I'm guessing that the  ***initrd /boot/initrd.img-2.6.22-14-generic.bak***    backup file was created by the kismet upgrade process so, therefore,  you may not have one in your /boot directory.  Therefore, this "solution" may not be of any value then  unless you were attempting to upgrade kismet prior to your "kernel panic".

No wonder I seem to be the only one affected.

---

### Post by Sheix on 2008-03-16
Oh, man thanx, it worked well!

I've got following error because of power shutdown while doing sudo dpkg.reconfigure -a, bad luck :)

---

### Post by TheDeivix on 2008-04-28
Phew!

Thanx for the help LarryJ2, by following your advice i was able to boot, then i did the following:

i made a backup of *initrd.img-2.6.22-14-generic.bak*, since this was the last image i was able to boot with i thought it was a good idea to take this extra precaution.

Then: 

```

  488  sudo dpkg-reconfigure linux-generic 
  489  sudo dpkg-reconfigure linux-image-2.6.22-14-generic 
  490  sudo dpkg-reconfigure linux-image-generic 
  491  sudo dpkg-reconfigure linux-restricted-modules-2.6.22-14-generic 
  492  sudo dpkg-reconfigure linux-restricted-modules-common 
  493  sudo dpkg-reconfigure linux-restricted-modules-generic 
  494  sudo dpkg-reconfigure linux-ubuntu-modules-2.6.22-14-generic

```

I don't know which one of those lines solved the problem but after that i was able to boot normally

I thought of another solution in case of the last lines not working, (not an elegant one though) editing /boot/grub/menu.lst to make my backup of *initrd.img-2.6.22-14-generic.bak* the default image, fortunately i didn't need to do this.

Hope this helps :)

---

