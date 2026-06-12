---
title: "A couple of ennoying things I hope to resolve"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by MockY on 2007-09-10
There's been some things that I have been bugging me for a long time and I hoped that they would be automatically resolved every time a new release comes around, but there are still a few things that never change and that I hope you have the answers for. If not, that's fine. I'm not leaving Ubuntu either way, but it would make life a little bit easier.

**1. **Many .jpg pictures are not displayed as thumbnails in Nautilus, even though they came from the same camera, shot at almost the same time and transfered to the computer at the same time. Why is this? There is not reason for it and is very annoying. Here is a picture to demostrate:

[IMG]http://www.sotd.se/thumbs.jpg[/IMG]


**2. **Except Amarok, is there any way at all to transfer playlists to and from an iPod? So far, only individual songs are possible. Tried every player out there and I just don't get it why this is not implemented in any of them by now. Would this change if I put Linux on the player?

**3. **My backup drive and slave has always been in NTFS, but I figured formating it in raiserfs would make it faster to read/write to. So I converted it to raiserfs and what do you know, it became extremely slow. When I mount it (which I have to do manually after every boot and extremely annoying) the entire system turns into glue (just opening a small .jpg takes about 8 seconds, no matter on what drive it resides). The system freezes after about 10 minutes and I have to restart the system by pressing the reset button. This as you all know is not good for the system at all. It seems like I have to go back to NTFS, which does not make any sense at all.

And while I'm at it, how is it that the drive doesn't show up under Computer from the places menu? And making a shortcut to it to place on the desktop or somewhere else where it is more easily accessible (having to manually go to /media/mountfolder gets old very quickly).

**4. **This can have to do with this particular install since I don't have this issue on my laptop, but even though I tell gconf-editor to display the trashcan on the desktop, it still doesn't appear. Homefolder, drives and other things works just fine to place or remove from the desktop, but not the trashcan. 

**5. **Is there any way to make a screenshot without saving it to a file directly? As of now, pressing printscreen, a dialog box pops up and you are forced to save it as a picture file. I want to be able to hit printscreen and then use Ctrl+V to directly paste in into Gimp or Photoshop. This saves me a couple of steps and in the long run a lot of time.

**6. **How do I go about to give someone SSH access to my computer but only be able to read and write in a folder I specifically allow? As of now, even though the user can't write to other folders, they still can browse and see read every file. This way I can use this as means instead of an FTP server which by the way is rocket science on Linux. None of the methods I have tried doesn't even come close to the usability of Serv-U. 

**7.** How come I can't ping the host names of the computers on the network and being forced to ping by IP numbers? Of course this applies to SSH as well, where I have to use the IP number and not the host name.

I hope some of these questions get answered. 

Thank you.

---

### Post by nonewmsgs on 2007-09-10
gtkpod rules for adding recursive directories of music files to ipod and it supposedly handles the playlists

an idea is to delte the thumbnails file (i think it's hidden in the folder with the pics) and when it rebuilds maybe it'll fix itself?

the rest you need someone greater than i.

---

### Post by tgalati4 on 2007-09-11
Couple means 2 and you listed 7 things.

For #7

Do you have all of your IP's and associated hostnames entered in /etc/hosts?

>sudo nano /etc/hosts

---

### Post by Chris S. on 2007-09-11
6: Can you assign the user to a unique group that is only allowed to view files and folders in their own home directory?

---

### Post by earobinson on 2007-09-11
1) Can you do a ```
ls -ah
``` in the directory

---

### Post by macogw on 2007-09-11
If you Rockbox the iPod, I think there will be other ways to sync it than just Amarok.

If you open a Nautilus to the drive then grab it from the top part above where you see files and drag the name to the left pane, it should get added to the Places menu.

Why not make your backup drive ext3?

If you want the drive to automount on boot, add it to /etc/fstab

---

