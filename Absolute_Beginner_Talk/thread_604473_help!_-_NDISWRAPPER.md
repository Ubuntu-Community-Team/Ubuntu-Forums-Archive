---
title: "help! - NDISWRAPPER"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by fitzybhoy on 2007-11-06
guys, on these instructions it states to install NDISWRAPPER in ubuntu open console.

does that mean i run ubuntu normally and install it via the desktop??

can somebody give me a link to download?






[http://ubuntuforums.org/showthread.php?t=579535](http://ubuntuforums.org/showthread.php?t=579535)


> **srd said:**
> install ndiswrapper 
in ubuntu open console 

    sudo apt-get update
    sudo apt-get install ndiswrapper-common
    sudo apt-get install ndiswrapper-utils
    sudo apt-get install cabextract

Download this windows drivers from HP (sp34152.exe)
 
    mkdir sp
    cd /sp
    mv sp34152.exe /sp
    cabextract sp34152.exe
    sudo ndiswrapper -i bcmwl5.inf
    sudo ndiswrapper -l
    sudo ndiswrapper -m
    sudo modprobe ndiswrapper
    sudo gedit /etc/modules

insert this : ndiswrapper
    sudo reboot

---

### Post by mike^_^ on 2007-11-06
I'm pretty sure the OP meant "in ubuntu, open a console." So to answer your question, yes you enter those commands into a normal console.

---

### Post by fitzybhoy on 2007-11-06
> **mike^_^ said:**
> I'm pretty sure the OP meant "in ubuntu, open a console." So to answer your question, yes you enter those commands into a normal console.

how do you download it??

i get an error when i try ...

---

