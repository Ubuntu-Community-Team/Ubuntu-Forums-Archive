---
title: "First login help"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by jerrycpny on 2008-02-10
Hi Ubuntu community.  I am a total newbie. I thought it would be cool to play with Ubuntu on an old laptop, and I'm kinda excited to begin to learn the whole linux thing.

After many attempts, I finally think I successfully loaded Ubuntu.  I ended up having to create a mini iso disc to get the computer to run the disc.

Anyway - On my first boot of my Ubuntu-loaded computer, I get teh login screen.  I think I successfully logged in.  

How now do I start the operating system?  After the "Ubuntu comes with ABSOLUTELY NO WARNING..." i get a prompt to enter something after jerry@ubuntujerry:~$

What now.

Thanks

Jerry

---

### Post by jrusso2 on 2008-02-10
Your running off the live cd?  It sounds like you don't have a gui.  Is there just a black screen with a command prompt?

---

### Post by overdrank on 2008-02-10
> **jerrycpny said:**
> Hi Ubuntu community.  I am a total newbie. I thought it would be cool to play with Ubuntu on an old laptop, and I'm kinda excited to begin to learn the whole linux thing.

After many attempts, I finally think I successfully loaded Ubuntu.  I ended up having to create a mini iso disc to get the computer to run the disc.

Anyway - On my first boot of my Ubuntu-loaded computer, I get teh login screen.  I think I successfully logged in.  

How now do I start the operating system?  After the "Ubuntu comes with ABSOLUTELY NO WARNING..." i get a prompt to enter something after jerry@ubuntujerry:~$

What now.

Thanks

Jerry
HI and welcome, it sounds like you installed without a desktop environment ( server) what do you get when you use the command startx?

---

### Post by spiderbatdad on 2008-02-10
sound like server edition?

---

### Post by jerrycpny on 2008-02-10
Thanks very much for the replies.  I hope I am not wasting everyones' time here.  gui?  Yes there is a black screen with command prompts.  And = yes I probably installed it withought a desktop environment since I don't even konw what that means.

Should I quit?  Do I need to be more software-fluent to run a linux os?  I thought I was pretty good around a computer before this undertaking.

---

### Post by overdrank on 2008-02-10
> **jerrycpny said:**
> Thanks very much for the replies.  I hope I am not wasting everyones' time here.  gui?  Yes there is a black screen with command prompts.  And = yes I probably installed it withought a desktop environment since I don't even konw what that means.

Should I quit?  Do I need to be more software-fluent to run a linux os?  I thought I was pretty good around a computer before this undertaking.

Hi and if you have a internet connection then you can try the command ```
sudo apt-get install ubuntu-desktop
``` or kubuntu or xubuntu if you prefer.

---

### Post by spiderbatdad on 2008-02-10
> **jerrycpny said:**
> Thanks very much for the replies.  I hope I am not wasting everyones' time here.  gui?  Yes there is a black screen with command prompts.  And = yes I probably installed it withought a desktop environment since I don't even konw what that means.

Should I quit?  Do I need to be more software-fluent to run a linux os?  I thought I was pretty good around a computer before this undertaking.
 Not at all. Ubuntu is for noobs...like us. You'll get it. And you'll love it.

---

### Post by jerrycpny on 2008-02-10
> **overdrank said:**
> Hi and if you have a internet connection then you can try the command ```
sudo apt-get install ubuntu-desktop
``` or kubuntu or xubuntu if you prefer.

You guys are the greatest.  

Overdrank - that command tried to install something.  Now I'm at "Unable to fetch some archives.  Maybe run apt-get update or try with fix-missimg"

I'll keep with it as long as there are dudes like you out there.

---

### Post by overdrank on 2008-02-11
> **jerrycpny said:**
> You guys are the greatest.  

Overdrank - that command tried to install something.  Now I'm at "Unable to fetch some archives.  Maybe run apt-get update or try with fix-missimg"

I'll keep with it as long as there are dudes like you out there.

Hi and try the commands 
```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by jerrycpny on 2008-02-11
> **overdrank said:**
> Hi and try the commands 
```
sudo dpkg --configure -a
sudo apt-get install -f
```




As always - thanks very much

---

