---
title: "Need help"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by marzy on 2006-02-07
Hi i am totaly new to linux. I wanted to learn it and mess around with it so i have a Hp netsever E 40 i installed ubuntu i start the computer up and it says starting unbuntu and does it's check and has the ok. Then it gets to the bit when you login. number one it is the terminal and then it flashes a few times then it says I cannot start the X sever (your graphical interface). It is likely that it is not ser up correctly. Would you like to view the x sever output to diagnose the problem. Then you can choose yes or no when i hit no it says i will disable this x sever for now. Resrart GDM when it is configured correctly.

Now i can only use the terminal.

P.S sorry if this is hard to read or it isn't written out right i was rushing it

---

### Post by paulmilliken on 2006-02-07
I'm not sure what the problem is, however, I suggest trying a reinstall.

Paul

---

### Post by JakeSpeare on 2006-02-07
sounds like your xorg.conf file may have a problem.  Did you make any changes to display settings or that file before this problem occurred - such as setting a resolution your hardware does not support?

---

### Post by Robgould on 2006-02-07
It is for sure an Xorg issue.  You need to edit the file.  This is not the simplest task in the world, but not overwhelming either.  Do you have any experince in linux command line at all?  You will need to use and editor (vi) to open and edit the file /etc/Xorg.conf.
 
sudo vi /etc/org.conf
 
then you need to read the file and find where the settings there are in conflict with your hardware and change those settings.  
 
then save the file and reboot.  
 
If you serch xorg in here you will find a lot of posts about editing this file. 
 
Just trying to give you some general direction.

---

### Post by warleggon on 2006-02-07
I have ran into this kind of problem myself. It came down to choosing the right driver and monitor resolution. You may have to search the net a bit to find the right driver name for your card. I have a Gforce 5950 and I have to choose vesa when setting up X manually. I had to search the net more than a little to find that out.

The net should be able to give you a good idea what the resolution and freq will work for your monitor. 

At the risk of getting shunned by the Gnu gods...hooking up your monitor to a Winders box (gasp...choke) can get you the info you need for the rez and freq.

Hope this helps

Warleggon

---

