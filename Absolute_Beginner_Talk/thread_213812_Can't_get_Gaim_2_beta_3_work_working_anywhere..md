---
title: "Can't get Gaim 2 beta 3 work working anywhere."
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Epperly on 2006-07-11
Hi, I've tried like every link I could find using search but nothing will work, I'm gettin like an error every way I try to install it.

Can anybody help me please?
(oh, and I'm an Ubuntu newbie, hah)

---

### Post by Dr. Nick on 2006-07-11
try the autopackage ver yet?

[http://prdownloads.sourceforge.net/gaim/gaim-2.0.0beta3.x86.package?download](http://prdownloads.sourceforge.net/gaim/gaim-2.0.0beta3.x86.package?download)

Just save to your hard drive then double click it, if you are in gnome it should start insalling pretty easily

---

### Post by Epperly on 2006-07-11
I get this... =\
[http://img.photobucket.com/albums/v92/k20importtuner/Screenshot-gaim-2.png](http://img.photobucket.com/albums/v92/k20importtuner/Screenshot-gaim-2.png)

---

### Post by Dr. Nick on 2006-07-11
bah, why is it using gedit i wander?

It should self execute, if you right click it what all options to open it do you have?

---

### Post by Epperly on 2006-07-11
I can open it with another application... but Idk which...

---

### Post by Dr. Nick on 2006-07-11
run the following command from a terminal


autopackage-launcher-gtk


if that gives you this output (Usage: autopackage-launcher-gtk <FILENAME>)
then open the terminal to the directory you have the .package save in and execute

 autopackage-launcher-gtk gaim-2.0.0beta3.x86.package

---

### Post by Epperly on 2006-07-11
bash: autopackage-launcher-gtk: command not found

---

### Post by Dr. Nick on 2006-07-11
weird, are you on dapper 6.10? I had it installed by default on mine, and see no mention of how to install it on the forums or in synaptic

---

### Post by Epperly on 2006-07-11
Yeah, I am. I have 1.5 installed but I'd prefer updating to version 2 beta 3

---

### Post by Dr. Nick on 2006-07-11
[http://www.autopackage.org/docs/howto-install/](http://www.autopackage.org/docs/howto-install/)

try the persmission part, gaim wanst the first program i used autopackage for, thats why I didnt have to do that step.

Good luck, let me know if that fixes it

---

### Post by Epperly on 2006-07-11
Yayyy! Thank you Dr. Nick! :-D

[edit]Oh, also... this isn't gonna update itself back to 1.5 eventually right? I thought I read somethin about it doing that...[/edit]

---

### Post by digby on 2006-07-11
If it does, you can just remove gaim and then reinstall the new version.```
sudo apt-get remove gaim
```
Alternatively, you can install it from the .debs (I found them somewhere on this forum - if you can't, PM me and I'll find some way for you to dl them from me).  That way apt will have them registered as a newer version and not mess w/ them.

---

### Post by Dr. Nick on 2006-07-11
if you have gaim installed in apt when it comes with a new version it will overwrite the auto package ver, you can remove gaim from synaptic, but that will also remove ubuntu desktop which will make upgrades to the next version a bit different. When edgy comes out in a few months, if you upgrade from dapper then I would reinstall ubuntu desktop which will overwrite your auto package gaim with whatever version is in the reps at that time. 

You would then have to reinstall the beta3 if it is still the newest at that time. 
BTW you will now have a Program in Applications - System Tools to manage autopackage programs.

And any new autopackage programs will install easier, I forgot that I had used autopackage before so I didnt have to go through some of the setup you did this time since I had already done it.

---

### Post by Epperly on 2006-07-12
Ohhh okay, thanks... but one more thing... Under Internet, GAIM shows up twice, and when I go to add/remove applications the 2 icons are always under internet whether it says removed or not...

---

### Post by Dr. Nick on 2006-07-12
I wouldnt worry about thier being 2 icons, I imagine they both open the same gaim, I just reinstalled beta 3 and it overwrote my 1.5 version. I would just delete one of them,

---

### Post by Epperly on 2006-07-12
wtf this is so gay.. it went back to 1.5. Such a hassle for a simple thing like IM.
How would I delete one of those icons though?

---

### Post by digby on 2006-07-12
Use the alacarte menu editor.

Applications>Accessories>Alacarte Menu Editor

---

### Post by Epperly on 2006-07-13
Thanks everyone! It's up and workin good now with one icon. :)

---

### Post by Epperly on 2006-11-09
oops ha, I just realized why I had two icons, because when I uninstall gaim 1.5 that comes in a fresh Ubuntu, I don't remove gaim-data as well, and they're not packaged together.

---

