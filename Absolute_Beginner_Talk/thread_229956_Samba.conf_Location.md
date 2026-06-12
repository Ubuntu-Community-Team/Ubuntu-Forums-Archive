---
title: "Samba.conf Location"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Geffers on 2006-08-05
I'm having a problem getting Samba configured on my Breezy Badger 
system ](*,) 

I cannot get swat to work, keep getting access denied, so am using webmin.

I seem to have a samba.conf file in two different locations as follows;
1. /etc/samba/samba.conf
2. /usr/share/samba/samba.conf

On my XP laptop I can ping my Ubuntu machine and the Ubuntu can ping the laptop so the connection is there but I cannot see the ubuntu shares on my XP machine.

Can someone confirm the correct location of the samba.conf file for me please.

Geffers

---

### Post by stig on 2006-08-05
> **Geffers said:**
> I'm having a problem getting Samba configured on my Breezy Badger 
system ](*,) 

I cannot get swat to work, keep getting access denied, so am using webmin.

I seem to have a samba.conf file in two different locations as follows;
1. /etc/samba/samba.conf
2. /usr/share/samba/samba.conf

On my XP laptop I can ping my Ubuntu machine and the Ubuntu can ping the laptop so the connection is there but I cannot see the ubuntu shares on my XP machine.

Can someone confirm the correct location of the samba.conf file for me please.

Geffers

I've got smb.conf files at both locations but to my knowledge it's only the /etc/samba/samba.conf file where you do the editing.

For more recent stuff on Samba, see Stormbringer's Howto:
[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=network+windows](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=network+windows)

Good luck!

---

### Post by Geffers on 2006-08-06
> **stig said:**
> I've got smb.conf files at both locations but to my knowledge it's only the /etc/samba/samba.conf file where you do the editing.

For more recent stuff on Samba, see Stormbringer's Howto:
[http://www.ubuntuforums.org/showthread.php?t=202605&highlight=network+windows](http://www.ubuntuforums.org/showthread.php?t=202605&highlight=network+windows)

Good luck!

Thanks, very interesting and I think my problem is with users, I was under the impression that as I had allowed 'guest' that I didn't need to create samba users for each potential visitor.

I've got a handheld computer that can browse windows networks but the the best of my knowledge has no specific user so I wonder how that would join a samba network.

Geffers

---

### Post by stig on 2006-08-06
> **Geffers said:**
> Thanks, very interesting and I think my problem is with users, I was under the impression that as I had allowed 'guest' that I didn't need to create samba users for each potential visitor.

I've got a handheld computer that can browse windows networks but the the best of my knowledge has no specific user so I wonder how that would join a samba network.

Geffers

Sorry, I don't know enough to help you, so I hope someone with more experience can solve your problem (I presume you have smbfs installed as well as samba).

In the meantime, here are some Samba guides that I found in addition to the Stormbringer one:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)
[http://www.samba.netfirms.com/index.htm](http://www.samba.netfirms.com/index.htm)
[http://us4.samba.org/samba/docs/using_samba/toc.html](http://us4.samba.org/samba/docs/using_samba/toc.html)
[http://www.tldp.org/HOWTO/SMB-HOWTO.html](http://www.tldp.org/HOWTO/SMB-HOWTO.html)

---

### Post by djsroknrol on 2006-08-06
Check System>administration>Shared Folders to see if they are shared...

---

### Post by Geffers on 2006-08-07
> **stig said:**
> Sorry, I don't know enough to help you, so I hope someone with more experience can solve your problem (I presume you have smbfs installed as well as samba).



No, I haven'y got smbfs installed, I know it stands for samba filesystem but what does it do, the samba page suggested that no-one used it so it wasn't maintained until recently.

Geffers

---

### Post by Geffers on 2006-08-07
> **djsroknrol said:**
> Check System>administration>Shared Folders to see if they are shared...

Yes, they show up ok.

Geffers

---

### Post by stig on 2006-08-08
> **Geffers said:**
> No, I haven'y got smbfs installed, I know it stands for samba filesystem but what does it do, the samba page suggested that no-one used it so it wasn't maintained until recently.

Geffers

Quoting from Stormbringer's thread (link given in earlier post in this thread):
"If you ONLY want to access a Windows-Share FROM your Ubuntu box you don't need samba at all, you only need "smbfs" installed in order to mount the share. You ONLY need samba if you like to access a share on your Ubuntu box FROM Windows."

So it sounds like you need smbfs to mount your shares. It isn't in the default Ubuntu and needs installing via Synaptic.

---

### Post by Geffers on 2006-08-10
> **stig said:**
> Sorry, I don't know enough to help you, so I hope someone with more experience can solve your problem (I presume you have smbfs installed as well as samba).



I installed smbfs but cannot see how it is run.

Tried the command line but it states smbfs does not exist.

A file search shows a folder named smbfs, a file within it named smbfs.ko and smbfs.gif

I don't appear to have any menu entry for it either :confused: 

Geffers

---

### Post by The Mekon on 2006-08-10
I think that smbfs is a service that should be initiated at Start Up.

Check System/Administration/Services and look for Folder Sharing Service (Samba).  If it there tick its box to enable it.

Brian

---

### Post by stig on 2006-08-11
Geffers, If you are still having problems I suggest again that you look at Stormbringer's HOWTO:

[http://www.ubuntuforums.org/showthre...etwork+windows](http://www.ubuntuforums.org/showthre...etwork+windows)

Look through his instructions on the first page and give them a try. If you need help, go to the end of the thread and put in a reply stating your own problem and asking for help.

He has been very helpful to a lot of people in that thread and solved many problems concerning Samba.

---

### Post by Geffers on 2006-08-12
> **The Mekon said:**
> I think that smbfs is a service that should be initiated at Start Up.

Check System/Administration/Services and look for Folder Sharing Service (Samba).  If it there tick its box to enable it.

Brian

Checked System, Admin, Services - also checked the sudo systemsettings and running services via webmin, no joy.

No man page that I could find either.

I'm slowly losing myself ](*,) with this samba.conf file being in two locations coupled with the locked ubuntu root user and not being able to get SWAT to work.

I know ubuntu's locking of the root user is a safety feature but I do not recall having any problem using a root desktop for configuration when I previously used mandrake.

I'll keep at it though :???: 

Geffers

---

### Post by Geffers on 2006-08-12
> **stig said:**
> Geffers, If you are still having problems I suggest again that you look at Stormbringer's HOWTO:

[http://www.ubuntuforums.org/showthre...etwork+windows](http://www.ubuntuforums.org/showthre...etwork+windows)

Look through his instructions on the first page and give them a try. If you need help, go to the end of the thread and put in a reply stating your own problem and asking for help.

He has been very helpful to a lot of people in that thread and solved many problems concerning Samba.

Yes, I will do.

When you first pointed me it that direction I found the file very informative and immediately thought that USERS were my problem.

Enthusiastically addressed that problem but still no joy :roll: 

Never mind, I'll keep at it.

Geffers

---

