---
title: "running microshafts I.E."
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by caffiend on 2006-05-30
I need it for my job can anyone help me get it or an emulator to run on ubuntu. Also I keep trying to get to my desktop from terminal I'm typing cd desktop, cd ~/desktop, sudo desktop, ](*,)  I CAN'T GET THERE AND ITS DRIVING ME MAD. ](*,)

---

### Post by Shay Stephens on 2006-05-30
The most reliable method for me has been using crossover office to install and run Internet Explorer.

And remember in Linux, files and folders are case sensitive, so capitalize Desktop and you should get better results ;-)

---

### Post by AndyCooll on 2006-05-30
I think that probably should be something like cd ~/Desktop (note the capital letter!).

For IE you will probably need to install Wine or use XP through VMware player/server.

---

### Post by halfvolle melk on 2006-05-30
Can't help you with the first. Maybe you can get it to run under Wine or something. As for the second, try
```
cd ~/**D**esktop
```
D, not d. Almost everything on *nix is case sensitve :)

---

### Post by Sef on 2006-05-30
Crossover is a commericalized version of WINE.  WINE you can download from the respositories.


> Also I keep trying to get to my desktop from terminal I'm typing cd desktop, cd ~/desktop, sudo desktop, 

so you just get a screen with a command line when you boot in?

---

### Post by caffiend on 2006-05-30
Thanks everyone guess I'm proving I belong here in begginers with the caps thing that worked duh:-? 
I did install wine and I'm kinda trying to avoid crossover office cuz I don't want to pay the fee. I hate paying for software not because of any noble reason just cuz I'm a cheap @ss

[QUOTE=caffiend]I need it for my job can anyone help me get it or an emulator to run on ubuntu. Also I keep trying to get to my desktop from terminal I'm typing cd desktop, cd ~/desktop, sudo desktop, ](*,)  I CAN'T GET THERE AND ITS DRIVING ME MAD. ](*,)[/QUOTE]

---

### Post by Kilz on 2006-05-30
[QUOTE=caffiend]Thanks everyone guess I'm proving I belong here in begginers with the caps thing that worked duh:-? 
I did install wine and I'm kinda trying to avoid crossover office cuz I don't want to pay the fee. I hate paying for software not because of any noble reason just cuz I'm a cheap @ss[/QUOTE]
The easiest way to get IE working with wine is a program called ies4linux [http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html) you have to install cabextract and wine to use it, but synaptic has them. You just download ies4linux, extract it. Open a termanal, type in cd ~/Desktop/ies4linux then ./ies4linux. It will ask you what versions you want to install, then setup is automatic.
Beware, wine is a bug for bug emulator of windowz, dont use IE for your normal surfing. It isnt a good idea.

---

### Post by RRS on 2006-05-30
You might give [this Firefox extension]("https://addons.mozilla.org/firefox/59/") a try. I've only used it a couple times but it seems to work without causing any other problems.

---

### Post by ProjectGod on 2006-05-30
when you say... i'm tryin' to get to my desktop... do you mean YOUR desktop as in the directory where you have all your files / folders ? if so if you want to get there via the terminal... its under /home/<yourusername>/desktop.

i think! cause i'm not on ubuntu right now! :mrgreen:

if on the other hand if youre stuck in the command when you start the machine... assuming you do have X installed... type: 

**startx**

to get into gui. once again... I THINK! :D HAHA!

---

### Post by aysiu on 2006-05-30
I second Kilz's recommendation of IES4Linux. No muss, no fuss.

---

