---
title: "x server failed to load"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by cknightfl on 2007-07-08
Hey everyone,
Im new to ubuntu and linux.  I installed yesterday after having trouble and haveing to put noapic in the grub menu (thanks from some help from you guys).  When i installed i booted up and i get a error message about x server unable to load.  the error message says something like ee can not loat 'nvdia' drivers,
ee no drivers found.  it than takes me to a login and where i put in my login and than it takes me to a command line (im assuming).  I have no idea what to do.  I read some of the other postes on x server problems but i just dont get what they are saying.  If i understand them currectly i need to download the drivers or use envy?  I am a absolutly new to this stuff.  

Here are my specs
hp dv 9000
nvidi geforce go 6150 graphics card
1 gig ram
120 gig hd 
dual booted with vista preinstalled
v7 32 bit ubuntu

---

### Post by nitro_n2o on 2007-07-08
If you want to nvidia driver just type this in you command line 
```
sudo apt-get install nvidia-glx
``` This restart X or the machine.. It might work and save you the work of config files

---

### Post by Fire Legion on 2007-07-08
I have the same problem. I'll try the above solution and report back...

---

### Post by cknightfl on 2007-07-08
just tryed that code and it says no unknow command

---

### Post by nitro_n2o on 2007-07-08
> **cknightfl said:**
> just tryed that code and it says no unknow command
Are  you sure that you are typing the same thing exactly...
you can try this: 
```
sudo aptitude install nvidia-glx
```
Your non-free repositories might be disabled, but it should not say unknown command, unless you don't have root premissions
if so (you have # in the prompt) just type the command without sudo

---

### Post by cknightfl on 2007-07-08
i got  it to work.  I typed suda instead of sudo.  Thank you so much this community is amazing!

---

