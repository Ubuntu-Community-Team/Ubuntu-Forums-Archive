---
title: "[SOLVED] Just installed and forgot user name"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Regit on 2007-08-27
Hi guys.. I have just installed Ubuntu 64 {I hope} and I got it all installed and up and running.
But when I went to log in for the very first time I forgot or haven't put in are user name for this OS.

I am also lost.. I have windows installed as well which I am using to make this post.
When I went to load up linux {Ubuntu} it didn't just say Ubuntu / Windows it had afew other Ubuntu to select so I don't know if I selected the right one or I have to reinstall the OS to work out this user name.

I know the PW for the user name.. Well the PW I typed in when asked me too just the user name I don't know.
So If you know what the user name is { if it is universal for first time install's then you change it } Or some way to work around it would be great.

Thank you for all your help.
Regit the n00b.:lolflag:

---

### Post by freebeer on 2007-08-27
nope.. there's no default username... you're prompted for it during the installation.  So try whatever you think you'd generally use for such a prompt.  "regit", maybe?  Remember that Linux is case sensitive and in the case of Ubuntu (I presume this is true of other distros), the first character is lower case.

---

### Post by dpar on 2007-08-27
You can probably use the live cd and look at the ubuntu file system. Look for the 'home' directory. In that directory will be a folder with your login name.

Usually the top entry in grub will be the one you pick to load ubuntu. Unless you have changed the menu.lst file, it will be highlighted by default.

---

### Post by aysiu on 2007-08-27
Reboot.

Select recovery mode (usually the second boot option).

Type ```
cd /home
ls
``` Your username should be there. ```
reboot
``` Select the normal boot option (usually the top one).

---

### Post by aspen_dv on 2007-08-27
ok, when you reboot and it show you couple of Ubuntu options (also know as Grub) which you can select which one to boot into. Just select the first one on the list, press e (stands for edit. Then go to the kernelt line, looks something like:
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet

press e again and add 1 (or single). E.g. kernel          /boot/vmlinuz-2.6.20-15-generic root ro quiet splash 1

Press enter to save and b to boot.
It should take to single user mode command prompt.
At this point do:
vi /etc/shadow
Look at the bottom see if you recall your user name, then remove everything between the first 2 colons.
Before:    testuser:$1$cia.hKfq$ZX6hvy/3V97phzpi1Sibp0:13753:0:99999:7:::
After:    testuser::13753:0:99999:7:::
That will remove the password for testuser. Don't forget to force save the file with  wq!
You can reboot normally and try to type in that user name. Once log in you can change you password again.
Hope this helps

---

### Post by Regit on 2007-08-27
Thank you for the fast reply!!! 

I will try the live CD to see and I will also try the case sensitive.
If it ends up I have reinstall then I will.. { Great thing is it doesn't take hours to install :) }
So once again thank you!

---

### Post by dpar on 2007-08-28
Follow Aysiu's advice.......it's probably spot on:biggrin:

---

### Post by sacater on 2007-08-28
load into recovery mode as the other guys said. 
then run these commands one at a time, the brackets are descriptive

cd /home

ls (list, should list users on comp in this case)

passwd john (replace john with the real login name)

shutdown -r now

--------

you should then be able to log in. Otherwise it looks like you will need to reinstall ubuntu with a new UN and PW

---

### Post by chuckyp on 2007-08-28
> **aysiu said:**
> Reboot.

Select recovery mode (usually the second boot option).

Type ```
cd /home
ls
``` Your username should be there. ```
reboot
``` Select the normal boot option (usually the top one).


Why not just?
```

ls /home

```

At least instead of changing directories first.

---

### Post by bodhi.zazen on 2007-08-28
You do not need to re-install

Find your user name as aysiu described

Then, still in recovery mode, enter this command :

passwd <username>

This will set a new password

Now , reboot :)

---

### Post by Regit on 2007-08-28
:guitar:Got on to it!!!!!!!

Thank you all for your help.
I just got to fix some other stuff to get it all up and going the way i like.

So thank you again for all your help and replys
Regit the slowly un-noob :lolflag:

---

