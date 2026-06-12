---
title: "File sharing using Samba"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by tartarian on 2007-07-07
I've followed this absolutley fantastic thread [here]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba") on setting up file sharing with samba
I've now got my network drive mapped on my windows machine but I can't delete files or add files to the drive from my windows box. How do I change that?
And also, I want to be able to read from my windows hard-drive on my Ubuntu box but I've no idea how to do this. Any ideas?
And I know i've explained that really badly, but hopefully someone will understand what I mean :P
Thanks guys!

---

### Post by Speedoo on 2007-07-07
You need to mount your Windows drive in Ubuntu.  I've found that the easiest way to do this is to install "automatix 2".  It gives you a bunch of multimedia stuff, but more importantly it includes a program that will automatically mount your NTFS drives and make them writeable.  Since installing automatix 2, when I boot to Ubuntu, my Windows drive appears on the desktop, and I can access it, and add and remove files from it.
It sounds like your linux drive, as viewed from Windows, needs to have the permissions updated.  I know the terminal command is "chmod", but I don't know the exact command you would use to make your Ubuntu drive writeable from Windows.
Hope this helps.  (Tips from another beginner!)

---

### Post by tartarian on 2007-07-07
I appreciate your help :P And everyone has to start somwhere (as I'm finding out)
My question is, i presume that you're reading files off an internal hard drive? I need to read files off a harddrive on a networked computer??? Do you think that would still work?

---

### Post by AndyCooll on 2007-07-07
Yes, you should be able to see shares that are on a Windows box from a Linux box. From your comments I'm assuming that you have Samba setup

1. On your Windows box enable the relevent folder to be shared on the network.
2. On your Linux box  go to Places > Connect To Server, and navigate to the relevent shared folder.

There are a couple of comprehensive guides here:
[Setting Up Samba]("https://help.ubuntu.com/community/SettingUpSamba")
[Comprehensive Samba guide]("https://help.ubuntu.com/community/ComprehensiveSambaGuide")

:cool:

---

### Post by tartarian on 2007-07-07
Thankyou :)
I've had a look at the guides you linked and they seem fantastic, but I can't seem to get past the first stage of the comprehensive one. 
When I type net localgroup UbuntuSMB /add into the command line I get a "System error 5 has occured, Access is denied"
Now I know you're not windows people :P but do you have any idea what I could do bout that?
Aparently, according to microsoft (yay!) it either a :
    1. Time Synchronization problem.
 
    2. Missing permission to access the remote computer (Share, NTFS, GPO).
 
    3. Firewall and/or third party product may eliminate connection to the remote computer.
 
    4. The computer account isn't disable (Or have expired computer account password)
 
             or doesn’t exiting in the domain.
 
    5. Active Directory replication problem may occur.

I'm guessing its missing permission to access the remote computer. But I may be wrong. Any ideas what to do? Thankyou!!!

---

