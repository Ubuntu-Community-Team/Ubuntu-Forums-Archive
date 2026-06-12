---
title: "Wine and Beryl"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by kspn on 2007-06-25
I want to be able to run some Windows games on my nice shiney Xubuntu Box, bowever I also want to keep the beryl interface tweaks because I think that they look really cool.

I have installed VMWare (testing ongoing).

I have heard that wine and beryl have some issues working together, is that so and if so is something _like_ VMWare the only other option.

I don't play many 3D Games (the only one at the moment is Guild Wars), most of the games I play are turn based type games so slightly slower interface is not an issue as far as I am concerned.

Any tips/suggestions are appreciated.

---

### Post by cogadh on 2007-06-25
Vitual machines will not allow you to play games that make any use of 3D at all, they do not have the necessary access to the hardware to do that. Wine will work fine if you have Beryl configured, you just need to switch your Window Manager back to XFCE's default before you run any apps (i.e. turn off Beryl before you try playing). Just right-click on the Beryl Settings Manager icon in panel and go to the "Select Window Manager" option. Choose XFCE's window manager, sorry, I don't know it's actual name, just don't select Beryl or Compiz.

---

### Post by kspn on 2007-06-25
Cool, I will try that for my 3d Games.

For the other games I will run them in VMWare for higher stability (I don't want to have to work out how to bug fix a windows app that doesn't like wine)

---

### Post by cogadh on 2007-06-25
Most games unless they are really, *really* simple games (like Flash web apps) make some use of your 3D hardware and/or DirectX, which will likely mean they can't be run in a virtual machine. What games in particular are you trying to play through VMWare?

---

### Post by kspn on 2007-06-25
The Games I am looking at playing are:

_VMWare:_
Starcraft + Expansion (Direct Draw)
Space Empires 4 (Looks 3d but uses bmp files)
Master of Orion (dosBox)
Transport Tycoon Deluxe (Direct Draw)

_3d Games:_
Master of Orion 3
Guild wars
*Another Game I cannot remember the title of*

Many of these games are older games but I find them quite enjoyable
for example I find _Master of Orion_ more fun to play than _Master of Orion 3_

---

### Post by cogadh on 2007-06-25
Starcraft probably won't work, it does require DirectX capable 3D hardware. 
There is an open source version of Transport Tycoon Deluxe that will run natively in Linux you may want to take a look at: [http://doc.gwos.org/index.php/Open_Transport_Tycoon_Deluxe](http://doc.gwos.org/index.php/Open_Transport_Tycoon_Deluxe)
DOSBox has a Linux version you could use for Master of Orion, it might be easier to do that rather than running through an emulator on a virtual machine.

---

### Post by kspn on 2007-06-25
Cool.

Thanks for that I will have a look (and do some struggling with wine to get my games working :))

---

