---
title: "I don't have root password"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by mevasquez on 2007-04-13
I inherited a kubuntu machine and the old user is not around any more.  The version is 6.06 and it boots using Lilo.  I have booted up using the ubutu live cd, as well as, Knoppix.  I have mounted the partition to /root, which contains the root directory and then chroot to /root.  I did the command passwd root and it prompted me for a password, which I did and after confirming the password, it seems as though the password was changed.  However, when I went to boot the machine and then trying the new password, I was denied access. 

While doing my searches, someone had suggested removing the root password in the shadow- file, then I could log in without a password.  That did not work.

One suggestion was to change the boot option in grub; however, this machine boots up using lilo.  Is there a way to change this box to use grub because whenever a change is made in lilo.conf ( I tried to change inittab to boot to single mode) you have to run lilo and that fails.

Any new ideas?
TIA

Mike

---

### Post by bcmiller on 2007-04-13
Since you inherited the machine I would sidestep the entire issue and just do a fresh install.

If you need to back anything up you can use the live cd.

---

### Post by mevasquez on 2007-04-13
This guy was the old system admin and I am the new one.  I wanted to find out what tools he used on his old work station.  Could I just reinstall without formating?

Mike

---

### Post by compmodder26 on 2007-04-13
Try this:

Boot into the live CD again.
Mount the hard drive
Change into the live CD root user: sudo su (you shouldn't be prompted for a password)
Edit the sudoers file: nano /mountpoint/of/hardrive/etc/sudoers
Change the following line:
     %admin ALL=(ALL) ALL
To:
     %admin ALL=(ALL) NOPASSWD:ALL

Save the file then reboot (take the CD out).

You should now be able to operate sudo without being prompted for a password.  You can then add your user account to the admin group.

*Note: after doing this, it would be wise to change that line in the sudoers file back to the way it was.

I am assuming that no alterations were previously made to the sudoers file.

---

### Post by aysiu on 2007-04-13
A Kubuntu installation using Lilo? That's highly unusual.

In the boot menu, is there an entry for *Recovery Mode*. If there is, you can easily add a new user by booting into recovery mode and typing ```
adduser mike
adduser mike admin
reboot
``` If there isn't, you can probably use a live CD to *create* a recovery mode entry in the /boot/grub/menu.lst file.

---

### Post by compmodder26 on 2007-04-13
After re-reading your post, I think my assumption that you already had an account set up is incorrect.  However, it seams that your attempt at setting a root password was successful.  However, Ubuntu doesn't allow root logins graphically.  So, you have a few options here.  

A) Try what aysiu said.

B) Find out what file is used to control the settings that dissallow root logins in Kubuntu (sorry, I don't know this one)

C) Edit the runtime configuration.  To do this: 
1) Again, use the live cd.  Mount the hard drive how you did before.
2) Change the the directory /mountpoint/of/harddrive/etc/rc2.d (this directory holds the symlinks to all programs that should start in runlevel 2, which is the default runlevel)
3) Remove the symlink for S13kdm (the number may be different, just look for kdm)
4) Reboot (remove live CD)
5) You should now be brought to a command line login where you should now be able log in as root.
6) Do whatever is necessary to get yourself an account with root privileges (You seem to have a decent knowledge of linux commands so I won't go into details.  If you need help, just ask).
7) Add the symlink back for S13kdm (it should point to the "kdm" script in /etc/init.d

---

### Post by mevasquez on 2007-04-13
compmodder26, do I log in using the name sudo?  I tried to login using the name sudo with no password and that did not work.

Mike

---

### Post by compmodder26 on 2007-04-13
With the live CD, you shouldn't have to log in.  It should log in automatically.

---

### Post by mevasquez on 2007-04-13
Still no luck.

I removed S99gdm from rc2.d, rc3.d, rcS.d.  He was running gnome. There was another script called S99stop-bootloged-single, which I removed.

Also, there is no menu.1st file.  Is there anyway to change the bootloader from lilo go grub using the live CD?

It seems that I was able to create an account with a passwd but it still will not let me in.

Thanks for all your advice.

Mike

---

### Post by Maestro23 on 2007-04-13
This is the file:
> /boot/grub/menu.lst (lowercase L)

---

### Post by mevasquez on 2007-04-13
I mean menu.lst.  There is no directory under /boot.  There are grub commands, such as:
   ```

    grub-install
    grub-reboot
    grub-set-default
    grub-terminfo
    grub-update-grub
   
```

It would be nice to change the boot loader from lilo to grub.
TIA

Mike

---

### Post by mevasquez on 2007-04-13
I got the following from another link, [http://www.debianhelp.co.uk/lilo.htm:](http://www.debianhelp.co.uk/lilo.htm:)
" Debian Sarge by default uses the Grub boot loader. Whether to use Lilo or Grub is a matter of taste. Actually they do not look much different when booting the system. But Grub has a tiny built in shell that allows you to boot certain partitions even if your boot configuration is broken. If you had used Lilo and made a mistake in your lilo.conf you would need to get a rescue disk.

These are the necessary changes to switch from Lilo to Grub

According to the /usr/share/doc/grub/README.Debian file you need to change the file /etc/kernel-img.conf:

postinst_hook = /sbin/update-grub
postrm_hook = /sbin/update-grub
do_bootloader = no

Unlike Lilo, it is not necessary to re-run or re-install the boot loader after every change to /boot/grub/menu.lst. menu.lst is automatically found on GRUB's root disk and read during GRUB's boot process.

Run grub-install /dev/hda to install the boot loader.

Do not forget to run "update-grub" after the installation to update the menu list to your current list of kernels.

/dev/hda does not have any corresponding BIOS drive.
Check the /boot/grub/device.map if it looks correctly like this:

(hd0)   /dev/hda"

I did all this and it still uses Lilo 22. somthing.

---

