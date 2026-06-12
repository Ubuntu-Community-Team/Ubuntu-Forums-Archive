---
title: "I don't  see ANY other computers in my network"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by bobsebay8 on 2008-01-30
I have a LAN of 2 notebooks, 2 desktops (all runnings Windows) and 1 new desktop running v. 7.10. I CAN connect to the internet with NO problem. I CANNOT however see ANY of the other 4 'puters running simultaneously on my LAN. I HAVE installed the Samba files, but still no help. Can anyone point me to where I can troubleshoot this, or do you have an idea on fixing it that you could impart to me? Thanks, Bob
:guitar:

---

### Post by anaconda on 2008-01-30
have you some shared folders on your windows machines?
Does the windows firewall restrict access to those folders?

can you mount them manually?
sudo mount -t smbfs -o username=guest,password="" //ip_address/shared_foldername_in_XP  /mnt 

This would mount the shared folder to /mnt folder..

---

### Post by mikeyphi on 2008-01-30
> **bobsebay8 said:**
> I have a LAN of 2 notebooks, 2 desktops (all runnings Windows) and 1 new desktop running v. 7.10. I CAN connect to the internet with NO problem. I CANNOT however see ANY of the other 4 'puters running simultaneously on my LAN. I HAVE installed the Samba files, but still no help. Can anyone point me to where I can troubleshoot this, or do you have an idea on fixing it that you could impart to me? Thanks, Bob
:guitar:

After installing Samba - did you open System/Administration/Shared Folders and enter the domain name under the 'general' tab - also tick 'this computer is a wins server'?

---

### Post by bobsebay8 on 2008-01-30
Thanks for the quick reply! YEs to shared forlders on Windows machines, NO to firewall question,  mounting maually did not work...also, none of my external hard drives will show up on the Ubuntu box either. 3 of them, different brands, tried connecting them thru the network and even tried directly connecting thru the USB port on the Ubuntu box. Doesn't see them. 

When I go to NETWORK, I see my network name, I double click on it, error reply is this: The Folder Contents Could Not be Displayed      Sorry, could not dislplay all the contents of the Windows Network

---

### Post by bobsebay8 on 2008-01-30
NO, so I went back in, typed in the name , clicked the box. But still get the error message. Thanks though, any other ideas?

---

### Post by mikeyphi on 2008-01-30
> **bobsebay8 said:**
> NO, so I went back in, typed in the name , clicked the box. But still get the error message. Thanks though, any other ideas?

In that case - also under System/Administration/Shared Folders
highlight your shared folder (usually home/user)  select properties and check that the 'share through' box is set to Windows network (SMB)

edit: Also check that the domain name is entered under the General tab of System/Administration/Network

---

### Post by skydaver on 2008-02-01
I'm having the same problem as bobsebay8, since I upgraded to Gutsy Gibbon the other night.  

I'm pretty sure that I've followed all the suggestions in this thread.  My answers to Anaconda's questions would be yes, no, no

I don't remember this being such a problem on 7.04, but I could be having a senior moment.

I'm slightly perturbed that the upgrade knocked out my connection to my Windows machines, but I'll get over it.

I don't need this Linux machine to be accessible to the windows machines, just the other way.

When I go to Places->Network, the browser lists 'Windows Network', but when I open that, there is nothing.  I know, however, that there are two other computers up and running on that workgroup 

TIA!

 There is also a computer on another domain on this network.  I don't need to access that computer, but I used to see the domain listed under the Network Places.  Now I don't.

---

### Post by skydaver on 2008-02-01
I've also read through [MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently"), and I don't think that's really what I need.  I just want to be able to access the printer hanging off my Windows machine, and read and write to the shared directories on those machines.

---

### Post by dcstar on 2008-02-02
> **bobsebay8 said:**
> I have a LAN of 2 notebooks, 2 desktops (all runnings Windows) and 1 new desktop running v. 7.10. I CAN connect to the internet with NO problem. I CANNOT however see ANY of the other 4 'puters running simultaneously on my LAN. I HAVE installed the Samba files, but still no help. Can anyone point me to where I can troubleshoot this, or do you have an idea on fixing it that you could impart to me? Thanks, Bob
:guitar:

Can you ping those other machines?

---

### Post by skydaver on 2008-02-02
I know you were responding to Bob, but in my case, the answer is yes.  I'm able to ping the Windows machines from the Ubuntu machine, and the Ubuntu machine from the Windows machine

---

### Post by jose158 on 2008-02-02
Try going [here.]("http://www.youtube.com/watch?v=Ad17kma8rNM")

---

### Post by skydaver on 2008-02-02
I'm running 7.10, not 6.10.  I used to have this working, but it stopped after I did the upgrade from 7.04 to 7.10.  I may have to just go and reload, but that is not a step I'd really like to take.  It's also more a Windoze solution than a Linux one.

I did view the video, and do what was suggested, but still no visible computers on the network.

---

### Post by skydaver on 2008-02-05
My solution was to just re-install 7.04, Feisty Fawn.  After I did that, views of my Windows machine just worked, with no problem, with no settings to tweak.

I don't know if this is a problem with 7.10, or with the upgrade process.  I'm not yet willing to do a full install of 7.10 to find out.

---

### Post by skydaver on 2008-02-06
I had been trying to get Stellarium to compile under 7.04, but it needs Qt 4.3.3 which comes with 7.10.  Last night I upgraded to 7.10 again, and this time, the access to the Windows shared folders and printer just worked.  Go figure.

---

