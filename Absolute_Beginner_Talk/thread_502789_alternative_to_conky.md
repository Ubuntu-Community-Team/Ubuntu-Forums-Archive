---
title: "alternative to conky"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by Nessa on 2007-07-17
It doesn't seem to work. I want to see my system info on my desktop. Is there something else I can use? I have compiz-fusion btw.

---

### Post by bodhi.zazen on 2007-07-17
Depending on what you want to see there are several panel applets and gkrellm 

[http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)

gkrellm is in the repositories (as are some additional themes).

---

### Post by Nessa on 2007-07-17
Is there something that blends with the desktop background and doesn't look too intrusive?

---

### Post by jordanmthomas on 2007-07-17
There's always torsmo, an old and umaintained conky-like program.

...or you could make conky work.  :)

---

### Post by Bofur on 2007-07-17
Desklet's are another option.

---

### Post by cawill on 2007-07-17
Conky should work but as you use compiz fusion you need to edit the settings in your conky file, I would give you the link to the guide I used to get it working but im not at my pc at the moment so i'm unable to help for now, maybe searching the web for using conky with beryl or compiz-fusion might help.

---

### Post by Bofur on 2007-07-17
Here's what you do to get conky to work with compiz:
Right click your home folder
Click Create Document->New File
Call it .conky_start.sh
Open it up and type 
```
#!/bin/bash
sleep 10 && conky;
```
Change the number 10 to however many seconds you want it to wait to start up. I have it at 10 because compiz starts up fairly fast on my computer
Save the file
Go to the Main Menu->System->Preferences->Sessions
Click New
Call it conky
For the command type in 
```
sh /home/yourusername/.conky_start.sh
```
Click ok
Restart or Log off and conky should start up after 10 seconds(or your set value).

---

### Post by merlyn on 2007-07-17
Conky works fine, it's simply a matter of spending a bit of time sussing out the config options.

The script mentioned by the previous poster works a treat with Beryl or Compiz-fusion.

Check out [this]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky") thread for bucket loads of ideas on configuring conky, complete with config files to copy and use.

Cheers.

---

### Post by silent1643 on 2007-07-17
> **Nessa said:**
> It doesn't seem to work. I want to see my system info on my desktop. Is there something else I can use? I have compiz-fusion btw.

here's a quick install for conky - worked for me 
[http://www.littleubuntu.com/blog/?p=10](http://www.littleubuntu.com/blog/?p=10)

---

### Post by mytwobears on 2007-07-17
Another suggestion in case conky still doesn't work for you.  I use gdesklets and only use the sidecandy applets.  Just place them all on the same side of your desktop, all lined up.  They are transparent, so they blend into your desktop and give a sort of conky look.   I don't use compiz fusion, so I don't know how well they would work with it.  Also, I still can't find an applet to display my processes information.

---

### Post by Nessa on 2007-07-17
I tried again. It worked! Hehe. Looks weird though. But the important thing is that it's on my desktop. Just a few more tweaks. Thanks guys! :)

---

### Post by merlyn on 2007-07-17
> **Nessa said:**
> I tried again. It worked! Hehe. Looks weird though. But the important thing is that it's on my desktop. Just a few more tweaks. Thanks guys! :)

Good stuff.

If you haven't already paid a visit to the thread in my earlier post, check it out.

As mentioned it contains a whole host of different Conky setups with screenshots and config files, a useful resource for tips, tricks and inspiration.

Cheers mate.

---

