---
title: "Virtual Box Shared Folders"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by bob-aptllc on 2007-02-27
I set up a VirtualBox shared folder with no errors given in Edgy's terminal or when I ran the command in the guest (W2K). The commands I entered were:

...~$ sudo VBoxManage sharedfolder add "Windows 2000" -name "aptshare" -hostpath "/home/.../aptshare"

net use t: \\vboxsvr\aptshare

The syntax appears correct when I compare to the VB manual and what others have entered in this and other forums. However, when I click on W2K's Entire Network/VirtualBox Shared Folders, I receive the Windows error message: "Unable to browse the network. The network request is not supported." :(  Any ideas of how to fix this? Thanks!

---

### Post by zdude on 2007-02-28
I don't think you need to use "sudo" since it should be updating the files in your home directory.

---

### Post by rocketboyjro on 2007-03-18
I am getting this same error on XP :confused:

---

### Post by bob-aptllc on 2007-03-20
Hi rocketboyjro,

I made 2 mistakes resulting in the above error. The first was that I was entering the guest's command in "run" rather than at the dos prompt. The second, and more likely the source of the error message, is that the shared folder will appear in My Computer along with the C: and other drives, not in Windows' Entire Network. Try looking for it under My Computer. I hope this helps. :)

---

### Post by xlnt01 on 2007-03-20
I got the same problem.
I can't find my shared folders in my winxp guest.
And I dont find then under my computer either...
Seems like the winxp guest can find the vboxsrv host at all. Any other good ideas?

---

### Post by bob-aptllc on 2007-03-21
xlnt01, what commands did you enter into your host and guest?

---

### Post by .simon on 2007-03-22
[QUOTE=bob-aptllc;2220396]I set up a VirtualBox shared folder with no errors given in Edgy's terminal or when I ran the command in the guest (W2K). The commands I entered were:

...~$ sudo VBoxManage sharedfolder add "Windows 2000" -name "aptshare" -hostpath "/home/.../aptshare"

net use t: \\vboxsvr\aptshare



Hi there,

I also tried this, I'm running Edgy 6.10 with xp pro in virtual box. The terminal command in Edgy worked ok, no error message and the new folder appeared in my home folder.

When I tried to run the net use command in a dos box in xp it's not working

I seem to be incapable of setting up USB support for my virtual xp pro too, I've spent several days messing with it now lol... starting to feel stupid!

Help!!

Thanks

Simon

---

### Post by bob-aptllc on 2007-03-26
Here is a good workaround for VirtualBox not recognizing USB drives and peripherals:  [http://www.virtualbox.org/discussion/1/449#-1](http://www.virtualbox.org/discussion/1/449#-1). This approach is to not use VirtualBox's filters to mount the USB in the guest, but to use SMB (Samba) in Linux to communicate the already mounted USB device to the (Windows) guest. I was very surprised at how easy it is to set up Samba in Ubuntu! Just right-click to share the folder and not much more. Please see the link for more. :)

---

### Post by neyfrota on 2007-10-28
- install samba
- tweak samba to do-not-ask password on windows share. edit /etc/samba/smb.conf, search and change  security to share, like this "security=share"
- share some folders (system, administration, shared folders)
- stop/start samba (system, administration, services)
- go to your virtual windows, start, run and type \\10.0.2.2   
bingo!

ps: 10.0.2.2 its the default gateway on my virtual windows... just your!!

---

### Post by toastermm on 2008-05-21
I too am having the same problem, here is what I enter:

VBoxManage sharedfolder add "Windows" -name "VirtualFiles" -hostpath "C:/home/nick/test"

Here is the result:

VirtualBox Command Line Management Interface Version 1.5.6_OSE
(C) 2005-2008 innotek GmbH
All rights reserved.

[!] FAILED calling machine->CreateSharedFolder(Bstr(name), Bstr(hostpath), fWritable) at line 6236!
[!] Primary RC  = 0x80070057
[!] Full error info present: true , basic error info present: true 
[!] Result Code = 0x80070057
[!] Text        = Shared folder path 'C:/home/nick/test' is not absolute
[!] Component   = SharedFolder, Interface: ISharedFolder, {8b0c5f70-9139-4f97-a421-64d5e9c335d5}
[!] Callee      = IMachine, {31f7169f-14da-4c55-8cb6-a3665186e35e}


Any ideas?

---

