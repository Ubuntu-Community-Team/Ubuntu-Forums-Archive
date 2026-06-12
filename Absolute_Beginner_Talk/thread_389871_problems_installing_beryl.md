---
title: "problems installing beryl"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by skidkid87 on 2007-03-21
help me out plz 

every time I type "./configure" after extracting the .tar.gz it tells me in the end:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

can you help me out 
I get the feeling I'm installing the wrong file (like it was meant for gnome and I'm using KDE) and if I'm wrong can u post the correct link for me to download and install it ?

thnx

---

### Post by lamalex on 2007-03-21
do ```
./configure --help
``` and see if there is a special prefix for kde. The other option is to do it via repo and apt-get. This is by far the easier of the two ways. it's probably something like ```
./configure --kde-config
```^^that's just my guess, look through --help.

---

### Post by skidkid87 on 2007-03-21
I tried what u said but I'm a complete n00b so I can't manipulate things out of help, and the second command didn't work it's incorrect :S

---

### Post by bdogg64 on 2007-03-21
why dont you install beryl from the repos?

[http://wiki.beryl-project.org](http://wiki.beryl-project.org)

---

### Post by mahy on 2007-03-21
Why the heck you wanna compile Beryl?? Just follow these instructions:

[http://wiki.beryl-project.org/index.php/Install/Ubuntu](http://wiki.beryl-project.org/index.php/Install/Ubuntu)

Feel free to ask for more help.

---

### Post by skidkid87 on 2007-03-21
guys I only have ubuntu for a couple of weeks now I have no idea what those links want to say I can't understand them :S

---

### Post by mahy on 2007-03-21
> **skidkid87 said:**
> guys I only have ubuntu for a couple of weeks now I have no idea what those links want to say I can't understand them :S

Please tell me what your graphics card is and i'll direct you to the appropriate howto. And also tell me what desktop environment you use (is your desktop brown?).

---

### Post by skidkid87 on 2007-03-21
I think I have ubuntu 6.06 but I'm not sure if u know a way to tell which version of ubuntu do I have I'd be grateful

---

### Post by skidkid87 on 2007-03-21
my graphics card is nvidia 6200 GForce made by chaintech and I'm using kde

---

### Post by mahy on 2007-03-21
> **skidkid87 said:**
> I think I have ubuntu 6.06 but I'm not sure if u know a way to tell which version of ubuntu do I have I'd be grateful

Open terminal (Konsole), put this into it:

 cat /etc/lsb-release 

and post the outcome here.

---

### Post by skidkid87 on 2007-03-21
the output is :

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"

---

### Post by skidkid87 on 2007-03-21
this is the output:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"

---

### Post by mahy on 2007-03-21
That's Edgy, of course :)

Firstly, you'll have to install nvidia drivers (if you haven't already).

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I can't advise you more on this, coz i use an ATI card. If you complete this step, you can proceed to:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

Your best bet would be to find someone with similar hardware.

---

### Post by skidkid87 on 2007-03-21
ok thnx man

---

