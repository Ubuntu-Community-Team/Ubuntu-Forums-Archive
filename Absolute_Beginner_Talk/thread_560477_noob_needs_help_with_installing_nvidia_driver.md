---
title: "noob needs help with installing nvidia driver"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by brato on 2007-09-26
ok hi iam new to this forum.

i got interested on linux and tried the ubunt version 7.04.

i got some major problems with my drivers ...

i needed to install my geforce go 6150 on my hp tx 1250ed and i did all the steps the setup asked me for.

first i allowd to log in as root
then i shut down the xserver with the command 

/etc/init.d/gdm stop

and the i come to the textbased system you know.

so far so good 

now on the nvidia site they say that i need to write this command with the package file 

to install the driver .

# sh nvidia-linux-x86_64-100.14.19-pkg2.run 

the i press enter but nothing happens ..i tried also 

/sh  nvidia-linux-x86_64-100.14.19-pkg2.run 

but nothing happens

do someone know what for error i do? 

sorry for beeing noob i know how annoying a noob can be but i tried it before asking on the forum.

---

### Post by alienexplorers on 2007-09-26
Why don't you just use the ENVY script to load your nvidia drivers.  I have a link in my signature line to the site.

---

### Post by wpshooter on 2007-09-26
> **brato said:**
> ok hi iam new to this forum.

i got interested on linux and tried the ubunt version 7.04.

i got some major problems with my drivers ...

i needed to install my geforce go 6150 on my hp tx 1250ed and i did all the steps the setup asked me for.

first i allowd to log in as root
then i shut down the xserver with the command 

/etc/init.d/gdm stop

and the i come to the textbased system you know.

so far so good 

now on the nvidia site they say that i need to write this command with the package file 

to install the driver .

# sh nvidia-linux-x86_64-100.14.19-pkg2.run 

the i press enter but nothing happens ..i tried also 

/sh  nvidia-linux-x86_64-100.14.19-pkg2.run 

but nothing happens

do someone know what for error i do? 

sorry for beeing noob i know how annoying a noob can be but i tried it before asking on the forum.


Someone correct me if I am wrong but I don't think you need to do all that stuff you listed.

I would think you would just go to the Nvidia site, download the driver and run it in the terminal (I would not think you would need to stop X server) with SUDO in front of the driver command.

OR just use the ENVY program, like the other poster said, to install the proper driver for your card, that is probably your best bet.

Good luck.

---

### Post by brato on 2007-09-26
the installation said that i need to be in root .....the when i loggid in as root it said that i need to close xserver ...but i will try with the envy program ...

but where do i need to put the files ...cause when i look at this forum i never see any command that redericts to the folder where the file is

---

### Post by Terl on 2007-09-26
All you really need to do is use the restricted drivers manager.  Select nVidia and it will download and install it for you.  I then check my xorg.conf to make sure all my resolutions are listed.  Restart per the prompt and you are done.

---

### Post by irish_flu on 2007-09-26
If you simply go to Administration ---> Restricted Drivers Manager, is the NVidia driver listed there, to be enabled?

---

### Post by rsambuca on 2007-09-26
Why don't you just try the built-in Restricted Drivers Manager before trying outside programs?  It can be found under "System -> Administration -> Restricted Drivers Manager"

The benefit of this method is that you are more likely to have painless upgrades to Gusty than if you use envy or manual installation methods.

---

### Post by Majorix on 2007-09-26
Agreed on Restricted Drivers, it works most of the time, and as said, installing it via ENVY sometimes causes problems when upgrading.

---

### Post by brato on 2007-09-26
i tried now but it sais that i dont need restricted drivers!!!

---

### Post by brato on 2007-09-26
i forgot to say that i have the 64 bit version of ubuntu but i dont think that this can be the problem

---

### Post by brato on 2007-09-26
i forgot to say that i have the 64 bit version of ubuntu but i dont think that this can be the problem

---

### Post by brato on 2007-09-26
ok i tried with envy but i get an error 

 error : dependency is not satisfiable : xserver-xorg-dev

ok i think i did not download the xorg.conf file ...but i dont get it where to put it?

Does somone know?

---

