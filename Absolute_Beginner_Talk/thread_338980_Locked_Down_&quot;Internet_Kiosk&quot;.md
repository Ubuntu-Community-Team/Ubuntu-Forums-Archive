---
title: "Locked Down &quot;Internet Kiosk&quot;"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by lordmeatball on 2007-01-15
I'm looking for simple solution for an "Internet Cafe". I have 8 computers in the public domain which I would like to lock down. I've tried installing WinXP with an Internet Kiosk application, but eventually someone cracks it. They do something malicious, then I have to rebuild the computer from image.

I started looking at some Linux solutions, thinking it would slow them down. There are far less people that know their way around in Linux.

I've tried using a LiveCD (I tried like 10 different distros), which worked great at first. The only problem is it's not flexible enough (some distros don't include Flash, etc.). I even tried making a custom LiveCD, but it would be too cumbersome to update the systems often.

So this is kinda what I'm looking for:

-Full featured O/S
-Office application (OpenOffice or at least Word/Spreadsheet)
-Locked down, the user can use any applications but they can't make changes to the system. (Not even changing the desktop, internet shortcuts, or wallpaper)
-if the users did find a way to destroy the system (or it crashes), an easy way to rebuild
-Easy to manage 8 or so computers. It would be nice if I could make a change to the desktop without touching each desktop

I think the ideal solution would be for each computer to network boot off an image on a "server". Then have an each way for me to boot that image and make any changes which would change all the desktops the next time they reboot. I'm not sure if such a solution exists, building a server with DHCP/PXE would be a possibility with good documentation.

I'm not a complete noob, but not a Linux guru.

Thanks-

---

### Post by Sef on 2007-01-15
> -Full featured O/S
-Office application (OpenOffice or at least Word/Spreadsheet)
-Locked down, the user can use any applications but they can't make changes to the system. (Not even changing the desktop, internet shortcuts, or wallpaper)
-if the users did find a way to destroy the system (or it crashes), an easy way to rebuild
-Easy to manage 8 or so computers. It would be nice if I could make a change to the desktop without touching each desktop

I think the ideal solution would be for each computer to network boot off an image on a "server". Then have an each way for me to boot that image and make any changes which would change all the desktops the next time they reboot. I'm not sure if such a solution exists, building a server with DHCP/PXE would be a possibility with good documentation.


Check out [Edubuntu.org]("http://edubuntu.org/").

---

### Post by lordmeatball on 2007-01-15
Actually, I did. It seemed very kid-oriented, the group I'm working with are adults. Does it have lock-down tools built into it??

---

### Post by bonzodog on 2007-01-15
hrm...lets think about this another way:

I have run internet cafes since 1996, and we tried locking them down, but found it actually **encourages** people to try and break them, and do malicious things. In the cafes we left unlocked, all we did was uninstall anything that could be harmful, as they were win machines, we put a virus checker, and anti spyware checker on them, both of which ran themselves overnight once a week. 

We installed an IRC client (mIRC, or XChat), and MSN Messenger, and MS Office (Later OpenOffice), and found that they covered 99% of all activities that the customers wanted. Also, the kids found there was nothing to crack or break, and it took their fun away. They soon just became normal, internet using customers. 8 machines is not a lot. One of the ones I still help out at occasionally here in Galway where we have 20 Internet cafes, has 30 machines on 2 floors!!. 

oh, we have also since installed Firefox on all the machines. There really is NO advantage to locking down the machines.

Think about it; what is the WORST that they could do with un-regulated machines? disable the OS maybe. Easy, can be solved in <10 minutes. Put a hidden, protected partition on the HD with a restore image of windows in it. Run the restore prog when needed, it deletes any settings and malicious software the people may have downloaded. The restore prog is set-up in such a way that  it will restore settings that YOU want, even down to the desktop background!.

Also, if you go the linux route, which I have in a couple of places, the machines run in the user accounts anyway. They can't do anything harmful to the machines from the user account, unless they somehow get the root password, which only the admin alone should have.

We literally set up a user account on each machine and just called it "Machine 1, Machine 2," etc... if the last user accidentally logs out the desktop, then you just need to go and type in the user pass, which you don't give away to ANYONE.

---

### Post by lordmeatball on 2007-01-15
Thanks bonzodog, but we started with machines that were not locked down. It gets ugly real quick. Maybe you are dealing with a different crowd. I keep an image of each machine on DVD, I can restore it in about 10 minutes.

I'm hoping I can find a Linux solution that's a little tougher to crack.

With a standard user account, they can change plenty on the desktop. One of the biggest problems is them posting a picture of their favorite p0rn star on the desktop. Not so nice for the other clients. That's only the beginning.

There are alot of people who have setup Internet Cafes, someone has to have a nice solution......

---

### Post by anders_gud on 2007-01-15
Ok! Haven't tried this, but changing the owner/permissions for:
~/.gconf, .gnome2  etc... (where most of the user settings resides) to admin/root rw and the rest read only?

---

### Post by lordmeatball on 2007-01-15
> **anders_gud said:**
> Ok! Haven't tried this, but changing the owner/permissions for:
~/.gconf, .gnome2  etc... (where most of the user settings resides) to admin/root rw and the rest read only?

Sorry, since I am a noob, I have no idea what this means.

---

### Post by anders_gud on 2007-01-15
Hi!
Every file on the Linux system has owner permissions associated with it. So for example: if you open a terminal and type ls -al you'll get a listing much like this:
anders@jupiter:~$ ls -al
totalt 56080
drwxr-xr-x 135 anders anders     8192 2007-01-15 11:40 .
drwxr-xr-x   6 root   root       4096 2006-10-19 22:31 ..
drwx------   2 anders anders     4096 2006-01-29 18:55 .alsaplayer
drwxr-xr-x   3 anders anders     4096 2006-10-24 17:17 .anjuta
-rw-r--r--   1 anders anders      145 2005-10-16 16:39 .appletviewer
drwxr-xr-x   9 anders anders     4096 2006-12-29 21:54 Apps
-rw-r--r--   1 anders anders      168 2005-10-17 10:00 .arbarorc
drwxr-xr-x   3 anders anders     4096 2006-11-30 22:36 .armagetron
-rw-r--r--   1 anders anders      763 2006-01-29 22:27 .asoundrc
drwx------   6 anders anders     4096 2007-01-14 21:49 .gconf
drwx------  25 anders anders     8192 2007-01-14 21:46 .gnome2 ...

Files that begin with a dot are "hidden" and most likely they're configuration files for different programs. What you should be looking for is the config files for Gnome (the ui.), gconf (sort of like M$ win registry) and other apps you want to lock down.

Changing ownership and read/write permissions on these files should (theoretically) render it impossible for the regular user to write to or change the settings.

Of course some apps like Firefox needs to have write access to cache/download directories, so finding the right ownership/permission combo can take some experimenting...

for instructions on changing ownership on files:
man chown
and permissions:
man chmod

---

### Post by lordmeatball on 2007-01-15
OK, thanks, this is a start.

So to take it a step further, is there a an easy way to make these changes to a profile then be able to copy this profile to each machine? Maybe a structure like Active Directory where I could create this locked-down user on a server and the clients logon to the desktop with this user??

---

### Post by Matt Yun on 2007-01-15
KDE has a kiosk mode.  Here is a tutorial:  

[http://developer.kde.org/documentation/tutorials/kiosk/index.html](http://developer.kde.org/documentation/tutorials/kiosk/index.html)

If you google 'KDE kiosk', you'll find more articles.

---

### Post by lordmeatball on 2007-01-15
Thanks Matt, that looks promising. I'll fire up some kubuntu and start playing.

---

### Post by jeremy on 2007-01-15
The "KDE Kiosk admin tool" is in the repositories, it is called kiosktool.

---

### Post by anders_gud on 2007-01-15
> **lordmeatball said:**
> OK, thanks, this is a start.

So to take it a step further, is there a an easy way to make these changes to a profile then be able to copy this profile to each machine? Maybe a structure like Active Directory where I could create this locked-down user on a server and the clients logon to the desktop with this user??

Yes, sure! Use LDAP as directory service and mount user homes via NFS.

---

### Post by lordmeatball on 2007-01-15
Can anyone comment about the differences between Kiosk Admin tool for KDE vs. Pessulus for Gnome?? Personal preference or is one superior to the other??

Thanks.

---

### Post by fujikofujio on 2007-03-10
I have been looking for an opensource solution to this problem as well, I work for a public library and would very much like to provide kiosk terminals for public use.

No luck with ubuntu on doing this, however I did find a tool from microsoft that has worked well for our needs (we use windows xp pro sp2). I know this is not an opensource solution but at least the toolkit is free to use.

[http://www.microsoft.com/windowsxp/sharedaccess/default.mspx](http://www.microsoft.com/windowsxp/sharedaccess/default.mspx)

The toolkit allowed me to restrict a profile so that users 
* could not change any setting on internet explorer.
* they can browse the file system but are restricted in creating files on their home folder only.
* files they save on the disk are deleted after they logout and a fresh profile is ready for the next patron. It comes with a deepfreeze like feature called windows disk protection.
* they can use all the applications that I installed, all changes to applications are erased when they logout. (openoffice, gimp, tuxtype, msoffice, inkscape, audacity, scribus, celestia : just some of the apps we have)

I was able to make an image of the main partition after I configured everything correctly using partimage ( I booted with systemrescuecd and used partimage and transferred the image on our ubuntu fileserver )

So now whenever we add new machines all I have to do is re-image it using partimage, I haven't found a machine that was broken into or hacked. The patrons we get are diverse, kids, teens, adults, engineers etc.

---

### Post by thenone on 2007-07-11
I own cyber cafe too, and I am also a free lancer, I've setup a internet kiosk for a several hotel in east coast malaysia, and my solution for them was LTSP. One of my client is [Residence Inn Cherating]("http://www.ric.com.my"), the first time was in 2003 using SuSE Linux and the second time was this year in April.

The Spec For Server is:
- 1 IBM E-Server 3Ghz Server
- 1GB DDR Memory
- 240GB Sata HD
- Kubuntu Linux Edgy
- [CCL]("http://ccl.sf.net") for cafe Point Of Sales system and to lock client screen

The Spec For Client
- 4 Unit Workstation
- AMD Sempron 1.6Ghz
- 256MB DDR Memory
- Floppy Drive
- CDROM
- Boot via PXE

Right now I was setup a blog and a forum for cyber cafe owner called [OSSCC]("http://www.osscc.org") stand for Open Source Sotware Cyber Cafe, it was meant to be anyone who like to share their opinion and experiences in building, setup, design, discussing in how to running a cyber cafe base on open source software and linux..

---

### Post by Nekiruhs on 2007-07-11
[This ]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Deepfreeze_for_Linux")may be the solution you need, If you've heard of an app for windows called deepfreeze, this is an easy way to do something like that for linux. Basically, what it and deepfreeze do is make an imgae of the disk and restore it on reboot. That way, if something goes wrong, just reboot.  Like a live cd only more customizable.

---

### Post by Atomic Dog on 2007-07-11
> **Nekiruhs said:**
> [This ]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Deepfreeze_for_Linux")may be the solution you need, If you've heard of an app for windows called deepfreeze, this is an easy way to do something like that for linux. Basically, what it and deepfreeze do is make an imgae of the disk and restore it on reboot. That way, if something goes wrong, just reboot.  Like a live cd only more customizable.

I have used vmware player with a non persistent image for about a year now on our client workstations.  Machine boots, then player starts and they have no idea they are using a VM on top of ubuntu.  When the machine is powered off any changes made are gone.  Can be quite handy.  Might be an option.

---

### Post by idrifter on 2008-04-21
I recently setup an Ubuntu kiosk for a coffee shop as well.  I [wrote up a tutorial]("http://caffeinefueled.com/posts/building-an-internet-kiosk-with-ubuntu") on how I went about it.  Hope someone finds it useful.

---

