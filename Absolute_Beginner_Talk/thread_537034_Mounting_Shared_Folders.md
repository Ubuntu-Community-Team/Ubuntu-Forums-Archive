---
title: "Mounting Shared Folders"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by saj0577 on 2007-08-28
Hiya,

I have currently got my folder that i want to share shared other the network but i have a questions which i need some help with please.

How do i mount the network drive so it appears on my desktop whenever it is present (just like when i plug usb devices in etc.) At the minute in rhythm box my library destination is smb://saj-desktop/disk/Music Files . which is only tempory i believe so i would like to mount the network drive, 


Regards
Saj

---

### Post by saj0577 on 2007-08-28
Also the computer may not always be switched on which has the drive connected to it so when it is not turned on i simply want the drive not to appear on my desktop and for rhythm box to just not display any music (untill i develop a program which will not start rhythm box unless the drive is connected).

Saj

---

### Post by reckless2k2 on 2007-08-28
i believe gconf-editor will allow you to show your mounted drives:

[http://ubuntuforums.org/showthread.php?t=53729](http://ubuntuforums.org/showthread.php?t=53729)

That is about unchecking but you get the idea. 

As far as not showing it when not mounted, i think it will still show but nothing will be mounted in there.

---

### Post by saj0577 on 2007-08-28
Thanks alot.

Anyway have any easy step-by-step way for me to mount the network drive rather then it being a temporarily link. I have seen a few guides showing how but i could not work out which variables to change. the files i want to share i can access just their not mounted.

The local ip address of the computer with the HD mounted to (which i have shared the drive across my ubuntu network and can access temporarily: 192.168.0.10

Local ip address of computer i am using as a client to receive the shared files : 192.168.0.11

Drive Name which i have shared and want to mount: drive

Any more information needed just ask and I will do my best.

Saj

---

### Post by saj0577 on 2007-08-28
Any links or any help people?

Thanks in advance
Saj

---

### Post by saj0577 on 2007-08-29
I found this:
" How to mount/unmount network folders manually, and allow all users to read

    * Read #General Notes
    * Read #How to install Samba Server for files/folders sharing service 

    * In this example: 

    Network computer's IP: 192.168.0.2 
    Network computer's Username: myusername 
    Network computer's Password: mypassword 
    Shared folder's name: linux 
    Local mount folder: /media/sharename 

    * To mount network folder: 

sudo mkdir /media/sharename
sudo mount //192.168.0.2/linux /media/sharename/ -o username=myusername,password=mypassword

    * To unmount network folder: 

sudo umount /media/sharename/            "

but i am unsure which computer i type this into and which computer the folder /media/foldername  should be on. Could someone please simplify these instructions above for me thank you. Also i installed samba but have not configured it or changed it in anyway may this be the problem?


Thanks in advance
Saj

---

### Post by saj0577 on 2007-08-29
ERROR MESSAGE:

mount: wrong fs type, bad option, bad superblock on //192.168.0.12/disk,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Saj

---

### Post by saj0577 on 2007-08-29
I right clicked the folder and clicked connect has this mounted the folder or if the computer that has the folder on it is turned off will i have to re-connnect it this way everytime i want to use those files?

Saj

---

### Post by reckless2k2 on 2007-08-29
ok...sorry i didn't check back on this thread. i'm a little lost on what you are trying to do. do you want a permanent mount of a network share? if so, apt-get install smbfs first. then you need to do and or try a few things. determine if you only want it to mount at certain times, when only you log in and disconnect when you log out, or always connected at boot but only certain users/groups have access. i know it sounds complicated but linux is that powerful to cover all of it and more. just explain to me what you are trying to mount as in where it is and how you want it to work. for instance, i have a mounted music share that's viewable by all and only 2 users can edit it. the music server is directed at this share to serve music to anyone on my network or across the internet. this share is viewable on the local machine by all but can only be edited by a few. the share actually exists as a mounted file system from a NAS on my network. get the idea? 

you are on your way to getting there. i just need a few more details to be able to help.

---

### Post by saj0577 on 2007-08-29
I have the music store (a extenral HDD connected to computer A. I want all computers on the network to be able to see it and use them(play the music). But i only want users called Saj to be able to edit it(add files to it delete files change files etc..(so only my usernames/usergroups.) I want the drive storing the music (external HDD) to be mounted from boot on all computers. (A similar set up to yours)

A factor that may effect how it is done: the external HDD is not always connected to the computer, if i mount the drive what will happen when the drive is not accesible(connected) when i next connect the drive will it automaticaly show up on the computers as being mounted or will i have to remount it everytime.

Hope that helped.
Saj

---

### Post by reckless2k2 on 2007-08-30
ok...may i suggest gnump3d then for what you are trying to do? that's what i use and i think that is what you're trying to do. it's a music server with a nice GUI and ease of use in general. when your external HDD is mounted, you can view, play, and assigned users/groups can edit content. when the HDD is offline, the GUI will be blank. pretty simple. users will access the music server via a web browser like firefox at [http://theipofserver:8888](http://theipofserver:8888). you can open ports to the WAN and listen from some another persons house too. you get the idea. 

mount the external HDD in /etc/fstab with a gid=youradmgrp and fmask=775 and dmask=775. this directory will be vieable to all now and only can be edited by people in that group. throw it out there if you have issues understanding the fstab mount. anyway, this way the others in your network will not have to mount the drive because they can access the http gui to listen. pretty simple. let me know if that's good or you can use the same directions fstab mounting each machine. if they are windows, you will mount using "map network drive" menu. 

let me know if we are getting closer to what you want or need. oh...obviously make sure that the users you want to edit the share are part of that group. i used a designation like "music" and included my r/w users to that group along with whatever else they already have. only people in the "music" group can edit. you get the idea? you can make the group whatever you want. only thing is that after you create and or add someone to a group like in the GUI desktop, you have to log out of that desktop and log back in for them to be in that group.

---

### Post by saj0577 on 2007-09-05
Going to try it now thanks. Sorry for long reply been away for a while.

Saj

---

### Post by saj0577 on 2007-09-06
I have over 70gb of music and when ever i set the music path to the folder with all my music in the webpage takes ages to load, is their anyway to speed this up?

Saj

---

### Post by reckless2k2 on 2007-09-06
hahahaha...sorry i don't think so. you've got a lot of music. hahaha. are you using gnump3d?

---

