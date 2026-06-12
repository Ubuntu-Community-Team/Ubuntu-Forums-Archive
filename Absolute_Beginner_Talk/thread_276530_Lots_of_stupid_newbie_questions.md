---
title: "Lots of stupid newbie questions"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Scarlett on 2006-10-13
So I've been checking out Ubuntu for a few weeks now and I'd like to make it my primary OS but there's a few things I still need to work out to make this possible and was hoping to get a little help...

1.  I currently have Ubuntu installed on a secondary drive that's way too small and I want to reinstall it on a third drive.  Can I keep both installs or do I need to get rid of the first one before installing the second?  Also, the grub menu currently looks like a mess.  I've got at least 3 different Linux kernels and recoverys for each of those listed that I don't need.  How do I get rid of them?

2.  (Ok, this is a probably a really stupid question but I honestly don't know the answer.)  Can I copy all my mp3's, gifs, jpgs and psd's onto a DVD and transfer them to the new hard drive?  Even better... is there a way to access the stuff on my Windows drive from Ubuntu?  Oh... and where can I find WINE?

3.  How do I install drivers?  Ubuntu doesn't recognize any of my hardware.  Assuming I can find drivers written for Linux, how do I make them work after I've downloaded them?

4.  Could someone please, please, before I tear my hair out, tell me how to make Flash work on a 64 bit system?  I've heard there isn't a plug-in for 64 but I was unable to install Firefox32 as one of the many howto's I've tried suggested.  I got it all un-tarred and made a new file for it but it still doesn't work and I have no idea why.  I'm seriously banging my head against the desk over this one.

TIA!

---

### Post by Foudre on 2006-10-13
damn good quesiton, what is the command to mount a hard drive,i like ubuntu but the lack of root. some things still want root, even sudo won't suffice, and having to do it all via terminal can be annoying when you need rights and don't know all the commands.

oh for copying stuff i just burned to disk, my suse could mount ntfs drives, but only as root as user, not even with su... hmm funny

to install stuff, try and follow their instructions, sometimes the instructions are wrong, thats when it get annoying.. but i've gotten the install thingy sort of down, it takes a little bit to do via terminal, but if you can download the drivers with thte .deb extension (its linux file extensions mean nothing) thats a debian package, just click to open, and it will either install or give an error

---

### Post by igknighted on 2006-10-13
> **Scarlett said:**
> So I've been checking out Ubuntu for a few weeks now and I'd like to make it my primary OS but there's a few things I still need to work out to make this possible and was hoping to get a little help...

1.  I currently have Ubuntu installed on a secondary drive that's way too small and I want to reinstall it on a third drive.  Can I keep both installs or do I need to get rid of the first one before installing the second?  Also, the grub menu currently looks like a mess.  I've got at least 3 different Linux kernels and recoverys for each of those listed that I don't need.  How do I get rid of them?

2.  (Ok, this is a probably a really stupid question but I honestly don't know the answer.)  Can I copy all my mp3's, gifs, jpgs and psd's onto a DVD and transfer them to the new hard drive?  Even better... is there a way to access the stuff on my Windows drive from Ubuntu?  Oh... and where can I find WINE?

3.  How do I install drivers?  Ubuntu doesn't recognize any of my hardware.  Assuming I can find drivers written for Linux, how do I make them work after I've downloaded them?

4.  Could someone please, please, before I tear my hair out, tell me how to make Flash work on a 64 bit system?  I've heard there isn't a plug-in for 64 but I was unable to install Firefox32 as one of the many howto's I've tried suggested.  I got it all un-tarred and made a new file for it but it still doesn't work and I have no idea why.  I'm seriously banging my head against the desk over this one.

TIA!

I don't have much experience with 64bit, but I'll try to help on the first 3...

1) As far as the boot menu goes, open a terminal window and type:

```
sudo gedit /boot/grub/menu.list
```

you will see entries in the file that correspond to each option on the grub bootloader.  You can delete the ones that you don't need, but definitely leave the most recent kernel, the corresponding single user mode entry (useful later when dealing with drivers) and rescue.  After deleting the obsolete entries, save and exit.

2) That would be a fine way of transfering files.  The windows partition (I am assuming it is XP and hence NTFS file system) needs to be mounted to your Ubuntu OS, there is a how-to floating around on these forums somewhere, search for mounting NTFS drive.  I have never used WINE, I would guess that if you search on adept or synaptic you would find it, but I don't know if it needs anything else or how to configure it.

3) As far as drivers, there are many diferent solutions depending on what type of device isn't working... if you post the problematic hardware I can point you in the right direction.

Hope this helps, if you need any clarification just ask

EDIT: Assuming you just need more storage space, you can format your new hard drive as ext3 file system, and then mount it as /home/your_user_name/insert_name_for_disk_here/ and it will fit right into your file system nicely

---

### Post by Old Pink on 2006-10-13
If you want root user permissions for one session, hold Alt, tap F2 and type this in the box that appears: ```
gksudo nautilus
```If you want to always have root permissions, I can do that too, but I **DO NOT **reccomend it as it leaves you able to instantly destroy your system. If you want the information at your own risk, PM me. :)

---

### Post by Kateikyoushi on 2006-10-13
You can keep both installs if you like or remove the first while partitioning the second install. You can uninstall the unneceserry kernels with synaptic package manager.

System >> Administration >> Synaptic Package manager, then check the Installed ( local or obsolate ) packages.

You can backup your files to a dvd and use them in ubuntu, you can also mount your windows partition in ubuntu and see what files you have in windows. [How to do this.]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

Concerning the drivers tell us what doesn't work, we will help with the install it's different from windows.

I did not use 64bit ubuntu so can't help you about that.

---

### Post by tommcd on 2006-10-13
To mount windows:
[http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only)
For drivers:
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)
Scroll down to the section on 'hardware' Is there something specific you need?
I would not worry about the extra kernel entries in grub. If you have a problem after a kernel update, you can use them to boot to an older kernel. If you really want to get rid of them, read this tutorial on grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I don't know about flash for 64bit.

---

### Post by Scarlett on 2006-10-13
I'll try tackling that command line to delete menu items tomorrow.  Thanks.

As for the hardware, it's pretty much everything.  For right now I'm most concerned about the MSI mobo, Logitek 6 button mouse and Liteon DVD R/RW external drive.  I'm also fairly certain I haven't configured the nVidia card correctly either and I'd like to have all the options I had with XP.  I've got it to the point where at least my screen is at the right refresh rate but I'm still not seeing all the configuration options it should have.

---

### Post by Scarlett on 2006-10-13
Oooohhhh... about the root permissions....  Is there a way to enter that from the GUI that shows me where all the folders are?  I keep thinking I should be able to right click on a folder or a file and find somewhere to enter my password so I can move stuff around and so far that hasn't happened.

---

### Post by Kateikyoushi on 2006-10-13
Yes there is a script to be able to right click on a file folder in nautilus and open it as su, but can't find it now, still searching.

---

### Post by tommcd on 2006-10-13
> **Scarlett said:**
> Oooohhhh... about the root permissions....  Is there a way to enter that from the GUI that shows me where all the folders are?  I keep thinking I should be able to right click on a folder or a file and find somewhere to enter my password so I can move stuff around and so far that hasn't happened.

Just hit ALT+F2 and type 'gksudo nautilus' in the box that pops up (you will need to enter password). This will give you a GUI as root that you can navigate to any file/folder and modify as you wish. When done just close the window and you're back to being a regular user.
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Scarlett on 2006-10-13
Thanks!  That just made my life sooooo much easier.

---

