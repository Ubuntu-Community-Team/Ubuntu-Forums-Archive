---
title: "One problem done...more to go"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by tyboon on 2007-03-27
So..it seems i finally made it...still..one last thing...
I have an Lg-L204WT model 20"+ and that seems to have been the problem...i am working now linux but on my old monitor...
does anybody knows how i could calibrate my Lg ...
Its getting crowded on my desk...i d rather use one monitor..
Good news is tha the Xp's are history to me..
Please guys help me out with the Lg..do i need to find a driver or something..It works on 1600 by 1050 ....
Anybody knows anything..:confused:

---

### Post by z_diver on 2007-03-27
Not sure I understand what you mean by 'calibrate the lg' but if what you want to do is tell Ubuntu to use the maximum resolution it knows of for your monitor and video card combination, this command run from the console should do just that.
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by tyboon on 2007-03-27
i just installed it..i dont know where to find the sudo comand..even if i find it how i am supposed to adjust it..i use now my old monitor..i even tried them together..my old one works on maximum resolution 1280 by 1050..an the Lg is all scrumbled..
I really appreciate though..its just that i use ubuntu  like 1 hour now..not really sure what i am doing and how things work...
I am really a beginner..
can you tell step by step..
I would really appreciate...
Thanx

---

### Post by chili555 on 2007-03-27
Hook up the LG. When the display goes nuts, after it's all booted up, press CTL-Alt-F1. You will get a cool old-school black screen with white letters and a command prompt. Log in, give your password and enter the command:```
sudo dpkg-reconfigure -phigh xserver-xorg
```A little utility will come up that asks you to reconfigure your display settings. Try to find a generic LCD that does 1600x1050. Tab to OK (you will probably have no mouse) and when you get back to the command prompt, type sudo reboot. Your display should love you now.

sudo is always a command in a terminal: Applications -> Accessories ->Terminal. It means, approximately, I want to DO a command that requires Super User priveleges. sudo!

Post back if you need more.

"sudo Honey, please bring me a cold brew."

---

### Post by tyboon on 2007-03-27
Maaaaaaaaaan ........... it seems so simple..i wish it will work :guitar: ...
one last thing...
I am booting from my slave..i cant see the master where Xp and all my files  are located..
Iluminate me...
Pleazeeeeeeeee .........
Thanx
:)

---

### Post by tyboon on 2007-03-27
i tried but the keyboard goes dead..cant write my passwrd.any suggestions..?
Other keyboards do the same..
Whats the deal?????????
Any suggestion?
I would real appreciate...
Thanx ...

---

### Post by z_diver on 2007-03-27
> **tyboon said:**
> i tried but the keyboard goes dead..cant write my passwrd.any suggestions..?
Other keyboards do the same..
Whats the deal?????????
Any suggestion?
I would real appreciate...
Thanx ...

You won't see any password.  That's the typical console method of hiding passwords.  When you use sudo and are asked for a password, it will want your password and you should just type without worrying whether the keyboard is functional.  It will be. Hit enter at the end and the command will run.  ;)

Give that a shot and post back.  I'm following this thread and will help you.  It really is a very simple task that has some funny methodolgy.  No worries though, we'll get it going.

---

### Post by tyboon on 2007-03-28
Thanks man..
I ll keep trying ..see what happens...hope it will work...
keep an eye on the thread just in case..
:guitar:

---

### Post by tyboon on 2007-03-28
it says that xorg file is not installed...
any ideas..

---

### Post by chili555 on 2007-03-28
```
sudo apt-get install xserver-xorg
```Accept any dependencies.
Try:```
sudo dpkg-reconfigure -phigh xserver-xorg
``` after Ctl-Alt-F1 and with the LG attached.

Are you sure you typed the command exactly correctly? It's hard to imagine any system, except the server edition, getting installed without xserver-xorg.

---

### Post by tyboon on 2007-03-28
oem@ubuntu:~$ sudo apt-get install xserver-xorg
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
oem@ubuntu:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070328185723
oem@ubuntu:~$ 

this is what i got so far..
I am going to try ctrl+alt+f1..
follow the thread please..

---

### Post by tyboon on 2007-03-28
this is what i got...i get this from the terminal or tha black screen..any suggestion?????

oem@ubuntu:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070328184938

---

### Post by Rhubarb on 2007-03-28
What version of Ubuntu are you running there?
Dapper Drake 6.04?
Edgy Eft 6.10?
Feisty Fawn 7.04?  (this is currently in Beta)

In Feisty it won't give you the option to specify what resolution you want if you use:
sudo dpkg-reconfigure -phigh xserver-xorg

It's a bit more messy, but try typing this in instead:
```
sudo dpkg-reconfigure xserver-xorg
```

I haven't run this myself in Feisty, but in Edgy + Dapper it asks many questions, like what keyboard language do you use, screen resolution, bit depth, etc.

---

### Post by tyboon on 2007-03-28
i use the 6.10 probably this one..Edgy Eft 6.10.. i downloaded it the day before..really dont know what to do..may be i ****** something up..

---

### Post by tyboon on 2007-03-28
i finally got to use my Lg monitor using the codes you provided...but i use the vesa xserver and only in 1024 by 768 resolution , unfortunately although i found the ATI and also found the 1680 by 1050 resolution i had again the same problems...
could anybody suggest something?

---

### Post by z_diver on 2007-03-28
> **tyboon said:**
> i finally got to use my Lg monitor using the codes you provided...but i use the vesa xserver and only in 1024 by 768 resolution , unfortunately although i found the ATI and also found the 1680 by 1050 resolution i had again the same problems...
could anybody suggest something?

I think it may be best that you use the closed source ATI drivers.  I think EasyUbuntu might be the easiest methond to install those.  Since you are new to Ubuntu and linux in general, you'll find it to be a helpful tool.  Here is a link to the their page.  [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

Once there you should click the download "here" at the bottom of the page and then go ahead and download the alpha deb from the next page.  Don't worry about the developer stuff further down.  Won't need that, but you will want to run the command they list to add the gpg key to your system for further upgrades.

Once you have the tool installed, under "System", you will find a checkmark for the ATI driver.  That should help tremendously.  The open source drivers are OK too but for standard resolutions only and no fancy xgl.  1600x1050, although somewhat standard isn't supported as well in OS as in the closed source driver.

Try that and let us know how it goes.

---

