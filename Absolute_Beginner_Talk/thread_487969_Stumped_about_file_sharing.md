---
title: "Stumped about file sharing"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by bgb1122 on 2007-06-29
I have a laptop and a PC both with Feisty installed and I cannot for the life of me get any kind of file sharing going.  I am very new to Ubuntu (maybe a week).  My computers both have a wireless connection to the same router.  Besides using the obvious menu selection to share a folder, I have tried installing and using samba and read some about NFS.  I guess I am absolutely clueless and need it spelled out for me.  The Ubuntu Guide page was almost helpful but I don't quite understand it.  Any help would be great!

---

### Post by Zzl1xndd on 2007-06-29
Try going to Places then Connect to server then type in the IP of the computer you wanna access, it should give you an Icon on your desktop works for me everytime.

---

### Post by Seisen on 2007-06-29
Are you trying to share files between two ubuntu computers, than you can use NFS.

[https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29]("https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29")

---

### Post by punx45 on 2007-06-29
since you have two linux systems, I would highly suggest not using SAMBA, since it is intended for use in communicating with windows systems.   NFS is definitely the way to go when communicating between all *nix systems.   

any specific questions you have about NFS?

---

### Post by skullmunky on 2007-07-09
hi, i'm kind of stumped about file sharing too.  i have plenty of experience with setting up NFS by hand, but i'm curious whether how much can be done automagically - namely, can avahi or another zeroconf thing make the nfs shares advertise on the lan?  

i have two machines, let's call them "adam" and "betty".  both are running feisty, adam is in KDE and betty is Gnome, just to make things interesting ;) 

on adam, i R-click on a folder, choose Share, turn on Samba and NFS. since i'm not using windows i don't care about Samba, i just want to deal with nfs.  

i take a look in /etc/exports, everything looks good there:

/home/me/shared/ *(rw,async,all_squash)

now on betty, i can mount the directory:

cd
mkdir adam_shared
sudo mount 10.0.0.2:/home/me/shared adam_shared

and it works fine.  actually it's still read-only, which i assume is because the uid's are not the same on the two machines since not using NIS.  but that's no big deal.

now, here's the real question: on betty, can i get that nfs share to show up in nautilus or konqueror? 

in Places->Network i have "Windows Network" with nothing in it.  i installed everything avahi-related that i could find on both adam and betty.  on Betty, the Zeroconf discovery applet found a Limewire tunes service and a "workstation" service from Adam, but has no plugins to handle either of them.  but this makes me thing avahi is working but just not advertising my nfs share, maybe?  

i guess the thing i'm curious about is that the nice GUI options make it look like this ought to work without needing to, say, edit my fstab by hand.

---

### Post by kelvin spratt on 2007-07-09
i don't know if this will help you but i just click on places then network and all our computers show up nothing has been set up and just transfer files from one to another through the router.

---

### Post by skullmunky on 2007-07-09
i love it when stuff Just Works.  


even when it Just Works for someone else, not me. :) 

no, i don't have anything in Places->Network

---

### Post by punx45 on 2007-07-09
since you did a manual mount, you actually wouldn't have anything in places>network.
you mounted the share in ~/adam_shared
you should be able to browse to that like any other directory.   or am I missing something?

---

