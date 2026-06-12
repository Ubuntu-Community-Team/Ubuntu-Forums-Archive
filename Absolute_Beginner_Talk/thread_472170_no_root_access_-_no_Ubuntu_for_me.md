---
title: "no root access - no Ubuntu for me"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by nomore4me on 2007-06-12
OK, new to linux and Ubuntu, and now probably will throw away the cd's as I really hate not being able to login as root if I want to.

I tried reading some material and can kinda get root access working but I still can't drag and drop files, or copy/paste without getting errors about permissions or something else.

I am not a sysadmin, OS guru (win or linux) but I when I want to do something I want to do it, not have to mess around figuring out the permissions etc.

If there is a global setting that will allow me to use the gui to move,copy,paste whatever and whenever I want to I ahve not found it.

If it does not exist I will use Fedora as I can do that there.

Ubuntu, thanks for nothing

---

### Post by Digitallysick on 2007-06-12
Why not just use sudo? its not safe to be logged in as root all the time.

---

### Post by dpar on 2007-06-12
You can probably use gksudo nautilus. But don't blame me if you break it.:D

---

### Post by nomore4me on 2007-06-12
thanks, i tried sudo and gksudo and read some more

still I can't simply copy and paste to whatever I want, of course there probably is a way but it should be easier.

so Ubuntu sucks for me

---

### Post by PilotJLR on 2007-06-12
Google this for maybe 15 seconds and you'll see the answer. But here it is anyway:

```

sudo passwd root

```
and then enter the user password (for sudo) AND THEN enter the new root password.

That's it. Now you have a root account. Pretty simple, huh.

Do a little reading before you start trolling.

---

### Post by aubre on 2007-06-12
Also you can use
sudo -i 

for a root shell while you are logged in as someone else.

Really, it isn't bad once you get used to it. It is there to protect you.

---

### Post by lazyart on 2007-06-12
> **nomore4me said:**
> thanks, i tried sudo and gksudo and read some more

still I can't simply copy and paste to whatever I want, of course there probably is a way but it should be easier.

This is not Windows where by default you can wreck your system by moving and altering system files.  This is one of the reasons why viruses and adware could only do at best minimal damage to your system.

> so Ubuntu sucks for me

Conversely true.

---

### Post by gezus on 2007-06-12
> **lazyart said:**
> This is not Windows where by default you can wreck your system by moving and altering system files.  This is one of the reasons why viruses and adware could only do at best minimal damage to your system.



Conversely true.

QFT!

---

### Post by Adramelech on 2007-06-12
Have fun breaking your system

---

### Post by feistyfirsttimer on 2007-06-12
Last year I was running Breezy, and I felt like you at first - "Screw sudo, I wanna be ROOT!!"  So I did the ```
sudo passwd root
```thing,  Then, afterwards, I didn't ever need to actually login as root - that ol' sudo thing did me just fine!

Logging in as root *can be dangerous*, and I'm not trying to be patronising here.  When you want to do some admin task, if you're using sudo the password prompt may well give you time to realise your planned action is gonna break something.  If you're logged in as root, the system will do what it's told, no questions asked, and maybe you will end up witha dead box.

Maybe Ubuntu isn't the one for you - which is cool, there are a lot of distros out there and you're bound to find one to your liking.  But give sudo a go for a little while - maybe you will find, like I did, that it's more than enough.

---

### Post by mcduck on 2007-06-12
> **nomore4me said:**
> thanks, i tried sudo and gksudo and read some more

still I can't simply copy and paste to whatever I want, of course there probably is a way but it should be easier.


Press Alt-F2 and run 'gksudo nautilus'. Then go to File/Open New Window. T be able to drag & drop into root nautilus both the source and destination need to run as root. Running some 2-panel file manager like Gnome Commander would of course make this even easier.

Anyway, Logging into X as root is not very wise. That would mean that *every* application you run has root privileges..

---

### Post by ncappel1 on 2007-06-13
May also be of interest. Stay positive!

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

