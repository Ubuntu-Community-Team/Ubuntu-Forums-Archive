---
title: "Urgent: I can not log in anymore after"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by taekr on 2008-01-13
OH MY GOD!!!

I can not log in anymore!!!!  

I got a CRT monitor from my friend and just wanted to test it. 

I went to System --> Administration --> Screens and Grahpics

I clicked on Screen 2 and enabled 'secondary screen'..   chose a model for the monitor. 

it asked me to re-login.  I restarted the system.. 

I rebooted..  and first I got a screen with a name of Nvidia ...  

Then, it went to the log-in page. I typed my user name and password .. and enter.. 

a message pops up saying.. 

"Your home directory is listed as:'home/mark' but it does not appear to exist. Do you want to log in withe the / (root) directory as your home directory? ... blah blah.."

I tried to log in as 'root'.. but there was nothing I can not access to anything..

Wow.. this is a disaster..   How can I fix this??  I really don't want to reinstall again.

---

### Post by smartboyathome on 2008-01-13
You will have to use the command line to fix this. Once the login screen comes up, press control+alt+f1 and login with the username root and your password. Then, cd to /home. Type ls to see which whies are located there. if you see one called mark (it will be colored), then your home directory is there. If not, create it with the command mkdir mark. This should fix your problem (but you somehow got your home folder deleted if you did the latter).

---

### Post by taekr on 2008-01-13
> **smartboyathome said:**
> You will have to use the command line to fix this. Once the login screen comes up, press control+alt+f1 and login with the username root and your password. Then, cd to /home. Type ls to see which whies are located there. if you see one called mark (it will be colored), then your home directory is there. If not, create it with the command mkdir mark. This should fix your problem (but you somehow got your home folder deleted if you did the latter).

My home folder is not deleted. I am using LiveCD now and I can see my folder. I mounted the home partition and checked that my folder it there.

---

### Post by taekr on 2008-01-13
> **smartboyathome said:**
> You will have to use the command line to fix this. Once the login screen comes up, press control+alt+f1 and login with the username root and your password. Then, cd to /home. Type ls to see which whies are located there. if you see one called mark (it will be colored), then your home directory is there. If not, create it with the command mkdir mark. This should fix your problem (but you somehow got your home folder deleted if you did the latter).

Anyways, I did it like you suggest. I log in in the terminal and created a folder named 'mark'. But first of all, I disabled secondary display. Then restarted, all my settings are gone. Desktop settings and everything..     Screen resolution is 600 X 480.. or something.  Ubuntu failed to mount partitions..  /home and another partition..

I opened /etc/fstab to find it is a blank. 

T T ;; this is so frustrating. Since a month ago when converting to Ubuntu from Windows, I am having  a problem after a problem.. 

Plz, help me.

---

### Post by bodhi.zazen on 2008-01-13
I know it is overwheliming to start a new OS 

fstab can't be empty ~ you need to access it as root :

```
gksu gedit /etc/fstab
```

or

```
sudo nano /etc/fstab
```

Anyway, we can look at your mounted partiton(s) with mount 

```
mount
```

---

