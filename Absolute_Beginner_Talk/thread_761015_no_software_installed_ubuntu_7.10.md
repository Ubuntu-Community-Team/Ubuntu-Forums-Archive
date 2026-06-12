---
title: "no software installed ubuntu 7.10"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by kattou22 on 2008-04-20
Hi, I managed to install the 7.10 ubuntu trhough windows and my hard disk instead of a CD rom . Thanks to the person who mentioned that! So keep in mind that i do not have a CD burner or ubuntu CD other then 5.10.  

I installed it and when it came to install other software it would not work. I had to skip this part. So now i can boot but it only lets me go to the console mode. I want to install a desktop.     i need help as there is absolutely nothing installed at least i think!

Anyone know how i can check. I tried everything i could think of. In "bin" i cant seem to find any command that remotely looks like install .. The only idea i have is by downloading one by one the packages and installing that!!!    

Last question is there a way to "ls -a" by page or rather screen!!!!  thanks

---

### Post by tvtech on 2008-04-20
sudo apt-get install ubuntu-desktop   


that should download the desktop from the repositories and install it.

if your running 5.10 though you might want to try 

sudo aptitude install ubuntu-desktop

there was an issue between the two early on check out 

[this website]("http://www.psychocats.net/ubuntu/puregnome")

it details pretty much everything you need to know to get up and running I think it's based around 6.04???? though

---

