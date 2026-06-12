---
title: "No idea whats going on"
date: 2005-07-07
forum: Absolute Beginner Talk
---

### Post by Yoshiassasin on 2005-07-07
Well, I'm a Windows person. I admit it. But the problem is, Windows XP only lets you install it 3 times, and I exceeded that amount, trying to reformat my HD. Well, I couldn't live without a computer, so I did some research and came across Ubuntu. Extremely happy, I installed it into my PC and tried to connect to my network. Thats when I hit my first problem. I couldn't connect. I have a D-Link DWL G510 pci wireless card installed in my pc. so then I decided to connect via ethernet. I thought it would be relatively easy, but somehow it has become a wall I can't climb over. Would anyone be so kind to help me?

---

### Post by poofyhairguy on 2005-07-07
[QUOTE=Yoshiassasin]Well, I'm a Windows person. I admit it. But the problem is, Windows XP only lets you install it 3 times, and I exceeded that amount, trying to reformat my HD. Well, I couldn't live without a computer, so I did some research and came across Ubuntu. Extremely happy, I installed it into my PC and tried to connect to my network. Thats when I hit my first problem. I couldn't connect. I have a D-Link DWL G510 pci wireless card installed in my pc. so then I decided to connect via ethernet. I thought it would be relatively easy, but somehow it has become a wall I can't climb over. Would anyone be so kind to help me?[/QUOTE]

Well...I guess you have a choice now. I'll just stright shoot with you.

Choice A: Get Linux to work. I use Ubuntu on my desktop everyday. And I know why yours won't work- its the wireless network card. Drivers for many wireless network cards don't work under Linux. But there is a way:

ndiswrapper

this program uses the Window's driver in Linux. Many Ubuntu fans use it with success. Problem is that its kinda hard to do. High learning curve quickly for you. Without wirless right now I could tell you about neat ways to install Java or media codecs....but with the wireless card your barrier to entry is clear-

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

It has worked for some people. It can work for you. But it will take some work on your part that you don't have to do in Windows.

Choice B: You can pay the $20 or whatever it is for this program:

[http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)

Its an easy ndiswrapper basically. Make sure you email them and ask them if it will work before you buy though. Many people are happy with this. Its definately not as expensive as XP but its more so than ndiswrapper

Choice C: Buy XP. And OEM copy would probably suit you, froogle can help with that.

Choice D: (my favorite)  I personally fixed this problem but just running some cat5 cable (it was for my desktop though). The stuff is cheap. I kinda dislike wireless nowadays because it never impresses me with its speed (its usually not as advertised) and because the drivers don't exist for Linux and suck on other platforms (even in Windows and OSX I have wireless problems sometimes.) My wireless router has the wirelessness turned off, its my router now. I think this is the best way....but many (most) would disagree. 

In this plan you just run all the wires to together and have reset parties (what I call reseting everything) till it works. It will work_ does for me every day.

Chose what you like best.

---

### Post by Yoshiassasin on 2005-07-07
thank you for helping me.

Well, I decided to use Ndiswrapper, and I followed the directions, but I got to direction 7. and got lost. So what do you do? I went to networking settings, but I don't see anything that might be a wireless connection. all I see are the Modem Commection, and the Ethernet connection. 

And where do you find "edit /etc/network/interfaces" ? I can't find an edit menu anywhere.
thanks

---

### Post by aysiu on 2005-07-07
Don't forget about Choice E: Try another distribution.

Ubuntu is excellent for recognizing hardware, but it isn't perfect. Others that are worth trying are Mepis and Blag.

---

### Post by musicman2059 on 2005-07-07
Try this for that step in particular:

Open up a terminal window
cd /etc/network
ls (to see if there's an interfaces file)
sudo gedit interfaces  (replace gedit with your choice of editor, whether it be vi or whatnot)

---

### Post by Yoshiassasin on 2005-07-07
Ok, well I figured out a lot of things, one being that my driver that I had installed is invalid. So I went to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) and found my card and downloaded my driver, but I can't find an .inf file. Am I not looking hard enough? Or is there somewhere else I can find these drivers.

---

### Post by Shinitenshi on 2005-07-07
[QUOTE=Yoshiassasin]Well, I'm a Windows person. I admit it. But the problem is, Windows XP only lets you install it 3 times, and I exceeded that amount, trying to reformat my HD. Well, I couldn't live without a computer, so I did some research and came across Ubuntu. Extremely happy, I installed it into my PC and tried to connect to my network. Thats when I hit my first problem. I couldn't connect. I have a D-Link DWL G510 pci wireless card installed in my pc. so then I decided to connect via ethernet. I thought it would be relatively easy, but somehow it has become a wall I can't climb over. Would anyone be so kind to help me?[/QUOTE]

Yes only lets u install 3 times but if you get a hold of your compy that u bough it from they will give you information who to call. They can fix that problem or send u new cd no extra cost :)

Ya its a big hassle but if you are so dependent on windows why not do it.

---

### Post by Yoshiassasin on 2005-07-07
Ok, well never mind that. I found it, but it still says invalid driver. So now I'm trying to install the latest Ndiswrapper. 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
I'm at this site trying to figure out how to install it.  Under install it says "Go to source-directory". Where is that?

---

### Post by tjleeland on 2005-07-07
[QUOTE=Yoshiassasin]Well, I'm a Windows person. I admit it. But the problem is, Windows XP only lets you install it 3 times, and I exceeded that amount, trying to reformat my HD. Well, I couldn't live without a computer, so I did some research and came across Ubuntu...[/QUOTE]

Yoshiassasin,

While I don't want to discourage anyone from leaving MS, the fact is you can re-install Windows XP as often as you want. You may not be able to activate via the internet anymore, but if you call them you can activate over the phone 100 times if you need to. 

Just follow the instructions, and call the number that comes up after the error message that tells you your internet activations have exceeded the limit.

Then keep working on your linux.

---

### Post by Yoshiassasin on 2005-07-07
thanks. I have another problem though. I was searching other places on how to update ndiswrapper, and i keep seeing 

sudo make
sudo make install

If that is the key to installing this, then how and where are you supposed to type it in?

---

### Post by N'Jal on 2005-07-07
Ah right that's easy enough ok let's assume that this is my PC, this is were ndiswrapper would be

```
/home/neil/ndiswrapper
```

So look somewhere in there, within sub folders as well, for a makefile, you will know what a makefile is as that's what it'll be called.

So... you find makefile in /home/neil/ndiswrapper (it might not be but find where it is anyway)

type this into the terminal

```
cd /home/neil/ndiswrapper
```

Just to ensure you can see the makefile type 

```
ls
```

Ok so you can see the make file? Type

```
sudo make
```
```
sudo make install
```

I have never used ndiswrapper before but that's how to 'roll-your-own' source.

---

### Post by Yoshiassasin on 2005-07-07
Thanks N'Jal. I have finally installed ndiswrapper. But now there's another problem I have run into (man, this feels endless). Every time I try to install the driver that I need according to [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#D), I get an error saying it is an invalid driver. Anyone know of any other place I can get a D-link DWL G510 (the first one) driver?

---

### Post by Yoshiassasin on 2005-07-07
Ok, everything has worked out except the fact that every time I go to turn on my wireless network, the computer freezes. I have a light on my D-Link adapter, and its flashing like crazy, but the computer itself is frozen. The mouse won't move, keyboard won't respond. If you guys can give me another hint on how to work this I would appreciate it. Thanks.

---

