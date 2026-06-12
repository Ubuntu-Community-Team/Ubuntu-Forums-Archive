---
title: "exe files"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by rodney3 on 2006-12-19
Is it possible to use .exe files (for games, programs, etc..) in Edgy?

I'm not too familiar with the command prompt, so normal English would be great. lol


Thanks

---

### Post by iPirates on 2006-12-19
Check this out:

[http://www.winehq.com/](http://www.winehq.com/)

To my understanding ( i'm just learning too ), it's a program that allows you to run windows applications in Linux OS.

---

### Post by jvc26 on 2006-12-19
Take a look at wine it allows you to use some of your windows apps in ubuntu. (See post above for link) It does not run every application or game, so you'll have to have a look round to see if it supports the app/game you want to use.

---

### Post by rodney3 on 2006-12-19
Ok, another problem.
I just installed Ubuntu today and I haven't configured the wireless network settings. I was told to download ndiswrapper; however, I don't really know how to install it with the command prompt type program. Any tips? I have the Linksys WMP54G with the Broadcom chipset

---

### Post by jvc26 on 2006-12-19
Have a look at
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)
or maybe this one
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)
Don't have wireless myself, but those two may point you in the right direction.
Il

---

### Post by rodney3 on 2006-12-19
Those are the same two links. lol

---

### Post by jvc26 on 2006-12-19
Gutted. must've not copied the second properly... 1 sec:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)
thats the other I think.
Il

---

### Post by iPirates on 2006-12-19
Another windows application running program (for gaming) is Cedega.

[http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1](http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1)

Wine is apparently available in the Synaptic Package 
manager, but Cedega you'd have to download.

---

### Post by jvc26 on 2006-12-19
Wine is available via synaptic as iPirates says (if you have 32bit ubuntu):
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)
Enjoy! :)
Il.

---

### Post by ]Nbx*cmD[ on 2006-12-19
anyway... in my opinion it's a bit nonsense using wine and cedega, since you came to ubuntu you should make yourself the idea now you OS doesn't know what an EXE file is.
Now yours is a free system, so it will get veeeery angry if you ask it to emulate window$ behaviour :P
You know, this is like if a Mac user said "Oh! I can't run exe files!" You'd answer: "You don't need to, Mac has great programs which will do the thing". That's the same in free (as in freedom) software, the idea is 'don't try to trick but to find a free alternative' ;)

---

### Post by iPirates on 2006-12-19
Hah, very good point.  

But what if you want to run computer games?  

I only recently starting using Ubuntu, and after using it for about a week, I can't believe I didn't switch over sooner!  
However, I configured my system to dual boot between XP and Linux so that I would be able to continue playing computer games.  
Ideally, I would like to just run ubuntu, so if there's any way to make games work in the linux OS besides Cedega or dual booting, I'd take it!  However, those are the best options I can find so far.

---

### Post by dorcssa on 2006-12-19
[http://www.ubuntuforums.org/showthread.php?t=321165&highlight=linux+games](http://www.ubuntuforums.org/showthread.php?t=321165&highlight=linux+games) <--some native linux games. But for windows games(which are using directx), there's no alternative, you have to use cedega or wine. Or continue dual booting, as many do for this reason. ;)

---

### Post by Perfect Storm on 2006-12-19
Check my sigs for linux games.




[quote=]Nbx*cmD[]anyway... in my opinion it's a bit nonsense using wine and cedega, since you came to ubuntu you should make yourself the idea now you OS doesn't know what an EXE file is.
Now yours is a free system, so it will get veeeery angry if you ask it to emulate window$ behaviour :P
You know, this is like if a Mac user said "Oh! I can't run exe files!" You'd answer: "You don't need to, Mac has great programs which will do the thing". That's the same in free (as in freedom) software, the idea is 'don't try to trick but to find a free alternative' [/quote]

Wholehearted agree. 

Just look for the linux alternative out there. If you can't find it don't hesitate to ask on the forum :KS

---

### Post by jvc26 on 2006-12-19
Yup you're right I'd have to agree with finding open source apps for use in linux, but to answer the question about .exes wine was the answer. There are a lot of alternatives out there definitely worth a look.
Il

---

### Post by ]Nbx*cmD[ on 2006-12-19
For linux games you can fill up your apt repositories with some cool ones and then:

```

apt-cache search game | grep arcade
apt-cache search game | grep 3d
apt-cache search game | grep ...

```

I've found really good ones.
You can also visit [www.linux-gamers.net](www.linux-gamers.net) !!
Oh btw, did you try openarena? It's a free implementation for Quake III Arena, which code has been relased as opensource some months ago

---

