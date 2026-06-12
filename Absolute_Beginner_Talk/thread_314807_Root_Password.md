---
title: "Root Password"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by jmdean on 2006-12-08
I have just installed Ubuntu 6.10 from a DVD on a magazine and am very new to Linux. The installation went well but at no time can I remember being asked for a root password. I now want to change the screen resolution but I think I need to be "root" to do so.

I have obviously done something wrong and will have to do the installation again but can anyone tell me where to look out for specifying the root password.

---

### Post by seijuro on 2006-12-08
ubuntu doesn't make you set a root password instead anything you need root privledges for just use sudo.

---

### Post by amo-ej1 on 2006-12-08
a default ubuntu install has the root password disabled. You can escalate your privileges by prefixing a command you wish to execute with sudo e.g.
```
sudo do_the_magic
``` this will prompt you for your _own_ password. The same will apply to the resolution.

You can always assign a root password using the same method but that's discouraged.

---

### Post by hotbrainz on 2006-12-08
>  jmdean  
I have just installed Ubuntu 6.10 from a DVD on a magazine and am very new to Linux. The installation went well but at no time can I remember being asked for a root password. I now want to change the screen resolution but I think I need to be "root" to do so.

I have obviously done something wrong and will have to do the installation again but can anyone tell me where to look out for specifying the root password.



This should help you...you dont have to do a reinstall

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

If you cant figure it out then ask and i will help.

---

### Post by jmdean on 2006-12-08
Many thanks all for your help. I will now spend a bit of time reading through the info at the website.

---

### Post by quarkhirad on 2006-12-08
When u installed ubuntu it would have asked u to enter a password 
(say u chose 123456abcd)
this is the password u use to log in to ubuntu and by default ur root password is the same as ur login password 

whenever u want to change to root user in terminal he just enter the command sudo su and then press enter and at the password promt type 123456abcd (that is ur password ) and enter. Thats it ur the root usr.

Cheeers

---

### Post by tej_kohli on 2006-12-08
Hi, my name is Tej Kohli and I had the same problem.
When I installed UBUNTU I don't remember that a root password was asked, I just used my user's password, wich I thought the Ubuntu will assign the superuser root password. Later I wanted to install some software and it said I don't have enough privileges. Then I tried to switch to root and didn't accepted my password as root password. I was blocked, I really thought about reinstalling. Thanks to you I won't need to. Thanks!
     Best regards, 
     Tej Kohli

---

### Post by quarkhirad on 2006-12-09
> **tej_kohli said:**
> Hi, my name is Tej Kohli and I had the same problem.
 I was blocked, I really thought about reinstalling. Thanks to you I won't need to. Thanks!
     Best regards, 
     Tej Kohli

Hey tej ur welcome :) :) ;) :) :) . however please do remember to check the forums threads as well as try posting ur problem u will definately get some response. Reinstalling is not the way out. Only chickens do that. 

Cheers 
quarkhirad

---

### Post by Rnny_X on 2006-12-11
I cannot write password in shell...

-sudo
-password:

And then I can't write anything in shell, just a white space...](*,) 
Problem?

---

### Post by 23meg on 2006-12-11
Just type it and hit enter; it won't appear on the screen.

---

