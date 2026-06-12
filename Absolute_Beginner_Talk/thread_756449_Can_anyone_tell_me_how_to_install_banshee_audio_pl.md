---
title: "Can anyone tell me how to install banshee audio player!"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by AeThEr777 on 2008-04-15
please! i need an audio player and i cant get any of the other ones! 

AeThEr777

---

### Post by spiderbatdad on 2008-04-15
```
sudo apt-get install banshee
```

---

### Post by y6FgBn)~v on 2008-04-15
You are quick Spider :) beat me to it lol

---

### Post by AeThEr777 on 2008-04-15
This is the error i get

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  banshee: Depends: libnjb5 but it is not installable
           Depends: libmono-cairo2.0-cil (>= 1.0) but it is not installable
           Depends: libmono1.0-cil (>= 1.2.4) but it is not installable
E: Broken packages

What do i do?

---

### Post by rfruth on 2008-04-15
The real question is forthcoming :confused:

---

### Post by AeThEr777 on 2008-04-15
Anyone?? I need an audio player

---

### Post by rfruth on 2008-04-16
Will the package manager (synaptic) run - can you fix broken packages if need be ?

---

### Post by ryanhaigh on 2008-04-16
Rhythmbox should already be installed on your system, if you are having problems playing mp3s in particular thats another issue. To install mp3 support (along with flash, java and some other essentials just [click here](apt://ubuntu-restricted-extras). You will need to have universe and multiverse enabled in System>Admin>Software sources to download much of the software available for ubuntu.

---

### Post by kostkon on 2008-04-16
> **AeThEr777 said:**
> This is the error i get

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  banshee: Depends: libnjb5 but it is not installable
           Depends: libmono-cairo2.0-cil (>= 1.0) but it is not installable
           Depends: libmono1.0-cil (>= 1.2.4) but it is not installable
E: Broken packages

What do i do?
Please, go to *System -> Administration -> Software Sources* and check if all the repositories are enabled (i.e. checked) in the first tab.

Then, try again to install the program.

---

### Post by AeThEr777 on 2008-04-16
Hey all the repositories are checked i have:

Canonical-supported Open Source Software (main)
Community-maintained Open Source software(universe)
Propietary Drivers for devices (restricted)
Software restricted by copyright or legal issues (multiuniverse)

those are the ones i have checked. Should i also have Source code checked?
Do i have to change anything on the third party software to get this up and running?

AeThEr777

---

### Post by misfitpierce on 2008-04-16
Could maybe install a different package from [http://linuxappfinder.com/package/banshee](http://linuxappfinder.com/package/banshee)

and then see if it works for you and auto updates libraries and such.

---

### Post by AeThEr777 on 2008-04-16
I downloaded the package it opened in another window saying:

error:dependancy is not satisfiable:libnjb5

ANYONE please!!! Can someone just remotely control my comp and fix this! lol

---

### Post by misfitpierce on 2008-04-17
> **AeThEr777 said:**
> I downloaded the package it opened in another window saying:

error:dependancy is not satisfiable:libnjb5

ANYONE please!!! Can someone just remotely control my comp and fix this! lol
[http://mirrors.kernel.org/ubuntu/pool/main/libn/libnjb/libnjb5_2.2.5-4.1ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libn/libnjb/libnjb5_2.2.5-4.1ubuntu2_i386.deb)

There is 32 bit of libnjb5 ??

---

### Post by ryanhaigh on 2008-04-17
You should not install from anywhere other than the ubuntu repos. Also you do not need to have source code active. Can you please do the following and report and errors:
```

sudo apt-get update
sudo apt-get install banshee

```

---

### Post by misfitpierce on 2008-04-17
hmmm

---

### Post by AeThEr777 on 2008-04-17
Ryan for the first cmd i did not get any error it updated everything i think... for the second command i got:

Setting up banshee (0.13.1+dfsg-3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

So i look in the audio video section and surprise, Banshee is there!!!!!
THank you so freaking much! I dont know how or what happened but it finally worked. Thanx a bunch guys

---

### Post by wawadave on 2008-04-17
D/l and install the restricted content that the link was given on the first page. i just installed banshee no problem., but i had installed the restricted content a few days ago.
 allso make sure your updates are all done. and like suggested try  going through synaptic package manager.

---

### Post by AeThEr777 on 2008-04-17
Sry so now i have banshee BUT it says i have unsupported codecs and I cannot play the mp3's!! Agghhh how do i get these?

AeThEr777

---

### Post by k3lt01 on 2008-04-17
> **AeThEr777 said:**
> Sry so now i have banshee BUT it says i have unsupported codecs and I cannot play the mp3's!! Agghhh how do i get these?

AeThEr777By following Ryans suggestion on page 1. Here is the posy again, just click the link and then click yes.
> **ryanhaigh said:**
> Rhythmbox should already be installed on your system, if you are having problems playing mp3s in particular thats another issue. To install mp3 support (along with flash, java and some other essentials just [click here](apt://ubuntu-restricted-extras). You will need to have universe and multiverse enabled in System>Admin>Software sources to download much of the software available for ubuntu.

---

