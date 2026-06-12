---
title: "x session and a fw other noob questions :)"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by werebunny on 2006-03-22
hello ubuntu community.
i have been playing with ubuntu for a few days now and had to do 5 reinstall because of my noobinnes.
after trying to install xgl and compiz i gave up. too advanced for me.
so i did a clean install but after 1-2 hours managed to mess my x session (i think i was trying to install ati driver for my 9600pro card)

so the question is/are:
1. how to backup x.confg (i think that's the name of the file with the session configuration) and later restore it if my xserver doesn't start. 
terminal commands pliz

2. how to organize my /home? should i put everything in /home/user or /home so that other potential user can get to it? also why can't copy to /home files? i get "no permssions" msg. just want to put stuff in my home so that other user can get to it.

3. /home should be on a separate partition but get's listed as a folder. is there a command to see on the terminal what are my partition and how much space is free/used?

4. easyubuntu---> is it good for installing ati driver? 
   don't wanna mess my install (again)  

thnx in advance for any help

---

### Post by matthewv on 2006-03-22
[QUOTE=werebunny]hello ubuntu community.
i have been playing with ubuntu for a few days now and had to do 5 reinstall because of my noobinnes.
after trying to install xgl and compiz i gave up. too advanced for me.
so i did a clean install but after 1-2 hours managed to mess my x session (i think i was trying to install ati driver for my 9600pro card)

so the question is/are:
1. how to backup x.confg (i think that's the name of the file with the session configuration) and later restore it if my xserver doesn't start. 
terminal commands pliz[/quote]

Do, in terminal ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` to backup ur x config and ```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
``` to restore your x config.

> 
2. how to organize my /home? should i put everything in /home/user or /home so that other potential user can get to it? also why can't copy to /home files? i get "no permssions" msg. just want to put stuff in my home so that other user can get to it.

All your files should go in /home/<username> . 

> 
3. /home should be on a separate partition but get's listed as a folder. is there a command to see on the terminal what are my partition and how much space is free/used?

/home probably is on a separate partition, it is just mounted as a folder (as are all partitions, eg /media) not sure how to check on them from terminal, although running ```
sudo fdisk -l
``` will show all your partitions.

> 
4. easyubuntu---> is it good for installing ati driver? 
   don't wanna mess my install (again)  

thnx in advance for any help
No idea :) Never used easyubuntu

---

