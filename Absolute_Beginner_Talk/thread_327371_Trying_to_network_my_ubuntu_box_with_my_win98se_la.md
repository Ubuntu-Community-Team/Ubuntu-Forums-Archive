---
title: "Trying to network my ubuntu box with my win98se laptop"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by beanni on 2006-12-29
Hi all, well I have decided to make the move across to Linux and I am really loving the look and fell of Ubuntu Dapper.  I have been playing around with some of the apps but I am really just beginning.

My current setup:

My main machine (TOWER) is running a dual boot of win XP SP2 and Ubuntu Dapper Drake (desktop install).  It connects directly to the internet and also has the printer connected to it.  It is also networked to my second computer (LAPTOP) running win98SE which goes through TOWER to connect to the internet and to print from.

My Problem:

While running TOWER in XP I have no problems with the network.  LAPTOP can easily print and access the internet and they can both access any files that I choose to share.

When TOWER is running in DAPPER it does not recognize LAPTOP and LAPTOP is unable to access the internet or printing through TOWER.

When I click on Places>Network Servers
and select Windows Network I sometimes have mshome (don't ask me why it only appears sometimes)  Here I find TOWER but no LAPTOP.

My Question:
Can somebody please help me?  I have read many of the forums and documentation relating to networking in these environments and using SAMBA and even though I have tried to follow some of the guides I have no result.

Could somebody please tell me where I may be going wrong and or give me a Noobie idiots guide to my problem.  I am a complete begineer to Linux and not overly versed in computers, so please be gentle.

---

### Post by houstonbofh on 2006-12-29
I found several was with a quick search, but this one seemd like the best quick fix for you.  Once you have time to look more you might want to do something else...
[http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370)

---

### Post by beanni on 2006-12-29
Thanks houstonbofh, well that gets the internet up and running on both machines which is great but after rebooting neither machine is able to access the internet.  After going through the steps of that "how to" you suggested I am up and running on both machines again.  This is a bit of a pain but I notice that others in that thread are having the same problem so I will chase it up further.

I still have a problem in that I don't have any file or print sharing for either machine as I did with the winXP - win98SE setup.  From both machines I am able to ping the others ip address without any errors, but other than that I am completly lost. HELP PLEASE!!!!!

---

### Post by beanni on 2006-12-29
AN UPDATE

and there it was ..... I can now access LAPTOP from Tower through Places>Network Servers, and I can also see TOWER from the Mshome directory in Windows Network Neighbourhood.  I didn't do anything new, they both just suddenly appeared.

The only problem I have now is that when I try to access TOWER from my LAPTOP it is asking for a password.  I have tried  "How to add/edit/delete network users" from [http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service) but no luck.

When I try to click on TOWER in MShome in Netowrk Neighbourhood on LAPTOP, it shows:  Resource: \\LINUX-TOWER\IPC$ and it asks for the password.  When I enter the password that i setup in "How to add/edit/delete network users" it says I am "The PAssword Is Incorrect. Try Again".  Am I trying to open the right Linux directory?  What is IPC$?  I have tried to map some other network drives but they all ask for passwords too.

I am so close yet so far PLEASE HELP!

---

### Post by houstonbofh on 2006-12-30
I wish I could, but I have a had time getting Windows file and print sharing working on Windows boxes.  (Assuming you run a firewall, which I do)  I use FTP mounts, and LPR printing. (Both fully supported on both systems) To share a Linux printer you have to enable printer sharing on the CUPS system.  I recommend a new thread. ;)

---

### Post by beanni on 2006-12-31
Ok here is what I have done.  I followed this great guide [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) and had success.  I had done this before but i thought I would try it from the beginning and lo and behold it worked (in the past I had tried it and failed every time).  The next day I logged into both computers and tried again but no success.  For some reason for me to connect to the internet on LAPTOP via TOWER I have to have Firestarter running on TOWER.  It seems that Firestarter is creating the problem.  If i have Firestarter running I can access the internet on LAPTOP but I cannot access shared docs on the ubuntu machine (TOWER) from LAPTOP.  The work around at the moment is that once logging on to the win98SE machine (LAPTOP) I must immediatly attempt to access the ubuntu machine (TOWER) then i can open Firestarter and also access the internet on LAPTOP.  From here everything works ok.

I am sure that there are some settings that I need to adjust to get this all working properly without all this fiddling, but for the moment I am just happy that I can do this.  If anyone could point me in the right direction that would be great.  Otherwise I will just kepp searching.

Love Ubuntu by the way ... KEEP UP THE GOOD WORK!

---

