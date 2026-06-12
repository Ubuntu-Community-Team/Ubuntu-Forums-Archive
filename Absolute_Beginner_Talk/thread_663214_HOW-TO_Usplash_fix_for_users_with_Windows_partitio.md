---
title: "HOW-TO: Usplash fix for users with Windows partition."
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by ubuntu-freak on 2008-01-09
Do you have a windows partition mounted? I realised when I enabled text mode that it was the filesystem check making usplash hang and timeout.
 
Enter this command in the terminal
 
**sudo gedit /etc/fstab**
 
Now go to the end of the line of your windows partition (usually sda1) and change the **1** to a **0** and then close and save.
 
This will stop it being checked at boot and stop usplash hanging and timing out. Now and then you should check it with windows though incase there are errors. 
 
If you have weird behaviour by usplash on shutdown, suspend, reboot etc it is probably video card related.
 
Easy solution for me was to install this application 
 
**sudo apt-get install startupmanager**
 
Go to system>administration and launch it. Then change bitdepth to 16bit or just experiment until shutdown usplash works properly. Personally I use 1024x768 and 16bit colour.
 
Hope that works as well for you as it did for me.
 
Nathan

---

### Post by ubuntu-freak on 2008-01-10
My streaming how-to is here 
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
I have almost perfect streaming of all formats.
 
Nathan

---

### Post by TWO on 2008-01-13
> **reassuringlyoffensive said:**
> 
If you have weird behaviour by usplash on shutdown, suspend, reboot etc it is probably video card related.
 
Easy solution for me was to install this application 
 
**sudo apt-get install startupmanager**
 
Go to system>administration and launch it. Then change bitdepth to 16bit or just experiment until shutdown usplash works properly. Personally I use 1024x768 and 16bit colour.
 
Hope that works as well for you as it did for me.
 
Nathan

Do you know why since updating to 7.10, the assigned sound no longer plays during logout?

---

### Post by ubuntu-freak on 2008-01-13
It's because shudown is faster now and it cuts out the last part of the sound. They are going to make a new sound which is really short. 
 
Nathan

---

### Post by TWO on 2008-01-20
> **reassuringlyoffensive said:**
> It's because shudown is faster now and it cuts out the last part of the sound. They are going to make a new sound which is really short. 
 
Nathan

Ah right, thanks for the info.

Can I ask where you find things out from?

---

### Post by Fleece Flamingo on 2008-01-20
> **TWO said:**
> Ah right, thanks for the info.

Can I ask where you find things out from?

He is lvl 99 wizard. LOL j/k I would like to know too.

---

### Post by ubuntu-freak on 2008-01-20
> **TWO said:**
> Ah right, thanks for the info.

Can I ask where you find things out from?

 
I read one of those online meetings they have I think. Or a bug report discussion between developers.
 
Nathan

---

### Post by TWO on 2008-01-20
Ah, OK. 

Well thanks for your help, it's been really useful! Keep it going!

---

### Post by unicron0827 on 2008-01-22
im not sure if this would fit as a question under this or your streaming how-to but ill ask here since it involves a windoze box... ive got a win2k file server that for the time being hasnt been converted to Kubuntu ...yet, as hwen i have guests they wanna use it etc etc.. ANYWAYS, it contains a large hard drive with amojority of my multimedia files on it(Part of why it hasnt been coverted yet..too busy to transfer it all to reformat) and i want to mount the share it use on it... as a drive under kubuntu, i know this is doable, but i havent messed too much with the mount command & networked boxes since redhat 7... what would be the proper way to use the mount command to mount this boxes share.. so that XMMS, VLC Etc etc will work w/o first copying files from the samba share?

the windows box is Win2KSP4, my other boxes are all Kubuntu 7.04, i use primarily XMMS & VLC for my multimedia needs... VLC will work but it copies to /tmp/ first XMMS wont play over the network ata ll... and yes ive tried audacious, Kmplayer, Amarok and BMP.... none of them work... VLC WILL copy the audio AND video files to play though so i do know that my sound system & vid system is working

---

### Post by ubuntu-freak on 2008-01-22
> **unicron0827 said:**
> im not sure if this would fit as a question under this or your streaming how-to but ill ask here since it involves a windoze box... ive got a win2k file server that for the time being hasnt been converted to Kubuntu ...yet, as hwen i have guests they wanna use it etc etc.. ANYWAYS, it contains a large hard drive with amojority of my multimedia files on it(Part of why it hasnt been coverted yet..too busy to transfer it all to reformat) and i want to mount the share it use on it... as a drive under kubuntu, i know this is doable, but i havent messed too much with the mount command & networked boxes since redhat 7... what would be the proper way to use the mount command to mount this boxes share.. so that XMMS, VLC Etc etc will work w/o first copying files from the samba share?

the windows box is Win2KSP4, my other boxes are all Kubuntu 7.04, i use primarily XMMS & VLC for my multimedia needs... VLC will work but it copies to /tmp/ first XMMS wont play over the network ata ll... and yes ive tried audacious, Kmplayer, Amarok and BMP.... none of them work... VLC WILL copy the audio AND video files to play though so i do know that my sound system & vid system is working

 
You want to partition it and mount it as 'Storage' or something like that? I used the Ubuntu install disc when I was a newbie to do stuff like that. Have you tried gparted?
 
Nathan

---

### Post by unicron0827 on 2008-01-23
> **reassuringlyoffensive said:**
> You want to partition it and mount it as 'Storage' or something like that? I used the Ubuntu install disc when I was a newbie to do stuff like that. Have you tried gparted?
 
Nathan

no its already partitioned and formatted on the windows box... works fine....with my roomates windows box and my friends ibook when she comes over as far as playin directly across the network and plays locally on the windows box fine, so im fairly sure its amatter of i need to mount it as a drive on the kubuntu box or map it as a network drive

---

