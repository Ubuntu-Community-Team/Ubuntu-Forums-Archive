---
title: "How to connect to network drive (airport extreme disk)"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by vatechtigger on 2007-04-09
anyone know which option under connect to server is the right one to choose for this task. On windowz I would just add network connection, enter the ip and was all set (it would ask for the drive password)

I tried just entering the ip on pretty much all the options under connect to server, but got varying errors with all of them.

Thanks

---

### Post by victorbrca on 2007-04-09
What fields did you fill and what did you put in the fields?

  I take this is a Windows share. Can you access the share by going to Places => network servers?

  Do you know if SMB is installed?


Cheers,


Vic.

---

### Post by vatechtigger on 2007-04-09
under windows it is a CIFS connection. 

if you go to map network drive, enter //68.193.xxx.xx and it mapped.

Under OSX, well it just shows up :)

---

### Post by victorbrca on 2007-04-10
But how about on your Ubuntu? What are the configurations that you are using?


Vic.

---

### Post by vatechtigger on 2007-04-10
thats the problem, I cant see it at all in ubuntu. If I go to network, then windows network, it doesn't appear. If I do connect to server, and try to enter the IP address. I didn't fill any fields (marked optional under ubuntu) because I don't know which ones to use, if any?

---

### Post by victorbrca on 2007-04-10
Do you know if samba is installed on you Ubuntu?

Go to System => Administration => Shared Folders. It should ask you to install in case you don't already have.

If that's the case, try searching for the share again on Places => Network Servers after installing samba.

Hope this helps...



Vic

---

### Post by vatechtigger on 2007-04-11
hello,

I did what you suggested, and enabled samba and folder share. Still no luck seeing the drive though. 

Is there an analog in Ubuntu to mapping a drive in windows. IE, which option to choose to just enter the IP and password and be good to go?

Thanks

---

### Post by victorbrca on 2007-04-11
Myself, I use [**_this how to**_]("http://ubuntuforums.org/showthread.php?t=288534&highlight=mount+samba"). However you should be able to access the share from Network Servers.

  Connect to Server is also an option.



Vic.

---

### Post by vatechtigger on 2007-04-11
ooh, that looks like it will hit the spot. Ill give it a try when I get home. Thanks

I did try the connect to server options, but none of them would work for me. Who knows........

---

### Post by PureLegend on 2007-07-03
Hello, sorry to revive this topic, but I was wondering if the AirPort Disk feature would work under Ubuntu? I'm thinking about getting one and using Ukop to backup to it.

It's under NTFS, but I got Ubuntu to play nice with NTFS.

So, good idea? Bad idea?

---

### Post by munchy on 2008-01-19
In Airport utility, ensure that you allow access to the Airport disk 'with base station password' and set guest access to 'Read' or 'Read and write'. Then, assuming you have Samba installed in Ubuntu, go to the address smb://"base station name or IP address"/"disk name" in Nautilus.

This method obviously allows read or read/write access to the disk for everyone on the network and proves that airport disk is at least accessible from Ubuntu. I've not been able to connect to the disk when it's set up for access with user accounts though, if anyone has figured this out, please reply! Do Apple deliberately make things difficult for us Linux users?! :)

Edit: Well this seemed to work, but copying files to the airport disk crashes Nautilus! :(

---

### Post by drvid on 2008-02-06
Yes, I've confirmed that connecting to the Airport disk as guest in Nautilus will allow reading, but writing will crash Nautilus (also crashed my AEBS the first time)

Also, connecting via cifs in /etc/fstab as guest will keep giving you 'permission denied' errors, even if you have working guest access from within Finder.

The solution is to use an account name instead of just guest via cifs in your /etc/fstab ... Then you can write to the shared disk from Ubuntu.

To do this...

1) In Airport Utility under 'Disks' enable file sharing 'with accounts' then make up some username/pw for Linux to use with cifs. Give that account r+w permissions. Update/restart base station.

2) Add the mount point in /etc/fstab via cifs and credentials as outlined earlier in this thread, then mount it.

Continue to allow read+write access for guests in Finder, if desired. What's still annoying though, is that it will now mount at a 'Shared' subfolder on your drive... so don't panic, your files are still there, just in the parent directory which is now hidden...

You can plug the USB drive back into a computer and move any old files and folders into that Shared subdirectory if you need to access them from Linux... Or just change the sharing permission schemes back the way they were, after you're done copying files.

BTW: PureLegend... I don't think Airport will allow you write access to an NTFS drive, I believe it will only share HFS or FAT formats.

After this backup I'm doing I will be disabling all samba on our network. We are all Mac + Linux and samba is a hassle with separate logins and unencrypted passwords anyway :)

---

