---
title: "Changing etc/environment"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by marcos.placona on 2007-08-18
Hi Guys, it's been a while since I've last posted here. I was running my Ubuntu fine here, but decided to add some environment variables to it, so they would be loaded when I logged in.

I added them to /etc/environment, doing:

sudo gedit /etc/environment

I added my variables, saved and tried to logoff and login again.

Now, I can't login, 'cause it says my session lasted for less than 10 seconds, and tells me that there's a problema with my /etc/environment file.

My question. Is there any chance for me to recover to the old /etc/environment, or even upate that file to remove the last 4 lines (the lines I added with my variables)?

I tried to do it via terminal, but with no success as when I try to use gedit or edit, it tells me that it can't display it.

Thanks,

Marcos Placona

---

### Post by nitro_n2o on 2007-08-18
login to your ubuntu from the recovery mode..  go that file and change it.. or even without graphics.. just type vim /etc/environment and edit it
if this didn't help.. you can boot from the liveCD and go edit the file graphically, but make sure you edit the file on the hard drive, not the one that comes with the liveCD

goo luck

---

### Post by marcos.placona on 2007-08-18
Hi thanks for your answer, but I'm still having problems. I was able to open the file using vim, but don't know how to save it. And tried to open using the cd, but don't know how to get to the file via terminal, as I have to use sudo to be able to change the file.

Sorry, i'm pretty noob....

cheers

---

### Post by nitro_n2o on 2007-08-18
so... if you don't know how to use vim... use nano it's easier 
do the following: 
sudo nano /etc/environment 
move normally with the cursor and delete the lines you don't want to keep with backspace and delete normally.. 
then CTRL+O to 'write out' or save the file 
it'll ask u for the file name just hit enter 
then CTRL+X to exit 
and that's it :)

---

