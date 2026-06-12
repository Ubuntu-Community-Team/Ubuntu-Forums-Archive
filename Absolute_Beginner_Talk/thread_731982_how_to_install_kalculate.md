---
title: "how to install kalculate"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by linuxtoindia on 2008-03-22
i have downloaded a software today  ,, here it is ''kalkulate''/home/akshay/Desktop/kalculate-pro60.tgz 

when i click on it it extracts  somethg and then shows whole list!
i dont know where to start and how to install it!
please help!

---

### Post by kellemes on 2008-03-22
> **linuxtoindia said:**
> i have downloaded a software today  ,, here it is ''kalkulate''/home/akshay/Desktop/kalculate-pro60.tgz 

when i click on it it extracts  somethg and then shows whole list!
i dont know where to start and how to install it!
please help!

Where did you get this software from? You have a link to the website where you found it?

---

### Post by linuxtoindia on 2008-03-22
yes i do have

---

### Post by linuxtoindia on 2008-03-22
[http://kalculate.com/kalculate.php](http://kalculate.com/kalculate.php) 

please help

---

### Post by linuxtoindia on 2008-03-23
/home/akshay/Desktop/kalculate-pro60 here it is

---

### Post by linuxtoindia on 2008-03-23
y:~/Desktop/kalculate-pro60$ make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by linuxtoindia on 2008-03-23
not able to configure

i see  many folders the main folder

---

### Post by N1N31NCHN41L5 on 2008-03-23
if im right and kalculate is a ubuntu program easiest way to install is to go into the termianl and:

sudo apt-get install kalculate

---

### Post by forestpixie on 2008-03-23
It appears to be a .rpm - can you give a bit more information- like what's in the folder you've extracted. Is there a readme?

This is the install page from the manual - it says you need redhat - which works with rpms instead of debs - but you can use aline to make a deb file, just need a bit more information from you.
[http://kalculate.com/kal_manual/index.html](http://kalculate.com/kal_manual/index.html)

---

### Post by linuxtoindia on 2008-03-23
yes it is in **/home/akshay/Desktop/kalculate-pro60'**'
now how to install it friend

---

### Post by forestpixie on 2008-03-23
perhaps a bit more information - I'd guessed that already :) - what's the contents of the folder

```
ls /home/akshay/Desktop/kalculate-pro60
```

---

### Post by linuxtoindia on 2008-03-23
it has many folders in it seems to be the contents of the software

---

### Post by linuxtoindia on 2008-03-23
there is and read me file but it says some other story!

---

### Post by forestpixie on 2008-03-23
If you want help you need to do a bit more than tell me it's got folders and software - I know that :) , run the command and post the output here  please - and if there's a read me what does it say - attach it if it's not too big.

---

### Post by linuxtoindia on 2008-03-24
read me 
Kalculate PRO Version 3.2
             
                  How to install Kalculate in your machine

   To install Kalculate on your machine, just follow the following steps:

    1. First, the obvious : You will need Linux on your PC. OpenLX Linux 11.0.
    2. Login with your id and required password.
    3. [user@localhost user]$ su <enter>
    4. [root@localhost user]# mount /mnt/cdrom <enter>
    5. [root@localhost user]# cd /mnt/cdrom/kalculate <enter>
    6. [root@localhost kalculate]# ./install-admin <enter>

   If you are in text-mode then start your X window before running kalculate. Kalculate can be installed in text-mode.

    7. [user@localhost user]$ kalculate-admin <enter>

   While using kalculate, you will require kalculate authentication password. It is 123.

---

### Post by linuxtoindia on 2008-03-24
[IMG]http://www.ziddu.com/download.php?uid=Z7GelJ2uaqufnOKnZqqhkZSoY6ydlpas6[/IMG] 


here is the pic of the folders



**[[B]http://www.ziddu.com/download.php?uid=Z7GelJ2uaqufnOKnZqqhkZSoY6ydlpas6**]("http://www.ziddu.com/download.php?uid=Z7GelJ2uaqufnOKnZqqhkZSoY6ydlpas6")[/B]

---

### Post by forestpixie on 2008-03-24
There is a folder in there - kalculate-install - what is the contents of that folder please, the installation help page is as clear as mud.
Open a terminal and use this command please

```
dir -R Desktop/kalculate-pro60/kalculate-install
```

[http://www.kalculate.com/kal_manual/index.html](http://www.kalculate.com/kal_manual/index.html)

Not sure I can help anymore with this

Tried to download to see what was there - but can't.

---

### Post by linuxtoindia on 2008-03-25
here is the out put of the dir....



''[B]akshay@akshay:~$ dir -R Desktop/kalculate-pro60/kalculate-install
Desktop/kalculate-pro60/kalculate-install:
kalculate_admin.desktop  kalculate_gnome.png  README
kalculate_admin.kdelnk   kalculate.kdelnk     req_rpm_list_9.1
kalculate.desktop        kal_icon.xpm         req_rpm_list_fedora_core2
[/B]

---

### Post by linuxtoindia on 2008-03-25
[B]and what to do now,, and thanks for all your efforts!
[/B]

---

### Post by linuxtoindia on 2008-03-25
sholud i place here the thumb nail?

---

### Post by forestpixie on 2008-03-25
I really don't know where to go from here, I see there is a readme - does that say the same as the other one?

I'm not going to be able to help with this I'm afraid.

---

### Post by linuxtoindia on 2008-03-25
ok finally

''unsolved thread'' hope some one in future will solve this here!

---

### Post by forestpixie on 2008-03-25
> ok finally

what do you mean by that!

---

### Post by linuxtoindia on 2008-03-25
i mean ,, as you being so genius gave up!
how cud i will be to solve this!

so i will move back to windows as no indian software for business except kalkulate is available for linux-ubuntu ..
if yet youcan do some thing then please help!!!

---

### Post by linuxtoindia on 2008-03-25
can i change this rpm to a debain?

---

### Post by forestpixie on 2008-03-25
I guess with an attitude like that you won't be able to install it. Try talking to the creator of the software as it's not available outside of India so I couldn't get a copy to look for myself to work out how to install it. Pictures of folders I'm afraid don't really help very much.

---

### Post by forestpixie on 2008-03-25
Yes you can change rpm to debian.

---

### Post by Perfect Storm on 2008-03-25
Normally, it's a bad idea, but here you go;

```
sudo aptitude update && sudo aptitude safe-upgrade
sudo aptitude install alien
cd ~/Desktop
sudo alien -i <rpm file>
```

---

### Post by BL00dFox on 2008-03-25
go to terminal, type

sudo apt-get install kalculate

---

