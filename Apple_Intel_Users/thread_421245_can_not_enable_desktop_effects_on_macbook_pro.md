---
title: "can not enable desktop effects on macbook pro"
date: 2007-04-24
forum: Apple Intel Users
---

### Post by Mattybook on 2007-04-24
hi

i installed triple boot with os x; win xp, ubuntu 7.04
everything went well 
enabled the restricted ati driver
everything looks good
want to enable desktop effects (and later on use beryl) => says can not enable desktop effects

the first error it gave was composite not enabled so i did enable it in xorg.conf
now it just says can not enable effects? 

can anyone help? 
my pc is a macbook pro 2Gzz (first generation) with 256 mb ati x1600 and 1 gb ram

thanks in advance

---

### Post by Greywhind on 2007-04-24
The FGLRX driver doesn't support the composite extension. If you use it, there's no way you can use AIGLX, which is the underlying technology in the default desktop effects.

If you want Compiz or Beryl, you have to install XGL underneath them instead. That means you won't be able to play 3D-accelerated games, etc. while Compiz/Beryl is running.

I have the same card, and I chose to just avoid Compiz/Beryl.

---

### Post by Mattybook on 2007-04-24
i don' play games and stuff in linux, i just want to use beryl...
can anyone help me please? :(

---

### Post by ronocdh on 2007-04-24
> **Mattybook said:**
> i don' play games and stuff in linux, i just want to use beryl...
can anyone help me please? :(
This is [but one]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m") guide which should get you on your way. It's a little old now, but I haven't bothered to find better yet, sorry. Googling around and of course checking the Desktop Effects forum should get your pretty far! We ATI folks have it rough, though, I'm afraid.

Key point is that the Beryl in the repositories won't work with our cards; you'll have to disable the Universe repo and grab an older Beryl elsewhere. All this is mentioned in the link I gave. Good luck, and let us know how it goes for you.

---

### Post by Mattybook on 2007-04-25
tried that allready
when i switch sessions, it get's all scrambled and stuff so it does not work ... 

and even then, i still can't switch  those desktop effects on which means i still won't get the cool cube effect

me sad :(

---

### Post by Mattybook on 2007-04-25
hm

now it did succeed partially!
i have the wobble effect, but not the desktop effect
and installing beryl like told in that tutorial makes that none of the effects work

---

### Post by ronocdh on 2007-04-25
> **Mattybook said:**
> hm

now it did succeed partially!
i have the wobble effect, but not the desktop effect
and installing beryl like told in that tutorial makes that none of the effects work
Right, Beryl will likely give you some trouble, but the first half of the guide involves setting up XGL, which allows for Compiz (which is running your wobbly windows).

---

### Post by rscow on 2007-04-25
Once you enable the restricted driver, you have to run aticonfig

sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
startx

Then see what you get

---

### Post by Mattybook on 2007-04-27
i have allready done this :)
desktop effects works partially now. the wobble effect works, the desktop cube does not.
when i install beryl, no effects are available

---

### Post by Ouchy on 2007-04-27
Did you downgrade the core-version already?

Anyways, this is a more recent guide that you might want to try yourself:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

Can't guarantee that it will fix your problem, but it's worth a shot I guess.

---

### Post by Mattybook on 2007-04-27
yes i did :)

is there anyone who would like to help me installing beryl. 
I tried 3 manuals allready and still nothing 

what i did so far is the xgl server + gnome login part
i've put the universe repo away
installed beryl again  = nothing works


is there perhaps anybody who can help me via msn or something cause i really want this stuff to work but it's driving me crazy

---

### Post by Mattybook on 2007-04-27
ok i tried that last tutorial

this is what i get when i launch beryl manager:

matty@Mattybook:~$ beryl manager
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

---

### Post by carli on 2007-10-21
I also have the exact same problem on my Acer 8210. Does anyone know if there is going to be a fix for this in the future? And what would it require? Must ATI make a new restricted driver to make this work or is it on someone else to fix it?

---

