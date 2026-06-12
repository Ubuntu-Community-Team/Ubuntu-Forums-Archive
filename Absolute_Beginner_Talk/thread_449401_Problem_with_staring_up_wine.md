---
title: "Problem with staring up wine"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by IngetSikte on 2007-05-20
I have installed wine with apt-get. When I'm trying to start anything wth wine it says making configuration dir in my home dir and then it all freeze with 100% cpu load. It makes a .wine dir with the name something like: .wine-Ghe4sF. I have tried to just rename the dir to .wine and it result in a freeze with out any message at all when I'm trying to start anything. I have treid to reinstall wine too no success.

---

### Post by machoo02 on 2007-05-20
What version of wine are you using?

---

### Post by IngetSikte on 2007-05-20
I think it is Wine 0.9.37.

---

### Post by zvacet on 2007-05-20
I know it is stupid question,but did you after insrallation type in terminal

```
winecfg
```

---

### Post by Neenjah on 2007-05-20
I have the same problem.  I did winecfg like said above but didnt know any settings to mess with. I however did change it to windows xp.

---

### Post by IngetSikte on 2007-05-20
My problem is that I can't even write that without 100% cpu load. So I feel a bit stuck and no error messages :(

---

### Post by zvacet on 2007-05-20
Try** system>settings>wine configuration**

---

### Post by IngetSikte on 2007-05-21
I don't have that item in my menu: "system>settings>wine configuration"

---

### Post by Terl on 2007-05-21
> **IngetSikte said:**
> My problem is that I can't even write that without 100% cpu load. So I feel a bit stuck and no error messages :(

Don't try to start wine at all.  Open a terminal and type ```
winecfg
```.  If you are at 100% cpu load without opening wine and cannot type the command then there may be other issues.

---

### Post by IngetSikte on 2007-05-21
I get the same thing when I'm trying with winecfg and the same message: 
wine: creating configuration directory '/home/axel/.wine'...
but the ".wine" folder is not created, just the tmp dir ".wine-7PgldA".
And I have like 5% CPU load before I start wine/winecfg.

---

### Post by Terl on 2007-05-21
what happens when you type:  winefile

Try it in terminal.

---

### Post by IngetSikte on 2007-05-21
I get the same thing, doesn't matter which of the wine files I'm trying to start.

---

### Post by Terl on 2007-05-21
I think you need to remove wine through synaptic and try a reinstall.  Something is wrong.

---

### Post by IngetSikte on 2007-05-21
Yes somethng is wrong, the problem is to know what it is. I have tried to reinstall with --purge and all and still the same thing. Should I try to recomple the thing myself or is there any other things I should try?

---

### Post by Terl on 2007-05-21
I am honestly not certain what to do.  I have never had a problem getting it installed.  Forgive me if you've given this already, but what are your system specs?  Do you have a 64 bit processor or a 32?  

You may want to try asking at winehq also.  Since it is their main focus they could probably help much more quickly.

---

### Post by IngetSikte on 2007-05-22
I have 64 bits.
Core2 Dup, 2.16 ghz, 2gb ram, GF 8800GTS, Creative soundblaster. 
Idd, I tried to ask in their forum but got stuck in the register part since I never got the validation mail but I'll try again. I have never had any problems before either and it's hard to do something without any error messages at all.

---

### Post by Terl on 2007-05-22
I had a feeling... I recalled seeing something about wine and 64 bit....

Check this at wineHQ:  [Wine on 64 bit]("http://wiki.winehq.org/WineOn64bit")

And this on our forums by YokoZar:  [Wine of 64 bit arch]("http://ubuntuforums.org/showthread.php?t=431503")

I am unfamiliar with 64 bit architecture so I am of little help, sorry.  I recalled seeing these (I read too much :) ).  I hope they help.

---

