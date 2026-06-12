---
title: "Modifying Windows 7 Recovery Image"
date: 2013-02-22
forum: Any Other OS
---

### Post by Marked One on 2013-02-22
Hello All.

First Off, some background:

I'm in a bit of a quandary, seeing as I have tried to update the graphics drivers on an HP dv7 while running windows. (I've given up on doing that with fglrx And the other variants thereof in Ubuntu). Long story short, windows 7 is no longer functional and has had its partition re-formatted. There is A recovery partition present on the hard disk, but from what I understand a recovery from a Factory Image will lead to the destruction of my Xubuntu Install. There is no Windows Install Cd.

My question is: 

Can this recovery image image be modified to point to /dev/sda2 (or whatever the windows designator is), instead of the entire drive such that the Windows will be restored while Xubuntu will not be destroyed? I can restore GRUB easily enough, the only question is whether this modification can be made. 

Specifications (Will be Updated As Requested):

Brand: HP
Model: DV7
Hard drive Layout: Three Primaries (windows (now empty NTFS), boot, recovery), one extended that holds the Xubuntu/SWAP/Home-Folder

Any Help would be greatly Appreciated!

Kind Regards,
Ivan Kozlov

---

### Post by mips on 2013-02-23
You usually have the option of creating a installation dvd from within the OS but seeing as you deleted that it's no longer an option.

The only way out I see is to download a HP installation image and use your own license key.

---

### Post by varunendra on 2013-02-23
I can see two options -
[list=1]
[*]Install [Remastersys]("http://www.geekconnection.org/remastersys/ubuntu.html") and create a 'Backup' DVD of your installation. Or,
[*]Create a [Clonezilla]("http://clonezilla.org/downloads.php") image of your Xubuntu installation (on an external drive)
[/list]

I recently saw a post mentioning that the poster was having problem with both methods in 12.10, although I believe clonezilla should be a sure-shot method as it does not depend upon file-system or OS on it.

Regardless, I'd suggest to test the remastersys dvd / clonezilla image on a virtual machine to make sure it works, then proceed with system restore on the notebook.

Once the backup of your xubuntu installation is created and tested successfully, restore the notebook to factory settings and restore the xubuntu backup later on it - just like you previously installed it.

In case of  clonezilla image, you may have to install grub separately, which can be easily done using either the original installation cd of Xubuntu or [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") on its live session.

Let us know if you have any doubts or are having any problems following this.

---

