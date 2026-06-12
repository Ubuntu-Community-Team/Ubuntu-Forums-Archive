---
title: "over large screen resolution?"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by timveryan on 2007-11-18
Hello all.

I have in the last day installed ubuntu 7.10 on my new laptop (had got sick of vista!). I had already got used to using ubuntu on my old laptop over the last few months and installations on both machines went fine.

However on my new laptop there has been a slight complication. Everything on my screen is just too big really (i dont know the technical term, but the graphics are too big). This is especially the case on firefox.

i dont know enough to be able to describe this in the correct terms? but anyone willing to help i will do my best at providing you with the necessary info.

The only other possible problem and maybe related, is on my new machine there is a driver problem i believe? 

Atheros Hardware Access Layer (HAL) pops up as restricted driver, i dont know if this is linked?

please advise

tim

---

### Post by Qwerty_ on 2007-11-18
A screenshot might help to explain things to everybody.

---

### Post by banewman on 2007-11-18
An overlarge desktop is generally due to the video card driver not being installed.
Open synaptic package manager - it's under   applications-system-admin
click settings from the top menu then select repositories - and select all checkboxes except source code.
Then find "restricted driver manager" in the menu and select it - your cards driver should then be installed.
Then in the menu there is an option to change screen resolution - use that to get a better desktop.
Come back here if that falls short of expectations. :)

---

### Post by timveryan on 2007-11-18
thanx for advice, however in the synaptic package manager, all the boxes were already ticked apart from source code. and in restricted driver manager the only driver showing is that HAL i mentioned in my first post. and finally when i attempted to alter my screen resolution it would only go to mush!?

any more ideas would be great please!!

---

### Post by banewman on 2007-11-18
Hard to see from here :)
What is the video card pls?

---

### Post by Qwerty_ on 2007-11-18
Perhaps try and reconfigure your xserver (although I dont know how much that would help, again screenshot of your situation would be very helpful)

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by timveryan on 2007-11-18
ok guys, just tryin to get a screenshot up

---

### Post by banewman on 2007-11-18
You will need to know the video card so you can choose the right driver during the repackage. :)

---

### Post by timveryan on 2007-11-18
this screenshot of google i think particuarly highights it, the text looks all strained??

---

### Post by Qwerty_ on 2007-11-18
Right thanks for those images. I would say that the solution is to change your resolution. As Banewman stated above you are going to need to find out which graphics card you have so you can select the correct driver.

I think there is a command that should let you see that, ill see if I can find it.

---

### Post by timveryan on 2007-11-18
how would i go about finding what type of video card?

---

### Post by banewman on 2007-11-18
If you go to   applications - system - preferences - screen resolution  
it will tell you what size the desktop is - if it is 800X600 as the max then you need to find out what video card you have and install the right driver. Only solution I can see from here :)
To find the video card there is a menu option for hardware information - read through that.

---

### Post by Qwerty_ on 2007-11-18
Try having a look in.

System>Preferences>Hardware Information.

---

### Post by timveryan on 2007-11-18
thanx guys, i appreciate your help with this!! i have had a look in hardware info but dont really know what i am looking at? hope you dont mind but here is list of everything

---

### Post by timveryan on 2007-11-18
1 more

---

### Post by banewman on 2007-11-18
Couldn't see anything video related there...
Next - in a terminal type - 
lspci
and search for anything video - or if you dual boot see if you can find out from the windows OS?

---

### Post by Qwerty_ on 2007-11-18
lspci thats the command I was looking for.

---

### Post by banewman on 2007-11-18
qwerty - lspci | grep (what for video ?) that is what I'm looking for...

---

### Post by Rinzwind on 2007-11-18
Like this:

$ lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]

or

$ lspci | grep nvidia

See I have an ATI X300 ;)

---

### Post by banewman on 2007-11-18
Rinzwind - but what to type when the video card isn't known?

---

### Post by timveryan on 2007-11-18
hey guys, this is what i got on terminal, i cant see anyhting here and i dont dual boot.

---

### Post by Qwerty_ on 2007-11-18
It is there tim, VIA Chrome9 IGP

(third from the bottom)

---

### Post by timveryan on 2007-11-18
Excellent, well spoted!! what do i need to do now? find compatible driver?

---

### Post by Qwerty_ on 2007-11-18
Yeah have a look when reconfiguring your xserver for a driver for VIA cards, I think that would be the only way to find out.

---

### Post by timveryan on 2007-11-18
if you dont mind helping me just a bit more Qwerty_ how would i do that? i dont want to get it wrong. i appreciate your help.

---

### Post by Qwerty_ on 2007-11-18
This might help you.

[http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/)

---

### Post by overdrank on 2007-11-18
> **Qwerty_ said:**
> This might help you.

[http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/](http://www.hombrepac.com.ar/software-libre/linux/how-to-via-k8m890-chrome-9-igp-and-linuxs-xorg-ubuntu-edgy-610/)

HI and please be careful those instructions are for edgy, First backup your xorg
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Then search synaptic manager for via is should be install if you are using gutsy.

---

### Post by Qwerty_ on 2007-11-18
Gee thanks for pointing that out overdrank I did not notice they were for edgy when I had a quick squizz.

---

### Post by overdrank on 2007-11-18
> **Qwerty_ said:**
> Gee thanks for pointing that out overdrank I did not notice they were for edgy when I had a quick squizz.

No problem and I did not mean to intrude it is just there has been alot of black screens in gutsy as of late. :)

---

### Post by Qwerty_ on 2007-11-18
No thats cool I am at a loss really ive only used nVidia cards, which appears to just be easy compared to anything else.

---

### Post by timveryan on 2007-11-18
Thanx for your help guys. i havent solved the problem yet, but am gonna have to go and do some essay writing now. im at uni and instead of working on essay at my laptop, im installing new systems and reading forums!!). but thanks for all your advice and i will be back on here later further picking brains..

Tim

---

### Post by Qwerty_ on 2007-11-18
EDIT: Wrong tab in Opera.

---

