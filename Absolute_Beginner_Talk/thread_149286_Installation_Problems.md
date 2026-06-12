---
title: "Installation Problems"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Dark26435 on 2006-03-23
Hello, I am very new to Linux and I recently got a copy of Ubuntu v.5.04 for intel x86 from a teacher of mine. 

I have a multiple partion on my drive set up with XP on one part and a section reserved for Linux.

I got through most of the installation that I can guess and I get to a part where I have to log-in and there I get an error message that states
----- I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

I go into that and it is all pretty much jibberish to me at this point.

Can anyone please help me and give some direction on how to correct this. 

Thank you.

---

### Post by KansasJoe on 2006-03-23
video card problem....what video card are you using?

---

### Post by Dark26435 on 2006-03-23
update to my last message////
--- after I get out of the diagnosis screen it tells me

" I will disable this X server for now. Restart GDM when it is configured correctly"
I am trying to learn this but I dont know what a GDM is, how to configure it, let alone restart it.

I am using an ATI Radeon x700 pro, pci express.

Any and all help is greatly appreciated. 
Thank you.

---

### Post by gpeck157 on 2006-03-23
[QUOTE=Dark26435]Hello, I am very new to Linux and I recently got a copy of Ubuntu v.5.04 for intel x86 from a teacher of mine. 

I have a multiple partion on my drive set up with XP on one part and a section reserved for Linux.

I got through most of the installation that I can guess and I get to a part where I have to log-in and there I get an error message that states
----- I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

I go into that and it is all pretty much jibberish to me at this point.

Can anyone please help me and give some direction on how to correct this. 

Thank you.[/QUOTE]

Hi Dark,

I have the same problem and just adding my two cents. I've been using Ubuntu Breezy now for a few months with no problems until yesterday when I tried to log in and got the same message as you. The only thing I did prior to this problem was upgrade Wine. I then uninstalled it using apt-get from the command line after I got the arcane message you did, but I still can't start my graphical interface either. I hope someone can help. I now have a lot of stuff on my Ubuntu side (I have a dual boot system - Linux and XP) that I don't want to lose.

G

---

### Post by taurus on 2006-03-23
From a terminal, do
```

sudo nano /etc/X11/xorg.conf

```
Scroll down with the arrow key until you get to the section that says about your card.  Change it to vesa...
```

Driver         "vesa"

```
Reboot and see if you can get back to X.  Now, read the instructions on how to install ATI's driver from 
[http://www.ubuntuforums.org/showthread.php?t=22496&highlight=howto+ATI](http://www.ubuntuforums.org/showthread.php?t=22496&highlight=howto+ATI)

---

### Post by Dark26435 on 2006-03-23
I have not been able to do anything. I was able to get back to the login page and I logged in there and said I had some mail. Which I didnt really understand because I did not even have an internet connection up yet. I figured out how to read the messages but I didnt understand what they were for. So I am still at the point.

---

### Post by Dark26435 on 2006-03-23
Ok Taurus, just to verify

is XXX@XXX~$ the terminal?   
 where as X=comp name etc...

if so.... i ran the code as you said and it came up to a blank document. There was nothing in there to scoll to. It seemed all I could do was add text?

if not... can you direct me how to get to a terminal or what I may have done wrong or why that was blank?

But for now I am off to work.. thanks for the help and ill check back when I get home.

---

### Post by gpeck157 on 2006-03-25
[QUOTE=Dark26435]Ok Taurus, just to verify

is XXX@XXX~$ the terminal?   
 where as X=comp name etc...

if so.... i ran the code as you said and it came up to a blank document. There was nothing in there to scoll to. It seemed all I could do was add text?

if not... can you direct me how to get to a terminal or what I may have done wrong or why that was blank?

But for now I am off to work.. thanks for the help and ill check back when I get home.[/QUOTE]
 
You may want to check this thread: 

[http://www.ubuntuforums.org/showthread.php?t=149497&highlight=server](http://www.ubuntuforums.org/showthread.php?t=149497&highlight=server)

I was able to solve my X Server problem by following it, specifically:
```
sudo dpkg-reconfigure xserver-xorg
```

Glen

---

### Post by akiro.yamamoto on 2006-03-25
Yup thats the secret sauce for a plain as jane default(Failsafe) GUI configuration ;)

---

### Post by Dark26435 on 2006-03-25
Thank you so much everyone. I am in and so far everything is working. Tell me one more thing though. If I need further help should I come back here or just use the IRC chat that is built in?

Thanks again you all were great!!!!

---

### Post by gpeck157 on 2006-03-25
[QUOTE=Dark26435]Thank you so much everyone. I am in and so far everything is working. Tell me one more thing though. If I need further help should I come back here or just use the IRC chat that is built in?

Thanks again you all were great!!!![/QUOTE]

Just speaking for myself, I have found 99% of what I've ever needed right here in the Forum.

Take care, glad to help.

Glen

---

