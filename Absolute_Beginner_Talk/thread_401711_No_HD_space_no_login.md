---
title: "No HD space no login"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by j002 on 2007-04-04
I've run out of HD space and now I can't login.

I press Esc after POST and I boot in rescue mode but it won't accept the root password.

What now ?  How do I change the password from grub ?  Can I get a boot floppy ?

---

### Post by amohanty on 2007-04-04
Boot from live cd, mount drives and wipe out extra stuff, and try again.

AM

---

### Post by LaurelLynn on 2007-04-04
Dear j002,

If you still can´t get in after the space is cleared:

At some point at the beginning of the boot process you should see ¨boot:¨ , at that point try entering ¨single¨ or ¨init=1¨. That should get you to a root prompt ¨#¨ (unless you set a GRUB password). At which point you can run:

#passwd user-name

Then enter a new password. If your still stuck you might try the Live CD. After booting you should be able to type something like (the names depend on which partition is your root):

sudo umount /media/hda1   (or umount /mnt/hda1  if that´s where it is mounted)
sudo mount -o rw /dev/hda1  /media/hda1
sudo chroot /media/hda1 passwd username

The first command is just in case it´s already mounted. After mounting the drive and running the last command you should be prompted for a new password for ¨username¨.

Last ditch option is to boot to the Live CD, mount the drive, then gedit ¨/etc/shadow¨. Find the username. The second entry between the colons is the password hash. If you remove it and leave nothing between the colons the account should require no password (write it down first just in case).

Laurel Lynn

---

### Post by amohanty on 2007-04-05
That was so much better :)

AM

---

### Post by j002 on 2007-04-10
Thanks.

I was mucking around under "Users and Groups" and I think I might have changed the root password (which is different to the user password, it's usually not set).

So after changing root password on the live cd I rebooted into text as root and typed :

startx

So then I could run Synaptic (cos removing files from the prompt is completely hit-and-miss).

---

