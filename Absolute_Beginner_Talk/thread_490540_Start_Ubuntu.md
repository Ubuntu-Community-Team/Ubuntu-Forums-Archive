---
title: "Start Ubuntu?"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-02
Hi.

I once had it so that i could choose if i wanted to use windows or ubuntu. Now i re-installed windows and i can't choose to start ubuntu. How do i do so that i can start ubuntu?

I've also got some other small problem that i also would like you to help with:

1.
Why cant i download the package so that aMSN works?

2.
I once had so i could change between workspaces on a cube, now i can't do that anymore even if i undo desktop effect and then set effects on again.

I know its a lot to ask, but please help me :)

---

### Post by Seisen on 2007-07-02
To answer the first question, you need to reinstall Grub

[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by Raineer on 2007-07-02
[This]("http://www.ubuntu.com/getubuntu/download") tutorial will help you reset what's called "GRUB" to get your dual-boot working again. It says it is for Vista but it works fine with XP.

Windows does not like to have any OS friends, it will not allow a dual-boot so you always install it first. 

Don't know about #1, I'm not an MSN fan. Do you know the name of the package you want?

For #2, try opening a console window (or pressing Alt-F2) and typing:
```
compiz --replace &
```
And seeing if that brings your cube back, if it says not found then I'm not 100% sure how to help. You could possibly remove and reinstall the "desktop-effects" package through Synaptic.

---

### Post by skymera on 2007-07-02
i have dual boot...
i messed up my GRUB by reinstalling windows.
i added the Ubuntu entry to windows OS selection
and windows to Ubuntu OS selection..

so whatever happens i can choose ubuntu or 'the toher one'

i forgot the link. sorry

---

### Post by Pragmatist on 2007-07-02
> **czepluch said:**
> Hi.

I once had it so that i could choose if i wanted to use windows or ubuntu. Now i re-installed windows and i can't choose to start ubuntu. How do i do so that i can start ubuntu?

I think the Windows boot loader is now booting your machine.  You probably want to use GRUB instead:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

> **czepluch said:**
> 
1.
Why cant i download the package so that aMSN works?

I don't think you can do that, but I'm not completely sure.

> **czepluch said:**
> 
2.
I once had so i could change between workspaces on a cube, now i can't do that anymore even if i undo desktop effect and then set effects on again.

Are you using Beryl?

---

### Post by czepluch on 2007-07-02
What is beryl?

Is it easy to install GRUB?

---

### Post by lamalex on 2007-07-02
There is an option to enable the cube, do you have it selected? You may need to install compiz-manager-gnome. and for grub, the second reply in this thread is howto

---

### Post by skymera on 2007-07-02
hmmm i had trouble with my GRUb is was being queer.

beryl however is just another windowe manager.
not just any windows manager!!!!
it allows wobbily windows, desktop cubes.

and many many more!!

ww.beryl-project.org

should bve the site.

GOOD LUCK! with your GRUB.

---

### Post by czepluch on 2007-07-02
Hmm.

I will try the GRUB thing, but i haven't got the CD with ubuntu right here where im at. I am at a friend.

And thanks for the tip with workspaces

---

### Post by czepluch on 2007-07-02
Can i just download and burn the CD here ?

---

### Post by jordanmthomas on 2007-07-02
If it's only the cube and not wobbly windows you're having troubles with, try this:  

To fix your problem with beryl, try right clicking on your workspace item on your panel and going to preferences.
Set the number of workspaces to 1.  Then, clicking it should rotate the cube like you expect.  I'm not sure why it's started to be annoying like that recently though.  This resets itself to 4 every time I log in to Gnome, so you may have to change it every time.

---

