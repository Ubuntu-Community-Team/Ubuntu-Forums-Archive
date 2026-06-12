---
title: "Kernels gone from menu"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by TheSe7enthSin on 2007-07-02
I tried to find the solution to my issue, but I couldn't find it. Hopefully someone can find an easy one for me.

I was on Ubuntu (I run 7.04) earlier today & I changed a setting. And now I cannot load Ubuntu anymore. I don't remember the exact names of the menus, so bear with me.
I remember I went to "Startup-Manager" (where you can edit the grub boot time, etc.). I wanted to hide a kernel that I never use (the one that was released when fiesty came out)

In the startup-manager, I remember clicking the last tab and seeing a setting. I cant recall the exact text, but there was a checkbox & a box with a number indicating how many kernels to see. The number I had was 2. I changed it to 0 I believe.

Now when I turn my laptop on, all I see is the option for "Memtest" & my Windows partition. My 2 kernel options & recovery mode are gone. I tried to search & figure out a way to get them back, but I'm at a loss. I'm still fairly new to the linux game and any help on recovering my menu would be appreciated.

---

### Post by Vajra Vrtti on 2007-07-03
[LIST=1]
[*]Boot from the Ubuntu 7.04 CD.
[*]Locate your Ubuntu boot partition in your HD.
[*]Edit the file **/boot/grub/menu.lst** in your boot partition.
[*]Probably you will have a line like this -> **# howmany=0**
[*]Change it to -> **# howmany=all**
[*]Save the file and reboot.
[/LIST]

---

### Post by TheSe7enthSin on 2007-07-03
bump
Anyone out there that can help? I miss my ubuntu and i don't want to resort to reinstalling everything & losing all my data. =[

edit: Sorry,didnt see the post. Thanks, i'll go try that out

---

### Post by TheSe7enthSin on 2007-07-03
So changing the howmany to "all" didn't work. Looking through the menu.lst, I noticed that the other boot options were not listed. Just the memtest "partition" and my Windows partition.

But I noticed there was a menu.lst.backup located in my grub folder. I guess the startup-manager created it. Which I am extremely happy it did. I was hoping to not recreate the option from scratch (even tho I was getting ready to make it until I noticed the backup). So yea, I did a "sudo mv" on the menu.lst and got the backup running.

All is well and I will not touch it again. XD
Thanks again for your help.

---

### Post by Vajra Vrtti on 2007-07-03
I'm glad you survived.  :D

But not to depend on luck a second time, I suggest that the first thing you do after installing a new system should be a backup the following files:
[LIST]
[*]/boot/grub/menu.lst
[*]/etc/fstab
[*]/etc/apt/sources.list
[*]/etc/X11/xorg.conf[/LIST]
It may be a good idea to do that right now!

---

### Post by mysticrider92 on 2007-07-03
> **Vajra Vrtti said:**
> [LIST=1]
[*]Boot from the Ubuntu 7.04 CD.
[*]Locate your Ubuntu boot partition in your HD.
[*]Edit the file **/boot/grub/menu.lst** in your boot partition.
[*]Probably you will have a line like this -> **# howmany=0**
[*]Change it to -> **# howmany=all**
[*]Save the file and reboot.
[/LIST]

I guess this is a bit late, but wouldn't having the # sign in front of the howmany line make the line useless?

---

### Post by Vajra Vrtti on 2007-07-03
It seems so but if you look some lines above you will see the following warning:
> 
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## **DO NOT UNCOMMENT THEM**, Just edit them to your needs
And after the automatically maintained kernel list you find:
> ### END DEBIAN AUTOMAGIC KERNELS LIST

I don't know enough about the grub and debian update processes to explain why it is that way, so I humbly obey. :)

---

