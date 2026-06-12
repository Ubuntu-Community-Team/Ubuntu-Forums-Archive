---
title: "sharing folders with windows/ samba wont install"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by drmoore1 on 2008-03-31
Ok I have had ubuntu for 2 weeks now and offically nothing works. The frustration is incredible as I can not find an answer to these problems anywhere. Enough ranting here is the situation: I try to open file sharing under administration and it tells me to install samba. It begins but after 2 seconds it fails producing this error:

:\\security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.22-1ubuntu3.1_i386.deb 404 not found.

So I then tried this:

sudo apt-get update and then apt-cache search samba | more .

samba - a LanManager-like file and printer server for Unix
samba-common - Samba common files used by both the server and the client
samba-dbg - Samba debugging symbols
samba-doc - Samba documentation
samba-doc-pdf - Samba documentation (PDF format)
 
sudo apt-get install samba

which resulted in this:


account_policy_get: tdb_fetch_uint32 failed for field 1 (min password length), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 2 (password history), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 3 (user must logon to change password), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 4 (maximum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 5 (minimum password age), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 6 (lockout duration), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 7 (reset count minutes), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 8 (bad lockout attempt), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 9 (disconnect time), returning 0
account_policy_get: tdb_fetch_uint32 failed for field 10 (refuse machine password change), returning 0


What could I be missing? Thanks

---

### Post by jonkulp on 2008-03-31
Hey, afraid I don't know how to fix this problem specifically, but thought I'd suggest that if you can't manage to get samba working, you can also share files with your other computers using ftp.  In Nautilus, choose File>Connect to Server, then under "service type" choose FTP (with login) from the dropdown menu and fill in the necessary info.  I also use the SSH option sometimes.  You just have to have these types of sharing enabled on the remote computer.  

My first thought when reading your problem was that the repository wasn't up-to-date, but it looks like it ought to be after the commands you ran.  Don't know.  I got samba running fine on two different computers and don't really remember how!  Sorry I couldn't be of more help.  JK

---

### Post by rkd on 2008-03-31
Those error messages you quote come from Samba, so you already have Samba installed, but perhaps not configured correctly.

The best approach to clearing this up might be to remove Samba from your computer and start over.  Setting up Samba isn't easy, and it seems like you might not have the patience for it.  Might there be some Ubuntu or Linux expert available to you who could do the setup for you?

---

### Post by drmoore1 on 2008-04-01
I don't know of any unfortunately. A co-worker of mine has some understanding but not that much. How would I go about removing it from the computer. I am going to have to just figure it out and find some patience. I would like to know how to fix it myself anyway. Hopefully someone will have an idea how to explain how to configure samba correctly, but I will also try the other way and see what happens. Thanks for the input.

---

### Post by prosys49 on 2008-04-01
drmoore1,

I have found this article in TUX magazine helpful for setting up a home server using samba. You can still get the article (issue #19 November 2006): [http://www.tuxmagazine.com/node/1000231](http://www.tuxmagazine.com/node/1000231)

It is based on using a Kubuntu install but it may give you some pointers. I would start by uninstalling your samba installation and start from scratch.
Removing samba: System -> Adminsistration -> Synaptic Package Manager
Click on the Search button and type in **samba** and then click **search**
Scroll down to:
samba
samba-common
samba-dbg
samba-doc
samba-pdf

if these have a green square before them they are installed on your system. Click the green square. A menu should popup, choose **mark for complete removal** and then up at the top of the Synaptic window you should see a Check Mark Icon with the word APPLY under it, click on that icon to apply the changes. Then try following the instructions in the artical, remember though they are for Kubuntu not Ubuntu.

---

### Post by drmoore1 on 2008-04-01
How would I uninstall samba? I checked out that article but unfortunately I can not see it since I am not a member. I don't know if I should point it out that I only intended to just be able to access it from my the computer I am on and the virtual pc that is running ubuntu. It might not matter but I just thought I should be as detailed as much as possible incase that changes anything.

---

### Post by prosys49 on 2008-04-01
drmoore1,

Are you trying to view your Windows files from a Ubuntu installation running in a Virtual Machine in Windows? Or are you trying to view files acrosss a local area network, where one machine is Linux and the other is Windows?

If it is the later then samba should work. If it is the former, I don't know if you can use samba to map from a virtual machine to the native Windows installation files.

What Virtual machine software are you running? if you are using vmware or virtualbox, you may need to check out their forums to see how to gain access to your files on the native OS.

---

### Post by prosys49 on 2008-04-01
VirtualBox gives these instructions in their User Manual: [http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation)

**4.4. Folder sharing**
Shared Folders allow you to access files of your host system from within the guest system, much like ordinary shares on Windows networks would -- except that shared folders do not need a networking setup. Sharing is accomplished using a special service on the host and a file system driver for the guest, both of which are provided by VirtualBox.
In order to use this feature, the VirtualBox Guest Additions have to be installed. Currently, Shared Folders are limited to Windows XP, Windows 2000 and Linux 2.4 and 2.6 guests.
To share a folder with a virtual machine in VirtualBox, you must specify the path of the folder to be shared on the host and chose a "share name" that the guest can use to access it. Hence, first create the shared folder on the host; then, within the guest, connect to it.
There are several ways in which shared folders can be set up for a particular virtual machine:
In the graphical user interface of a running virtual machine, you can select "Shared folders" from the "Devices" menu, or click on the folder icon on the status bar in the bottom right corner of the virtual machine window.
If a virtual machine is not currently running, you can configure shared folders in each virtual machine's "Settings" dialog.
From the command line, you can create shared folders using the the VBoxManage command line interface; see Chapter 8, VBoxManage reference. The command is as follows:
VBoxManage sharedfolder add "VM name" -name "sharename" 
                   -hostpath "C:\test"
There are two types of shares:
VM shares which are only available to the VM for which they have been defined;
transient VM shares, which can be added and removed at runtime and do not persist after a VM has stopped; for these, add the -transient option to the above command line.
Shared folders have read/write access to the files at the host path by default. To restrict the guest to have read-only access, create a read-only shared folder. This can either be achieved using the GUI or by appending the parameter -readonly when creating the shared folder with VBoxManage.
Then, you can mount the shared folder from inside a VM the same way as you would mount an ordinary network share:
In a Windows guest, starting with VirtualBox 1.5.0, shared folders are browseable and are therefore visible in Windows Explorer. So, to attach the host's shared folder to your Windows guest, open Windows Explorer and look for it under "My Networking Places" -> "Entire Network" -> "VirtualBox Shared Folders". By right-clicking on a shared folder and selecting "Map network drive" from the menu that pops up, you can assign a drive letter to that shared folder.
Alternatively, on the Windows command line, use the following:
net use x: \\vboxsvr\sharename
While vboxsvr is a fixed name (note that vboxsrv would also work), replace "x:" with the drive letter that you want to use for the share, and sharename with the share name specified with VBoxManage.
In a Linux guest, use the following command:
mount -t vboxsf [-o OPTIONS] sharename mountpoint
Replace sharename with the share name specified with VBoxManage, and mountpoint with the path where you want the share to be mounted (e.g. /mnt/share). The usual mount rules apply, that is, create this directory first if it does not exist yet.
Beyond the standard options supplied by the mount command, the following are available:
iocharset CHARSET
to set the character set used for I/O operations (utf8 by default) and
convertcp CHARSET
to specify the character set used for the shared folder name (utf8 by default).
The generic mount options (documented in the mount manual page) apply also. Especially useful are the options uid, gid and mode, as they allow access by normal users (in read/write mode, depending on the settings) even if root has mounted the filesystem.

---

### Post by drmoore1 on 2008-04-01
> **prosys49 said:**
> drmoore1,

Are you trying to view your Windows files from a Ubuntu installation running in a Virtual Machine in Windows? Or are you trying to view files acrosss a local area network, where one machine is Linux and the other is Windows?

If it is the later then samba should work. If it is the former, I don't know if you can use samba to map from a virtual machine to the native Windows installation files.

What Virtual machine software are you running? if you are using vmware or virtualbox, you may need to check out their forums to see how to gain access to your files on the native OS.

Exactly. Yes I am running ubuntu through virtualbox in windows. I want to share folders between the two. I have tried following the instructions as posted by prosys49. I get lost after creating the file on windows. I guess I get confused on which is actually the host and which is the guest. I am also not sure on how to create directories/create folders or mount the folder either.

So far I have created the file on windows and added the folder by clicking on the shared folder on the status bar.

---

### Post by rkd on 2008-04-01
In your case, Windows is the host and Ubuntu is the guest.

---

### Post by rkd on 2008-04-01
Which way did you want to share files?  Did you want to be able to access Windows files from within the Ubuntu system or did you want to be able to access Ubuntu files from the Windows system?

I don't know anything about VirtualBox, but it appears to me that the mechanism described in the document prosys49 posted only provides a way to access host files from within the guest, in your case Windows files from within Ubuntu.  If that is what you want to do, great -- I'm sure we can help you get it to work.  But if you wanted to do the sharing the other way, I'm pretty sure that document won't show you how to do that.

If you want to access the Ubuntu files from Windows, It may be possible to do that by running Samba in Ubuntu.  I believe I have read that VirtualBox instances can be made to appear to the host system just as if they were real systems on the LAN, so I imagine that if you had a proper Samba configuration set up in the virtual machine Ubuntu, you'd probably be able to access files in the Ubuntu system using the usual Windows file sharing.  I've not done any of that, so I can't say it works, but it seems it would.

I hope you want only to access the Windows files from Ubuntu, because that should be much easier to set up.  If you have questions about the instructions prosys49 posted, I'm sure we can help you figure out what to do.

If you want to access the Ubuntu files from Windows, that will be harder to get working unless there is a simpler way than using Samba.

---

### Post by drmoore1 on 2008-04-02
I only want to see the windows file from ubuntu so I guess we are not to bad off then.

---

### Post by prosys49 on 2008-04-02
> **drmoore1 said:**
>  I have tried following the instructions as posted by prosys49. I get lost after creating the file on windows.

Sorry, I have not tried to do this personally. I am running XP in VirtualBox on my Ubuntu but I have not tried to share files between them. I hope you can use the VirtualBox User Manual as a guide for that part.

> **drmoore1 said:**
> I guess I get confused on which is actually the host and which is the guest.

The Host is the Machine you boot the Computer on. The Guest is the Operating System running in VirtualBox.

> **drmoore1 said:**
> I am also not sure on how to create directories/create folders or mount the folder either.

To create a directory in Linux Open a Terminal or a Console command prompt window. In Ubuntu:
Applications -> Accessories -> Terminal

Then type in the mkdir command with your path and the name of the folder to create. For example if I wanted to create a folder called DocsXP in my Home folder I would type the following in a Terminal window:

hodges@hodges-desktop:~$ sudo mkdir /home/hodges/DocsXP

You would actually only type what is after the $ sign. The information before is the user @ computer name.

I hope this gets you a little further. If I get a chance to try the file sharing between a Virtual machine and the Host OS I will try to post what I find out.

---

### Post by drmoore1 on 2008-04-02
Ok thank you.

---

