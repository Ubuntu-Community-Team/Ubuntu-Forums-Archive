---
title: "Avant Window Navigator - help needed"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by dinuop on 2007-11-28
hi

can anybody help me out to install AWN through ofline
cuz i dont hv internet on my Ubuntu 7.10 gutsy 64bit

is it work on AMD64  with SIS graphics 128mb
2gig ram acer laptop?

thanks in advance

dinu

---

### Post by subs on 2007-11-28
this should help

> [http://ubuntuforums.org/showthread.php?p=3506749&page=11](http://ubuntuforums.org/showthread.php?p=3506749&page=11)

---

### Post by dinuop on 2007-11-28
hi subs

as i said i dont have internet on my ubuntu

so what are the files i need to download and 
waht command i should type on terminal

-din

---

### Post by jba6511 on 2007-11-28
correct me if I am wrong but you would need access to the internet in order to get avant. The repositories have it, but require internet connectivity. The other option is to compile from source, but again you would need connectivity to download the source.  If you can post on this forum then you should be able to use the connection to grab a .deb, the source, or grab avant from the repos.

---

### Post by dinuop on 2007-11-28
ya i hv dual boot and i can download files through windows xp and run it on ubuntu

can pls tel me step by step doing it

i installed doing copying through ftp sites of pakages puting into directory called gusty n source and edited instllation path like 

deb file:///(direcorry) gusty awant-window-navigator
&
deb-scr file:///(direcorry) gusty awant-window-navigator 

its saying somting called public key error

overcomming that i finallay installed
but if i click the program some squre window comming and closed momently

i can access setting of AWN in prefrence

but doc not displaying

---

### Post by Paul820 on 2007-11-28
You can get avant-window-navigator from here in a deb package: [http://www.getdeb.net/category.php?id=11]("http://www.getdeb.net/category.php?id=11")

---

### Post by dinuop on 2007-11-28
i m getting this error

-din

---

### Post by dinuop on 2007-11-28
can anybody help me in this regard

or any way i can install kiba-doc offline?

---

### Post by jba6511 on 2007-11-28
first: I am assuming you have an amd processor and the system you are running is the 64 bit version of Ubuntu. If not, the architecture needs to match the package you download. 

second: have you tried installing avant before? I would remove the package and reinstall the package you are having trouble with.

Really, you should just use synaptic and download avant from the repos. I do not understand how you got online to download the deb but can not get online with Ubuntu. Are you using wireless?

---

### Post by dinuop on 2007-11-29
i m using amd with 64bit processor

b4 installing using deb i tried to install by
download individual files and put in gusty folder and source folder respectively it didnt worked. i mean i got the AWN maneger but if i start awn then it comes up and applets are running (shows in process)
i cant see the doc 

now what should i do 
is my graphic card not capable(i m using sis graphic card with 128mb)

if  i really need internet to install then pls guide me how to install my
option GTMax e PCMCIA 3g card in ubuntu amd 64 bit

---

### Post by dinuop on 2007-11-29
how i can delete perviosly installed file showing in terminal window
its having root permition
how i can delete files having root permision

---

### Post by dinuop on 2007-11-29
now i m getting this error while instaling through terminal

---

### Post by jlotempio on 2007-12-03
I'm not sure if this was already covered, but, are you running any sort of compositor, such as compiz or beryl?  It is quite easy to run in Gutsy.  But, if you are not running a compositor, I don't think you will be able to run AWN correctly.  This may be why everything is working for you, except for the visual of the actually program.  I'm no Ubuntu guru, but as far as I know, you HAVE to be running a compositor for AWN.  But, I know that there are other docks that don't require a compositor if you don't want to run one. 

Also, why exactly can you not access internet in Ubuntu but can in XP.  I would think that is more of an issue than AWN.  Look into getting internet working, it should not be that difficult to do.  I got my impossible PowerBook running wireless in feisty and gutsy.

---

### Post by numbah_one's on 2007-12-08
i am having with awn,help needed pls..

spiniker@spiniker-laptop:~$ avant-window-navigator
/usr/share/themes/Blubuntu/gtk-2.0/gtkrc:169: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

should i remove blubuntu? i already did an uninstall/reinstall of compiz..any help would be appreciated.

---

