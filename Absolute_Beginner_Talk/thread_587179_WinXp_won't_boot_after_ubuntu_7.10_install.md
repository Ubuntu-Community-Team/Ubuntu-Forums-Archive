---
title: "WinXp won't boot after ubuntu 7.10 install"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Theodoric on 2007-10-22
I installed ubuntu 7.10 today.  
My alien area-51 has winxp on it, i used partition magic and let it run the fun of setting up partitions for a dual boot. 
something went wrong.
I can see the entire xp file structure from ubuntu
I cannot boot into xp normally, it gets as far as the windows logo and the running bar then gives me autocheck not found then fatal system error.
I cannot boot into xp safe mode, it just restarts after a few moments

I can get all my files from linux as i said above, but there has got to be an easier way.

when I try to do a repair install, xp disk says it can't install w/o deleting and recreating a new partition.

when i try to use the recovery console, it asks me for an admin password that I've never used.

Help

---

### Post by Baby Boy on 2007-10-22
Like many times before, my advice is - use GAG to fix Windows. 

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

I was in the same situation, and none of that fix MBR stuff worked because I kept getting asked for that Administrator password (which doesn't exist) and by googling I found out it's a bug which is very, very hard to fix. GAG is like a small Linux which you burn to a CD and use as a boot manager (to boot your broken Windows).

---

### Post by Hospadar on 2007-10-22
you probably overwrote the windows master boot record with grub, you can use a windows cd with recovery console and use the "fixmbr" command to replace the windows bootloader.

Alternatively you could manually locate the bootloader by pulling it off the cd and putting it onto the root of your cd drive (with the ntfs-3g drivers for example)

You'll need the "ntldr" file and I believe and maybe a couple others.  I'm not sure exactly which, but i'm sure you can locate an accurate list with the google machine.

---

