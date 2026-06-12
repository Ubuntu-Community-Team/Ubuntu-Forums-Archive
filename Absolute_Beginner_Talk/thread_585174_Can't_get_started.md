---
title: "Can't get started"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by davidexe on 2007-10-21
I am experienced in DOS and Windows. I just downloaded the Ubuntu server software to set up a server. I downloaded the program from Ubuntu, downloaded the CD Image writer. Wrote the CD. Installed on a blank hard drive and got the "black" screen of "what do I do now?" I printed out the Starcraft.Man complete guide and got the alt+F2 to give me the prompt as he said. Then nothing.  I cannot load the terminal. Is there more that has to be downloaded? Any help is appreciated.

---

### Post by forestpixie on 2007-10-21
when you say you've got to the "black" screen of "what do I do now?" - do you mean it's installed and you've got a command prompt?

Cos if that's so - that's what you installed - the server hasn't got a GUI - if you want that you need ubuntu-desktop I believe, which you can install from the prompt.

---

### Post by LanDan on 2007-10-21
eeuuuh what did you expect?

if it is asking for your log in then you're in the right place. ofcourse you can install a lot of stuff you don't need by installing a desktop but that is completely not needed for a server.
if you wonder what to do then the link below might be a nice start
[http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)


have fun

---

### Post by davidexe on 2007-10-21
When it finished installing I got the absolute black screen. With the alt+F2 I got some information and the command prompt. That is all.  The only thing I can get to work is the aptitude.  
Is there any instruction set that walks through how to get from the initial black screen of the server software to being able to do something?  If I have to download the GUI, how do I do that?
I have seen nothing that indicates that it is connected to the internet. It is connected to the LAN and should have access. It did in Windows.

I downloaded the manual from the Ubuntu site but it looks like it is really for the desktop version?

---

### Post by davidexe on 2007-10-21
Is there a way to print out the entire guide? I didn't see anything except walk through it on the screen.
Thanks,

---

### Post by forestpixie on 2007-10-21
I'm sorry but I know next to nothing about the server edition. If you have to install the desktop you can use aptitude

```
sudo aptitude install ubuntu-desktop
```

but I wouldn't be able to tell you if server has even installed properly or not

---

### Post by LanDan on 2007-10-21
try
wget -r [http://doc.ubuntu.com/ubuntu/serverguide/C/](http://doc.ubuntu.com/ubuntu/serverguide/C/)

and you will know if your internet connection is working right away ;)

[http://doc.ubuntu.com/pdf/ubuntu/C/serverguide.pdf](http://doc.ubuntu.com/pdf/ubuntu/C/serverguide.pdf) if you want some sofa reading

---

### Post by HermanAB on 2007-10-21
Ubuntu Server is meant for use in Data Centres where machines don't have screens and keyboards, since they are administered remotely over SSH.  If you wish to have a system with a screen and keyboard, then get regular Ubuntu or Xubuntu.

If you are a pointy-clicky-diehard, then even Ubuntu is probably not for you and you should look at Mandriva 2008 instead, since Mandriva has wizards for everything.  Mandriva is still the only Linux distribution where you really don't ever have to use the command line: [http://torrent.mandriva.com/public/](http://torrent.mandriva.com/public/)

Deep down, all Linux systems are the same, so what you learn on one system is generally also applicable to any other Linux system and even transferable to a Mac, BSD or Solaris system - which are just enough different to be annoying.

Cheers,

Herman

---

### Post by LanDan on 2007-10-21
why is everybody implying he should get a desktop installed?

i'm sure he did not download the server version because he wants to watch youtube and as he said he is experienced with DOS so he is a big guy


what do you mean by datacenter? some people actually have a server at home for file sharing their own website or even e-mail etc....

---

### Post by davidexe on 2007-10-21
I have a 5 person engineering company and am in the process of integrating 3 other companies at 3 different locations. I have run peer to peer and WAN for 15 years doing what I had to myself. I am a keyboard/command oriented individual. 

I do not want to be captive to some IT individual as I have seen the other firms do.  So, I am in the process of setting up a small (15-45 person) LAN that will be the intermediate step to having a full blown system when we get to about 35 stations or more at one location. 

In order to do that I have to set up a formal LAN, beyone Windows XP PRO and short of a dedicated point and click managed by some IT. It appears that LINUX is a reasonable option.

But, having absolutely no experience with LINUX, I get to start all over. Having done it when you had to set the interupts on the jumpers on the individual LAN cards to now, I have a fair degree of familiarity with the various aspects. But LINUX has its own unique set of buzz words and commands. So, the problems is where do you snip the corner to get inside just a little. 

I think I have found that with what I have found here and the manual. The Ubuntu Server Guide appears to be the main thing I need now.  So, now I will retire (and I AM old enough as I am on SS) to the sofa and digest what I can of that guide.

Many thanks for the inputs and help.  In the more distant past (BI - Before Internet) I just had to hammer at it long enough till something gave. Now it is just to give a little yelp for help and there are numerous fantastic people willing to extend a hand and info.

Regards,
A New LINUX user.

---

### Post by LanDan on 2007-10-21
that guide is just the tip of the iceberg but its a nice way to get started

and i can vouch for the fact that command style Linux is what gave it its good name and isn't that difficult once you get used to it.
if you want to set up a server that can be managed with point and click dont set up a desktop but use something like webmin or ebox.

personally i stay away of anything graphical on a server because what isn't there can not break and using the command line shows you so much more flexibility

but then again...linux gives you the choice so you decide.

have fun.....

---

