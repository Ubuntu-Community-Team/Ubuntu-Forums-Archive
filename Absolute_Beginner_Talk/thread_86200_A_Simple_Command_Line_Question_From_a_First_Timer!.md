---
title: "A Simple Command Line Question From a First Timer!"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by Simimi on 2005-11-04
So Ubuntu is the first Linux I have ever used, I'm liking it! Gaim is fun, though I can't seem to find out how to enable Custom Emoticons... I love how it supports all the languages I need, though the Thailand keyboard is hidiously off, but that's fine...I am running a 233Mhz processor, so I am using the GNOME GUI, because I am afraid Kubuntu would kill it!
My Questions Are-->
 My friend who has been on Linux since forever told me some commands and such, but some of them don't work...Mainly lynx to use the internet inside the terminal. I can't man lynx or man links or man linx? How do I use the internet inside the browser?
 I had a huge issue with trying to download and gunzip and compile and make and...*dies* a program, it seems everything is so much harder in Linux than Mac OSX.. but that is clearly because I'm new! But I want to learn!
  More Questions-->
1)How do I serf the internet inside the terminal? (lynx? It is not working. could be my error though!)

2)How do I get the "redness" out of the GUI? It looks kind of ..ew with my background, I would just like to make my toolbars blue, I guess that would be all.

3)My friend showed me this... is it "Fluxbox" or... "Flexbox"? It was like a new GUI and it had nothing on it...just little popup windows on the background. Can I use that with my Gnome? Or do I loose the Gnome to get the flexbox? Will it work for Ubuntu? Eek, so confused... I'm wanting to kind of get the usage of linux (it IS alot of fun to playwith...) but I want to most bang for my little POS Box, :)

4) I tried to sudo ap-get install kubuntu-desktop and it does 2 things and then tells me E:(something to the effect of you can't do that, I don't recall the exact wording..) What is going on in this situation? It did the same for trying to get kubuntu-core too!

5) How do I make the default movie player program work? For some reason my Ubuntu will not play any media, it says it does not have drivers or codecs...I mean nothing- no *.mp3 or *.dat or CD audio files, no *.wav ... Is this my own error or just something I have to enable or..?

 Thanks for all your help in advance.. I know i said only 1 question, but as I thought about it, I had a few more! Add a tallymark to one more for The People's Revolution!
  Yours, Simimi
    Recent Convert- Humankind Empire of MAC to The United People's Revolutionary Forces

---

### Post by Kyral on 2005-11-04
For basic terminal knowhow *Points to the first link in his sig*

For stuff like MP3s
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Fluxbox is a Window Manager (If you really want me to explain just ask). I think you can use GNOME with it... or standalone

"Redness"? I'd need to see a screenshot to even understand this one ;P

---

### Post by aysiu on 2005-11-04
These links should be helpful to you in general:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

Specifically, you can ```
sudo apt-get install lynx
``` I don't think that it comes with the default install of Ubuntu. Likewise, you may have to install Fluxbox as well. If you're not sure of the name of a program, you're probably better off using Synaptic Package Manager instead of apt-get.

For changing colors, I don't know what you're talking about. You can attach small screenshots to your messages on these boards.

When you get error messages, always post the exact error you get (copy and paste)--don't just describe the error.

**Edit**: Kyral beat me to it. The support is just too good on these forums.

---

### Post by Simimi on 2005-11-04
Sorry hee the readness is my monitor... the grayscale tabs and toolbars and the default ubuntu background just is not pleasing to my eye...so I'm trying to make the toolbars blue.
 Thanks so much for your help! And please do explain what a window manager is...I am truly truly new to everything Linux, but it is just so darn cute i can't put it down!

Well I am not at my Ubuntu box but I will post the screen as soon as i get back to it. I am notsure if i want to get fluxbox since i don't know what it is.. and I hope I did not give the impression of not having looked for an answer first, because I did...
 I will post the error message as soona s I get back to my ubuntu box, so sorry for the inconvenience.

---

### Post by Kyral on 2005-11-04
*Enters Technical Jibberish Mode*

