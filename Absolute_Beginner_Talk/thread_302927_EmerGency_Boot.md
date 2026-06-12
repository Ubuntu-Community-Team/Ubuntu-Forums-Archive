---
title: "EmerGency Boot"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by kiyometane on 2006-11-19
Now i cant boot into edgy. I'm stuck at loading screen.
Do u know how to recreat the boot sector just like "fixboot/fixmbr"
in windows?](*,) ](*,) 
Thanks

---

### Post by David_T on 2006-11-19
Hello,
   Have you ever been able to boot into edgy, or is this right after upgrading?  If you have been able to boot before, is there anything that you installed or changed in the meantime?  
   One thing to try would be to reboot, get into the grub menu before the three seconds are up, and try booting into recovery mode.

---

### Post by kiyometane on 2006-11-19
i have been able to boot into edgy
i just changed the hdd with ubuntu to another controler to be able to install a third hdd.
i would be able to boot in windows.
how would fix the problem?
remember i'm new to linux
thanks

---

### Post by Peepsalot on 2006-11-19
In linux, hard drive devices are named as hda, hdb, hdc, etc.
I think the problem is that if you connect your hard drive to a different port, this will cause it to be named differently(for example if it was hda before, maybe it is hdb now.).  The problem with this is that there are configuration files that are still refer to the old hard drive name.  Also, your BIOS might be set to boot from a particular hard drive which has now changed position.

Is it not possible to connect the drive the way it was before?  Can you explain exactly what you mean when you say you changed it to another controller?

What loading screen are you stuck at, what does it display?

---

### Post by kiyometane on 2006-11-19
my motherboard had only 2 sata ports connection for hardrives.
I had to install a sataII controller (silicon 3124) to support more than 2 hardrives.
I moved the hdd with edgy to the sataII controller, it is now hdb.
The grub will load fine with operating system choices.
I just cant boot into edgy.
But if i move the edgy back to original port, i have no problems.
But i want to install more hdds.

---

### Post by Peepsalot on 2006-11-19
Try editing your grub configuration.

on my computer, it is the file /boot/grub/menu.lst

Find the boot option that you are trying to fix in this file.
On mine it looks like this:
```

kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdd2 ro quiet splash

```
So you want to change the root device to point to the new location.  I think this should allow grub to boot Ubuntu, but I'm not sure if there are other config files that will need changing, because I've never tried such a thing.

---

### Post by kiyometane on 2006-11-19
yes but how do you enter the command and where ?

---

### Post by Peepsalot on 2006-11-19
> **kiyometane said:**
> yes but how do you enter the command and where ?
Well the file /boot/grub/menu.lst is a text file.  So you can edit it with any text editor.

Personally I like to use nano for simple text editing.  So in a terminal run```
sudo nano /boot/grub/menu.lst
```

Now of course, you'll have to be able to boot into *something* in order to edit this file.

You have two options that I see:  

1) You can temporarily put your drive back into the configuration that boots, and edit the file.  Once this file is edited, this configuration won't work anymore.  You can always try to make a copy of the working boot options in the same file though.

2) Or you can use a liveCD so that you are able to boot into something that will allow editing.  For situations like this that use command line only, I prefer [Slax Frodo edition](http://www.slax.org/download.php) because it's simple and quick to boot into.  Of course, you can use to Ubuntu liveCD or any CD you prefer.  The complication with this is that you will probably have to mount the drive manually using the mount command.  

The way to use mount is:
```

sudo mount device dir

```
Where you replace "device" with something like "/dev/hdb2".  hd stands for hard drive, the letter after that refers to the particular drive, and the number is the partition number for your root partition.
And replace the "dir" with the directory that you are mounting to.  On a normal bootup, your root partition is mounted to the root directory "/".  But when using a livecd, the liveCD itself will mount to the root directory.  So you'll need to use a different one.  a common place to mount would be "/mnt".

for more information:
```
man mount
```

Hope that helps.

---

### Post by kiyometane on 2006-11-19
the commade you gave me do not work.
i dont know if it is because i'm using gnome not kde.
is there another way?

---

### Post by Peepsalot on 2006-11-19
Which command didn't work, and what did it say when you tried it?

---

### Post by kiyometane on 2006-11-19
only the command "man mount" works.
i may be doing something wrong.

I'm able to run the life cd.
so first do i have to type "sudo nano /boot/grub/menu.lst"
then "sudo mount device dir" ?

---

