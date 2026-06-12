---
title: "AHHH, please help with UBUNTU!!!"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by psp_gamer on 2006-11-29
Please bear with me, i have no idea how to use linux at all... Uber n00b alert!

Ok, let me start by explaining my background:

I am 17 and have been an avid mac used since the age of three. I have very extensive knowledge of anything Mac from os7 to

the newest 10.5(beta leak). About two years ago, i recieved my first pc... It was a hp pavilion zv5000. Horrible, i hated 

every minute of xp home. I immediately upgraded to xp pro. A little better, but not quite there. I have had so far on my 

laptop, xp home sp1 and 2, xp pro sp1 and 2, many builds of vista,and ubuntu 5.10. I had no idea what i was doing with 

ubuntu so it came off. Just last xmas, I built my gaming pc. It was running a tripple boot of vista , osx86 10.4.5, and 

ubuntu 6.06lts but now it just has xp and ubuntu. It has an intel D848PFT2 mobo, 1gb of ram, and an agp ATI Radeon x1600 

pro. I did a fresh install of ubuntu because not getting xgl to run is driving me nuts. I have tried guide upon guide and 

none, and i repeat, NONE have worked. I have searched this forum up and down. Nothing, please from the deepest of my heart 

will a power user of ubuntu take me under their help and show me how to get xgl, beryl and other fancy things to do with 

ubuntu working? I'm extremely sorry for the long post, but i've had it with ubuntu and about to take it back off, but i 

really don't want to because it can do so much!

---

### Post by bulldog on 2006-11-29
If the only reason to keep Ubuntu is to show off with beryl and emerald,maybe it's better to take it off.

There are many tutorials to install Beryl and Emerald for ATI graphic's so do a search and keep on trying.
It's all Beta so no guarantees for stability.

I have a nVidia graphic's and it runs very well on Dapper as well on Edgy.

---