Okay, yanno how on Linux the GUI is something completely seperate from the OS (ie, X crashes it doesn't take down the OS with it....most of the time)

Well it gets even more separate. Technically all X does is manage the GUI. Early implementations of it were just ways to just multiple terminals open on one screen (TWM). So the Window Manager was born. It does exactly what it says. Technically it only controls the way the windows are drawn and what they look like and stuff like keyboard input (which is why your keyboard shortcuts don't carry over from GNOME to KDE to XFCE unless you "hardcode" them into X using a program like xkeybind). Examples of Window Managers are FluxBox, BlackBox, OpenBox, MetaCity, IceWM, FVWM, Sawfish (really old), XFWM, and Enlightenment. Notice I didn't say GNOME or KDE or XFCE. GNOME, KDE, and XFCE are "Desktop Environments". They provide the cool stuff like panels and toolbars and stuff. GNOME itself doesn't have its own WM, which is why it is usually paired with Metacity. KDE uses its own bundled WM which I think is called KWM, and XFCE uses XFWM. In GNOME you can swap out Metacity for something else (a popular choice here on the Forums seems to be Openbox or Enlightenment, with the latter being referred to as "Enlightened GNOME"). I mentioned that Enlightenment is a WM, however with Enlightenment 17 (more often referred to as "E17") it seems to be moving to become more like a Desktop Environment.

I hope that cleared things up

---

### Post by aysiu on 2005-11-04
Wow, Kyral! Thanks for that explanation. I finally understand. I never got before what the difference was between a window manager and a desktop environment.

---

### Post by Simimi on 2005-11-04
I -think- I understand. I'm just trying to make my desktop a bit more enjoyable to browse through and such, exploring my options. Wow I have been using Linux for.. 2 days and I already know whata "window Manager" is... I feel so enlightened now.
Also, I ran down to my UbuntuBox and got these for you!
The Errors!
Me- sudo apt-get lynx
Password:
E: Invalid operation lynx

Me- sudo apt-get install kubuntu-desktop
Password:
Reading package lists... Done
Reading dependency tree... Done
E: Couldn't find package kubuntu-desktop

 I hope that helps?
  I am still not so clear on the window manager thing, but your explination was great! I went to the fluxbox website, the screenshots are wonderful... Is the window manager like a Linux-Konfabulator?
 Thanks again for everything!
And what is 'X'?
  Simimi

---

### Post by aysiu on 2005-11-04
[QUOTE=Simimi]
Also, I ran down to my UbuntuBox and got these for you!
The Errors!
Me- sudo apt-get lynx
Password:
E: Invalid operation lynx[/QUOTE] I'm not sure if you even know how to install software. It should be ```
sudo apt-get install lynx
``` not ```
sudo apt-get lynx
``` Generally, though, it sounds as if you're trying to tackle too much at once without really understanding things. Please read this link:

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

The best way to get to know your system and tweak it as you want is to solve one problem at a time. It sounds as if you have a million things you want to do all at once.

---

### Post by Simimi on 2005-11-04
Yes...that is exactly right, I just got it for the first time and I am very overly excited, I'm sure you can understand...Ok I am reading the link right now!
 Thanks again for all your help!
Now back to the drawing board!

And...
E:Program lynx has no installation candidate
 Hmm...wierd...must learn more about....linux...

---

### Post by Kyral on 2005-11-04
For the first one the syntax to apt-get is 

```
apt-get <action> <package> <option>
``` 
Package is self explainitory, Action is usually "remove", "install", "update", or "upgrade" (for update and upgrade you don't have to specify a package). Option is a bunch of fun stuff that modify Apt's behavior. The most commonly used one is -s, which simulates the action. So if you want to know what WOULD happen if you did something, use -s.

Of course you need sudo in front of it.

So to install Lynx, you'd need

```
sudo apt-get install lynx
``` 
For the Kubuntu-Desktop part, do you have the Universe and Multiverse open? Aysiu has a good link in his sig for that.

X is the underlying thing that makes all the graphical stuff aside from the Virtual Terminals possible. Its really called the X Windows System or the X Server (forgot), and right now there are two different variations on it, X.Org and XFree86, which is one of hte main differences between Debian and Ubuntu right now (Ubuntu using XOrg, Debian using XFree86), but its commonly referred to as just X. 

And whats a Konfabulator (Man I've been outta the Windows world for a long time :P)

EDIT: Aysiu beat me to it this time on apt ;P

---

### Post by Simimi on 2005-11-04
Konfabulator is this tool for use inside Mac that lets you trick it out and make it look like virtually anything you want, very fun tool to play with!
  Also, I was just thinking about using kubuntu, but I'm afraid my little old POS Box wouldn't want to run it, and I already have my GNOME settings to thai and such...I think I will stick with it for now, until I learn it some more.
 I won't even ask about networking to windows XP...

E:Program lynx has no installation candidate
  Does this mean no lynx for me?

---

### Post by Kyral on 2005-11-04
GDesklets could be used to add things like monitors and starterbars and whatnot, but some have memory issues...

Look in Synaptic for addons to the GNOME Panel, there are some pretty good ones. One thing that I love about the way Linux handles GUIs, is since X pretty much only acts as a layer between the GUI and the Kernel, you can do almost ANYTHING with the GUI. I mean, look at Mezzo which SymphonyOS is rolling out. Its just a matter of knowing how to customize :D

---

