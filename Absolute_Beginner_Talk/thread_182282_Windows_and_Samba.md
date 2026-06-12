---
title: "Windows and Samba"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-05-25
Why won't my windows machine log on to my Linux Server?  I can log on with my linux machines by using SSH, but when I try to log onto my linux box with my windows machine it won't let me.  I have tried PuTTY and VNC and niether of them work.  I am missing something?  Some please give me some advice.

---

### Post by nalmeth on 2006-05-25
You might have to edit the /etc/smb.conf file, sometimes the default configuration is not great.

Do you get prompted for a password (which doesn't work) or can you simply not see the shares?

BTW you have to add folder's to share. YOu can do it by right-clicking the folder you want in nautilus and choose Share Folder.

You have installed samba correct? I don't think it's included 
sudo apt-get install samba

---

### Post by NeoGreen on 2006-05-25
I have tried both PuTTY and VNC, for PuTTY, Ill bring up the part where you input the address of the sever and then I get some sort of command prompt screen but with no prompt.  On VNC I do the same thing but it just time out.  I don't get to see anything from the server.  You said I might have to configure the etc/smb.conf file, is that the one on my server.  If so how do I go by configuring it?:(

---

### Post by nalmeth on 2006-05-25
I'm confused, your thread was about samba, but you're using other protocol's.
I think you first have to setup MSHOME from windows (Network Places maybe?)

Then in ubuntu:
sudo apt-get install samba

Browse around in nautilus, and right-click the folder you want to share with Samba. Select Share Folder. A dialogue will pop-up, and you have to select "Share with Windows Server", and you should be able to set some options.

You should then be able to browse that Ubuntu Shared folder from Network Places.

---

### Post by NeoGreen on 2006-05-25
Sorry for confusing you, I did not explain myself well.  This is my situation, I am working on installing a server for my home network.  This server will consist of a filesever, webserver, database and any other thing I can think of.  Well in my home network I have three XP machines and three linux machines and wha I am trying to do is to check and make sure all my machines regardless of make can communicate with my server.  I installed and configure Samba on my server and well for some reason when I try to use PuTTY or VNC to get into my server remotely it won't let me.  This probably doesn't have anything to do with Samba, I was sort of confused earlier about the meaning of Samba.  Well, that is my problem, I cannot connect remotely to my server from a windows machine.  No VNC and no PuTTY can help me connect.](*,)

---

### Post by NeoGreen on 2006-05-25
Ah, I figured it out!!!!!  My Norton Security Center was keeping me from using PuTTY or VNC!!!!  For some reason it dawned on me that maybe my securities program may be causing the problem.  I went in and disabled it and to my surprise I was able to use PuTTY and log on to my linux box.  Know I have to figure out how to disable it permanently on the port it is blocking me out of. :)  Also, thanks for the info, oh and those links on your sig are great, they have alot of good info.  Thanks.:)

---

### Post by nalmeth on 2006-05-25
ha! great news

All along it was Norton. Oh well. You got it now. Sound's like a sweet setup 8)

---

