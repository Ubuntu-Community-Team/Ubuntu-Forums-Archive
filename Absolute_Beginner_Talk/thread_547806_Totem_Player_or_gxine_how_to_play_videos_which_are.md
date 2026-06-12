---
title: "Totem Player or gxine: how to play videos which are stored on networked hard drives?"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by mrpurple on 2007-09-10
Using Totem or gxine, I can play movies which are on my local hard drives. I want to play movies that are on hard drives of networked Windows and Linux computers or NAS. I can access the movie files (fly.avi, for example) on a networked Windows machine, but I try to play them with Totem, I get this error: “There is no input plugin to handle the location of this movie.” untill some months ago was working great, only after some upgrade or installation it has stop to work.
Can you please instruct me on how to play movies located on network hard drives? Thank you.:confused:

---

### Post by nalmeth on 2007-09-10
Go to System -> Administration -> Shared Folders, the utility that comes up should download some network stuff for you, perhaps that will solve the problem.

Beyond that are you sure you installed all the codecs needed to play your files?

---

### Post by mrpurple on 2007-09-11
i tryed, but nothing has changed, the window shared folders come up there is in shared folder one that i 'd need shared and in general proprieties there is the name of the windows network.
that is a setting that i did some times ago, is maybe a cause of that that now are not playng anymore ?
is not a codec prolem because if i take the file in a local folder it has played
this is make me crazy !!

---

### Post by Jussi01 on 2007-09-11
You need to mount the shared drives in fstab, this will make them accessable to totem and gxine. see this link for more details: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by mrpurple on 2007-09-12
hi Jussi, 
what means ? that i have to mount the HD network ?
Can You post the entire strings ?
thank You
i try to follow the guide You post, but it seems not working on my ubuntu.
i added the follow row:
> 
smb://purpledisk /chroot/purpledisk none rw,hard, intr 0 0

thank You for any help

---

### Post by mrpurple on 2007-09-14
the problem still and jussi solution doesn't fix. any help ?
thank you

---

### Post by mrpurple on 2007-09-17
up

---

### Post by sympeltun on 2007-09-22
bump

lol, i want to know the answer to this as well.

someone help please

---

### Post by jimrz on 2007-09-22
[[COLOR="Sienna"]**_here you go_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=280473&highlight=smbmount") ... this HowTo worked nicely for me on several boxes

---

### Post by mrpurple on 2007-09-23
hi, after the comand "smbclient -L 192.168.1.xxx -U% i obtaing this output:

" Domain=[PURPLE] OS=[Unix] Server=[Samba 3.0.20b]
tree connect failed: NT_STATUS_ACCESS_DENIED"
i verifyed to put the right ip address of my NAS, but still thiss error.
 
thank you  for help

---

### Post by AndyCooll on 2007-09-23
I think we need to start at the beginning and ask you some basic questions, and then work from there.

We're assuming you have Samba installed. Have you? Samba is the software which interprets the "smb" protocol. You'll need that to access Windows shares (and in effect it is that process that the above posters have provided links for). 

Another question, have you inputted your Samba password (again, which those links will have shown you how to do)

:cool:

---

### Post by mrpurple on 2007-09-24
sorry, but i can browse al the folder shared in my NAS. i can copy and rename files. the ony problem is in seeing video. 
all the folder shared  has the location name starting with smb:// 
i'm tryng to review the samba configuration but is not so clear how it works.
i'm new to linux world. 
for the pasword i set to remember always ..  

thank you

---

### Post by DtH72 on 2007-10-11
Hi, I had the same problem. The only thing that worked for me was to remove totem-xine package and to install totem-gstreamer.

Code:

sudo apt-get remove totem-xine

sudo apt-get install totem-gstreamer


I hope it's the solution for your problem, it was for me...

Good luck!

Dylan

---

### Post by mrpurple on 2007-10-22
. finally .... Seems works great now. 
So is a problem in totem - xine ? 
thanks for your help Dylan

---

### Post by mrpurple on 2007-12-19
dear i don't know what happen .. but now still not working anymore ... i try to repeat the removing and the installation, but doesn't work .. 
VLC or Mplayer are not capable to play video from my network in streaming. Could be a samba setting ?

---

