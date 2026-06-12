---
title: "virtual pc ubuntu problems"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by sandbagger on 2006-07-14
Hi everyone.
I am trying to convert from win xp to ubuntu and have been running into a few problems. I am starting with a copy of virtual pc so I can still use internet on xp when I have trouble (ie: now).
I have installed ubuntu with a downloaded live cd and am up to the login screen. The screen is now all distorted so I can't really see what is displayed properly. After a bit of googling, I discovered a fix for my problem here [http://weblogs.asp.net/pscott/archive/2005/10/13/427426.aspx](http://weblogs.asp.net/pscott/archive/2005/10/13/427426.aspx) but that only lead to more problems. He says to go to /etc/X11, which i could do easily enough despite the distorted screen, and open xorg.conf using pico.
Pico is apparantly not installed on my machine but I can still open the file with gedit. However it opens in read only mode and I can't make the change I need to.
I am a complete noob with linux but I am determined to make the switch even if it kills me. Any help anyone can give would be much appreciated.

---

### Post by maniacmusician on 2006-07-14
do you have ubuntu installed? as in, did you set it up and stuff? did you set a username and password? if so, open a terminal, and type this:

sudo gedit /etc/X11/xorg.conf

tell us how it goes

---

### Post by sandbagger on 2006-07-14
Yes. I have it installed and can open programs and stuff. It is just really distorted so I can barely make out the words, and I have to go back to windows and slide the scroll bars in virtual pc to see the whole screen.
You might have to guide me on how to "open a terminal". Like I said, I'm a noob.
Thanks for the quick reply by the way.

---

### Post by maniacmusician on 2006-07-14
well we were all noobs at one point. hahahah i'm still a noob. i've been at it for a few weeks. um there should be a button on the top left or bottom left of your screen with a menu attached. terminal (or maybe Konsole) should be in there somewhere. It depends on which distro you have. I have Xubuntu and its like the 4th thing down in the menu. Gnome and KDE (aka Ubuntu and Kubuntu) probably have it in different places

---

### Post by sandbagger on 2006-07-14
Ok. I found terminal, and typed the command.
The first time it asked me for a password. I assumed it was asking for my login password which I entered.
Now I get the gedit window with a blank page. I think i must have done something wrong.

---

### Post by maniacmusician on 2006-07-14
most likely, it is that you typed the command in wrong. it is case sensitive so make sure everything is capitalized correctly.

sudo gedit/etc/X11/xorg.conf

---

### Post by sandbagger on 2006-07-14
ahhh. I had a lower case X in X11. I have so much to learn :)
Now I just have to get it hooked up to the net. I'll do a bit of googling before I start bothering people here again on that subject.
Thanks for the help. Now that I know about the terminal window I should go a bit better.

---

### Post by maniacmusician on 2006-07-14
awesome! glad you're getting used to it. It's a lot different from windows, but not any harder. you just need time to learn.

welcome to linux

---

### Post by FredB on 2006-07-14
MS Virtual had a bug which cannot make it possible to boot X in something better that 16 bits display.

Try [VMWare Player]("http://www.vmware.com/products/player/") + [this image of Ubuntu 6.06 LTS]("http://www.vmware.com/vmtn/appliances/directory/484"), it will give you a better training ground !

My 0.02$ of course :)

---

### Post by maniacmusician on 2006-07-15
mm I'm actually thinking of installing Xubuntu on my fast computer and then running windows on VMWare Player. I'm guessing the answer to this is no, but there couldnt possibly be a way to get a configured image of XP? hopeful thinking at its best

---

