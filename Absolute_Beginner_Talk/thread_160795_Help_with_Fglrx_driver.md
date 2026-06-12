---
title: "Help with Fglrx driver"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by zxcvbnm on 2006-04-15
How do i get the driver for my graphics card.......When i type in sudo apt-get install xorg-driver-fglrx it says can't find package

---

### Post by PhoenixP3K on 2006-04-15
HOWTO: [Add Extra-repository ]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories") Be sure to **sudo apt-get update** to refresh the dependencies. You could also visit ATI website and get the Linux drivers from them, along with install instructions.

---

### Post by zxcvbnm on 2006-04-15
I tried but everytime it says cannot unlock.... permision denied

---

### Post by zxcvbnm on 2006-04-15
bump

---

### Post by zxcvbnm on 2006-04-15
Also would it be different if i am installing Kubuntu because that is what i have

---

### Post by zxcvbnm on 2006-04-16
WOW one answer and that was 17 hours ago.....Please help i have been trying to get Kubuntu working for ever.....
BUMP

Oh and HAPPY EASTER!!!!!!

---

### Post by sn123 on 2006-04-16
[QUOTE=zxcvbnm]I tried but everytime it says cannot unlock.... permision denied[/QUOTE]
do you have any other update manager open while you are trying this, like Synaptic? If yes, then close every thing else and try again. If no, then post the entire error message that you receive when you try to install fglrx.


S

---

### Post by zxcvbnm on 2006-04-16
thanks for answering but i really don't no..I am very very noobish to linux.....

How would i check if it opened or not......oh and exactly it says (13 permission denied) if that helps

Also i know this is a stupid question but sometimes when i do something it say you need to be a superuser do do it......
How do ido that

---

### Post by sn123 on 2006-04-16
[QUOTE=zxcvbnm]thanks for answering but i really don't no..I am very very noobish to linux.....

How would i check if it opened or not......oh and exactly it says (13 permission denied) if that helps

Also i know this is a stupid question but sometimes when i do something it say you need to be a superuser do do it......
How do ido that[/QUOTE]
To be a superuser you prefix the command with sudo, you need to be a superuser (a.k.a. administrator in Windows) to install new packages (aka programs in Windows). apt-get requires you to be super user, hence to install new programs using apt-get you need to prefix it with sudo.
If synaptic package manager or update manager is open it would show up in the task bar, so close any open windows that you are not currently using and then follow this guide to install fglrx:
[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

Let me know how it goes.

S

---

### Post by zxcvbnm on 2006-04-16
[QUOTE=sn123]To be a superuser you prefix the command with sudo, you need to be a superuser (a.k.a. administrator in Windows) to install new packages (aka programs in Windows). apt-get requires you to be super user, hence to install new programs using apt-get you need to prefix it with sudo.
If synaptic package manager or update manager is open it would show up in the task bar, so close any open windows that you are not currently using and then follow this guide to install fglrx:
[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)

Let me know how it goes.

S[/QUOTE]


I don't have the desktop running yet because i need the divers so i can get into The desktop

SO i can only go into teminal

Also i used umm VGA i think from another bus port and i got into desktop but everthing is really really big like it is magnetized 100 times..LOL

But if i get the driver installed for my ASUS ATI Radeon EAX1600 then i am thinking it would work

Do you think if i install a live CD  i could see my Linux partitions and  download the driver and put it in manually

---

### Post by sn123 on 2006-04-16
[QUOTE=zxcvbnm]I don't have the desktop running yet because i need the divers so i can get into The desktop

SO i can only go into teminal[/QUOTE]
at the prompt, type this:
sudo dpkg-reconfigure xserver-xorg 
(enter your password when it prompts for it)
accept the defaults for everything except when you come to the driver section, select "vesa" as the driver there and complete the configuration process by selecting defaults everywhere else, once done reboot your system. That should get your X (GUI) up and running. Later you can follow the guide in my previous post to install fglrx.

HTH,
S

---

### Post by zxcvbnm on 2006-04-16
[QUOTE=sn123]at the prompt, type this:
sudo dpkg-reconfigure xserver-xorg 
(enter your password when it prompts for it)
accept the defaults for everything except when you come to the driver section, select "vesa" as the driver there and complete the configuration process by selecting defaults everywhere else, once done reboot your system. That should get your X (GUI) up and running. Later you can follow the guide in my previous post to install fglrx.

HTH,
S[/QUOTE]

Oh dam i did that lol...but i didn't restart my system....that sucks..LOL

I'll try it and get back to you

---

### Post by zxcvbnm on 2006-04-16
I am trying to configure my network settings but  it says i need a password to login as root what is the password because my login pass doesn't work

---

### Post by sn123 on 2006-04-16
[QUOTE=zxcvbnm]I am trying to configure my network settings but  it says i need a password to login as root what is the password because my login pass doesn't work[/QUOTE]
login as a normal user (i.e. with your userid and password) and use sudo whenever you need admin privileges. In case you are using some GUI application which prompts you for the root password after you've logged in, enter your password and that should work.

---

### Post by zxcvbnm on 2006-04-16
[QUOTE=sn123]login as a normal user (i.e. with your userid and password) and use sudo whenever you need admin privileges. In case you are using some GUI application which prompts you for the root password after you've logged in, enter your password and that should work.[/QUOTE]

I have went in aand changed password to root ...but it didn't work.....


I have kubuntu so i don't know if it is different

I can't edit my internet network because it is asking me for the rot passowrd and it isn't my userpassword

---

### Post by sn123 on 2006-04-16
[QUOTE=zxcvbnm]I have went in aand changed password to root ...but it didn't work.....


I have kubuntu so i don't know if it is different

I can't edit my internet network because it is asking me for the rot passowrd and it isn't my userpassword[/QUOTE]
I don't know why it's not accepting your password, do this simple test:
Open a terminal (Applications-->Accessories-->Terminal), at the prompt type this:
```

gksudo gedit

```
this should ideally show a graphical prompt where you can enter your password, enter your password and see if a text editor opens. Also, I am assuming that you are logged in as the same user which you created during the ubuntu installation. If not then login as that particular user and try again.

PS: I hope you atleast got your desktop up and running!
HTH,
S

---

### Post by zxcvbnm on 2006-04-16
[QUOTE=sn123]I don't know why it's not accepting your password, do this simple test:
Open a terminal (Applications-->Accessories-->Terminal), at the prompt type this:
```

gksudo gedit

```
this should ideally show a graphical prompt where you can enter your password, enter your password and see if a text editor opens. Also, I am assuming that you are logged in as the same user which you created during the ubuntu installation. If not then login as that particular user and try again.

PS: I hope you atleast got your desktop up and running!
HTH,
S[/QUOTE]

Thanks i got into my desktop and figured out to login as root.......

Thanks for your help

---