### Post by clapper65 on 2006-11-29
You also might want to try easyubuntu.  It's a fairly decent configuration program that does a lot of things for you.  I'm pretty sure part of its configs will set up ATI video drivers. Details on easyubuntu are at [http://easyubuntu.freecontrib.org](http://easyubuntu.freecontrib.org)

---

### Post by psp_gamer on 2006-11-29
The reason I want to use ubuntu instead of windows, is because it boasts alot of similarities with the mac os. It's just the fact that I can't use it to it's full potential.I used the ati wiki multiple times. I would greatly appreciate it if someone can help.

Edit, thankyou to the post above!

---

### Post by xpod on 2006-11-29
Your going to give up just cause you cant suss beryl out yet:confused: 

You would be giving up on sooo much for so little me thinks.
Beryls great and all that but figuring it out would mabey come a lot easier to you if you put just a little of the time you`ve put into macs into Ubuntu.

The first advice i was given about Beryl during that first week was to leave it till i`d got some basic grasp of what i was doing.

Best advice i could have been given.:D 
Of course once you at least know the basics then Beryl becomes sooo much simpler and there are plenty relatively simple guides out there including pricechilds thread with about every howto on it.

---

### Post by Henry Rayker on 2006-11-29
If you don't have any reason for keeping 6.06lts around, you may move to 6.10...it's my understanding that 6.10 has AIGLX pre-installed, so it's just a matter of installing the ati drivers and Beryl, right?

I don't know for sure as all that eye candy gives me a headache and just eats my poor laptop's resources for lunch.

---

### Post by bulldog on 2006-11-29
> **psp_gamer said:**
> The reason I want to use ubuntu instead of windows, is because it boasts alot of similarities with the mac os. It's just the fact that I can't use it to it's full potential.I used the ati wiki multiple times. I would greatly appreciate it if someone can help.

Edit, thankyou to the post above!

And it didn't work,what are you expecting from somebody when he's willing  to help you?
He  will use the same kind of tutorials you do.

---

### Post by zekopeko on 2006-11-29
i used this guide to install the ATI drivers without a problem(use the second method):

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

now beryl...
i used some guide from their forum but the site is currently down but i hope they get it back up soon.

linky: [http://www.beryl-project.org/](http://www.beryl-project.org/)

you should also try to search forums here. there is probably some guide from beryl forum here that can help you set up beryl

hope it helps

---

### Post by psp_gamer on 2006-11-29
Thankyou for your help guys(gals too if any of you are on the forums)... I am going to do a completely fresh install of 6.06lts and am going to start off with easy ubuntu. I will keep this thread updated. I really cant wait to dive  deeper into the system and get some cool things running.

---

### Post by Teamgeist on 2006-11-29
I also recommend using Edgy Eft (Ubuntu 6.10) due to the fact that AIGLX is included in x.org 7.1 and you do not need to install XGL.
So install Ubuntu 6.10, grab the ATI Drivers from somewhere. Maybe even the ones from the Ubuntu repositories work and install beryl.

That should be it.

Howto: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
Haven't  used it myself though since I have an Intel Card.

Good luck.

---

### Post by compmodder26 on 2006-11-29
> **Teamgeist said:**
> I also recommend using Edgy Eft (Ubuntu 6.10) due to the fact that AIGLX is included in x.org 7.1 and you do not need to install XGL.

I thought that ATI cards couldn't use AIGLX.

---

### Post by psp_gamer on 2006-11-30
Thaknyou all for your help on this matter. After installing a fresh copy of ubuntu and easyubuntu, I got this upon fglrxinfo:


xlib: extension "Xfree86-DRI" missing on display " :0.0".
Display: 0.0 screen 0
OpenGL Vendow String: Mesa Project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer srting: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I hope that's what i need to move on with xgl and beryl... any input?

---

### Post by psp_gamer on 2006-11-30
Also for somereason, sudo gedit won't let let me edit the xorg.confg... when i open it, it just shows up blank. Any idea on how to fix that?

---

### Post by kylevan on 2006-11-30
you're sure you're typing in /etc/X11/xorg.conf ?

---

### Post by KatanaSwordfish on 2006-11-30
I got beryl running the other day. The first time i tried to install it, it messed up (well... i messed up) my xorg.conf file.  So i booted with a disk and formatted. Felt like giving the whole thing another go from the very start.

Heres what i did:

-Formatted my drive.
-Booted with disk, reinstalled.
-after all my installation stuff finished, i made sure i was completly updated before installing anything at all. so, i ran system > admin > update manager, and then proceeded to install all the recommended updates.
-Next, i installed both EasyUbuntu and Automatix2 from this guide (ubuntuguide.org). After those finished i installed all the app's and various things that i wanted from those programs.
-After completing those installations, i ran the update manager once again, made sure everything was updated completely.

ok, part 2 will vary a little bit for you, because i have an nvidia card, however, this is the guide i followed (very precisely): [www.ubuntuguide.org](www.ubuntuguide.org). it helped a lot to understand how to add repositories and use the basic terminal commands. keep in mind i am a n00b, and this is my second day with ubuntu, so i had to learn all new commands.

-using ubuntuguide.org, i installed my proper nVidia drivers and made sure i followed the guide very closely. (didnt want to mess up and have to reinstall again!). Even though you have an ATI card, there is also a tutorial on installing Beryl/XGL for ATI cards.
-well, after my drivers were completely installed, now came the moment of truth. i hit the cntrl+alt+backspace, and restart. 
-i gave beryl-manager a shot and, voila, i saw the squirming beryl splash screen.


I guess my point is, try to endure and dont loose hope. I got frustrated when i messed up the first time, but learning to use a new OS  is like learning anything else in life, difficult and frustrating. However, just remember that the end result is very rewarding; not only will you have your new application, but also the skill and experience that you have never had before.

Right now, i have beryl up and running on my PC and i love it. I think what got me was making sure to check the **update manager** often. First thing i did with my fresh install was to update, and i updated again after using easyubuntu and automatix. Good luck with ubuntu and just keep trying.  :D

---

### Post by psp_gamer on 2006-12-09
Well, here we go again, i'm gonna do another fresh install and do exactly as you did just with the ati drivers... Thankyou for your help...

---

### Post by riven0 on 2006-12-10
> **psp_gamer said:**
> Well, here we go again, i'm gonna do another fresh install and do exactly as you did just with the ati drivers... Thankyou for your help...

psp_gamer, seriously you should go with edgy eft. The thing is, I could never get beryl running in dapper, but I installed edgy, followed [this howto]("http://www.ubuntuforums.org/showthread.php?t=290841&highlight=install+beryl") and got beryl working. My card is an ati 9200PRO and I'm using the Linux open source drivers.

---

