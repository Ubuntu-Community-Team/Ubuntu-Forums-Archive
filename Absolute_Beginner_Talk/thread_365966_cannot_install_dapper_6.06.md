---
title: "cannot install dapper 6.06"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2007-02-20
High all

had reason to format drive , when I came to re install ubuntu , all went well untill the final screen ,,heard the music ,, but had a black screen 

had screen untill that point  ( all was working as it should ) 

tried kubuntu , 128  xubuntu   EVERY ubuntu ,,( I have disks )   and same thing happened 

this is an AMD chip   dual booted with win XP    ( Xp was installed first ) 

Every other time I used Ubuntiu its worked perfectly .... 

how can I fix this problem 

I did read somewhere it could be the graphics card  and grub installer ... but mine is a AGP 

All other distros work ,( I am writiing this from freespire ,,debian based distro !)    I much prefer Ubuntu and so want to return 

Kind regards Stephen

---

### Post by ashmew2 on 2007-02-20
When this black screen thing hapens , are u able to access the tty ? 
Press CTRL ALT F2 to open a tty and u can login atleast in command line if not graphical frontend..

Btw , which graphic card are u using ? 
Plus i think it shudnt be a grub problem as grub has already done its job by booting up the system...isnt it ?

---

### Post by basilwatson on 2007-02-20
stand by will try

Thanks for the reply ... grafix card is a gforce5200 ( will confirm later )

Stephen

---

### Post by basilwatson on 2007-02-20
ok 
YES it will boot into the terminal screen , says I dont have x server installed ( live cd ???) anyway tried dpkg -i xserver ,,no luck 

as sudo su 

tried sudo dpkg-reconfigure xserver xorg

no luck 

compatibility between card and xserver???

Stephen

---

### Post by jvc26 on 2007-02-20
> 
YES it will boot into the terminal screen , says I dont have x server installed ( live cd ???) anyway tried dpkg -i xserver ,,no luck

Are you doing this from the live cd or after you've installed it?
Il

---

### Post by ashmew2 on 2007-02-20
HI again , I meant running tty from the INSTALLED system , if it is saying some error about X , just do this , open up a tty( CTRL ALT F2 ) , then first of all configure your internet , if you are using an Ethernet , it must be only typing 
```
sudo pppoeconf
```

and then starting connection with 
```
sudo pon dsl-provider
```

Once you get your internet working , try this

```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.2-0ubuntu1_all.deb
```
```
sudo dpkg -i envy_0.8.2-0ubuntu1_all.deb
```

It should install the great script Envy that will help u install your X properly. Then you do
```

Envy
```


Select the option "Install the Nvidia Driver" and then Let it download around 20 MB or something..
It should setup a working X system for you...

Please let me know how it went..

---

### Post by ashmew2 on 2007-02-20
As far as compatibility is concerned , i have no doubt that your graphic card is up to the mark...Im using an nVidia Geforce 4000 MX and UBuntu runs like water :P

---

### Post by basilwatson on 2007-02-20
Thanks all will let you know what happens ..this is the live cd it is doing it in  so I assume I have to install striaght from the boot  

Stephen

---

### Post by basilwatson on 2007-02-21
The installer and the graphics card are not seing eye to eye ..installed my old one and its fine 

its good to be home !!!!! 

every thing working as it should ! 

I have installed the nvidia drivers and will swap back the graphics card and see what happens 

thanks for all the help ,  I hope one day I can return the favor!!!

Stephen:) :guitar:  ( why not I am happy again )

---

### Post by ashmew2 on 2007-02-21
Hurray!!

---