### Post by MockY on 2007-09-11
> **earobinson said:**
> 1) Can you do a ```
ls -ah
``` in the directory

It lists every file with a green shade, including the ones not displayed as a thumb in nautilus.

[QUOTE=tgalati4]Do you have all of your IP's and associated hostnames entered in /etc/hosts?[/QUOTE]
This is not needed in a Windows environment, and since you don't have to manually enter it in the hosts file and still hit the specific computer on the network using only \\hostname or ping hostname, I figured it would work exactly the same way in Ubuntu since a computer always has a hostname and use tcp/ip to communicate. I mean, if a Windows box have the hostname of Thor, you can automatically ping it using that hostname, without adding anything manually in the hosts file. I guess it works differently here. 

[QUOTE=nonewmsgs]an idea is to delte the thumbnails file (i think it's hidden in the folder with the pics) and when it rebuilds maybe it'll fix itself?[/QUOTE]

This was an idea that I though would work on the NTFS disks, but it didn't. This happens on ext3 disks as well and does not seem to be related to the thumb file.

Furthermore, the gtkpod is not a player, even though a superior iPod tool. I want both (greedy I guess). But it is not that big of a deal if all I can do is drag and drop a folder into the iPod and it is then stored in the same fashion in the iPod and not as files in the root directory (playlist style)

---

### Post by Chris S. on 2007-09-11
Technically, computers do not "have hostnames".  A DNS name server somewhere will respond to DNS queries to "translate" the host name to an IP address*.  That being said, if hostnames don't work, but IPs do, then the problem must be DNS, and that's all I know.

Are you assigning hostnames for this network?  If so, then you must set up the DNS name server, otherwise you must specify the existing name server of the network, so your computer knows where to send DNS queries.

*Edit (clarification):  You send DNS query to name server (I want [www.google.com](www.google.com)), name server responds with IP (IP.address.of.Google), then your computer will send further requests to that IP.

---

### Post by tgalati4 on 2007-09-11
If you set up a static IP under Linux, then you have to manually specify things:  /etc/hosts, DNS nameserver, static IP, netmask, etc.  When you use DHCP, then it's automatic.  Windows works in a similar fashion--the networking stack comes from the same Unix/Linux roots.

---

### Post by earobinson on 2007-09-12
> **MockY said:**
> It lists every file with a green shade, including the ones not displayed as a thumb in nautilus.


This is not needed in a Windows environment, and since you don't have to manually enter it in the hosts file and still hit the specific computer on the network using only \\hostname or ping hostname, I figured it would work exactly the same way in Ubuntu since a computer always has a hostname and use tcp/ip to communicate. I mean, if a Windows box have the hostname of Thor, you can automatically ping it using that hostname, without adding anything manually in the hosts file. I guess it works differently here. 



This was an idea that I though would work on the NTFS disks, but it didn't. This happens on ext3 disks as well and does not seem to be related to the thumb file.

Furthermore, the gtkpod is not a player, even though a superior iPod tool. I want both (greedy I guess). But it is not that big of a deal if all I can do is drag and drop a folder into the iPod and it is then stored in the same fashion in the iPod and not as files in the root directory (playlist style)
I was intrested in the output to check the file sizes

---

### Post by irishgoth8822 on 2007-09-12
i use gtkpod, it works great and you can copy files from your ipod to your harddrive, which is lovely if you accidentally deleted them all from your computer :-p

---

### Post by MockY on 2007-09-13
> **earobinson said:**
> I was intrested in the output to check the file sizes

Hmm, I checked again, and it seems like every picture over 5MB can't be displayed as a thumb. How do I change that if possible?

---

### Post by Vogateer on 2007-09-22
To change the preview size for Nautilus:
[LIST=1]
[*]Open Nautilus
[*]Go to Edit > Preferences in the menu
[*]Click on "Preview" tab
[*]Change the "Only for files smaller than" setting
[/LIST]

I wouldn't set it for anything over 10, though.

---

