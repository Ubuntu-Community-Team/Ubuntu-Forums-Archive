---
title: "Tired of feeling stupid"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by tgrantt on 2007-08-21
Hi.  I am looking for help (What else?) with networking. I recently became a Linux noob.  I tried to install Ubuntu, but the install kept stalling.  Someone here suggested that I needed more than 256 M of RAM, so I installed Xubuntu.  I liked it, except for the lack of peer-to-peer network support.  I installed SAMBA, and followed an excellent tutorial here, and got my Windoze box to see my Linux one, but not vice versa.  However, as seems to be a problem, the Xubuntu computer kept losing the share.  

So I bought more memory, installed Ubunutu, and can't get it to see the Windows computer.  I was told that going to places>network would show it, but under windows networking the only network is MSHOME, which is not the name of my network.  I was finally able to change the network name under Ubuntu, but I cannot make it work.  I've read hours of instructions from here and elsewhere, but no go.

I'm not always a complete idiot, and I've used computers a long time, holding out with DOS until Windows 3.11 and after. (Remember HDM IV, the hard disk menu?)  If the Synaptic Package manager can work so well, why can't a GUI based network setup?

---

### Post by wirelessmonkey on 2007-08-21
I do remember HDM IV, wow!   
There is  a wealth of difference between an application that scans a remote database and downloads apps (synaptic) and one that evaluates hardware IDs, identifies firmware, installs drivers and creates a configuration for a specific external authentication mechanism in  an easy to understand way, THEN uses an outside application to create a share on a network with arbitrary configuration, AND try to synchronize itself with another device trying to do the same thing in an entirely different fashion (the nebulous network gui).  

Now, to be more helpful:
MSHOME is the name of your Windows Workgro  up, which should be specified on the WORKGROUP line of smb.conf  
If you just want to open a share from Ubuntu to Windows, here are 2 methods.

1)From a terminal
sudo mkdir /media/windows
sudo mount -t smbfs -o username=windowsusername,password=windowspassword //IPaddressofwinmachine/sharename /media/windows

2) I use Kubuntu, so this may be slightly different namewise.
From the 'places' menu on the taskbar, select "Remote Places", select "Add a Network Folder" 
Select "Microsoft Windows network drive" from the list of choices.  Give the connection a name, input the IP or network name of the windows machine in the Server field. Input the shared folder/device name in the Folder field (i.e. C$, D, or SharedFolder)
Enter Username and Password for the device you're connecting to.
This should be the last step.

If your Windows machine doesn't resolve properly, you should use the IP address of that machine instead, as I did in the above example.  

If you see an issue after trying the above, post again with as much detail as you can, and we'll get this figured out!

---

