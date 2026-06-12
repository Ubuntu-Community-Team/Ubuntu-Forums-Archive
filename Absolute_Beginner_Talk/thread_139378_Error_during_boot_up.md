---
title: "Error during boot up"
date: 2006-03-03
forum: Absolute Beginner Talk
---

### Post by mroark on 2006-03-03
I am unable to get past "mike@ubuntu:~$       I tried the suggestion of: 
sudo apt-get xubuntu with no success.  During bootup I get one error: "Temporary Failure in Name Resolution".  Could this be some of my problems?:confused:

---

### Post by pestilence4hr on 2006-03-03
It sounds like the xserver is crashing.  You should try "sudo nano /var/log/Xorg.0.log" and look for a line with (EE) in it.  Post that here.  Also give some details about your video card.

---

### Post by super on 2006-03-03
> I am unable to get past "mike@ubuntu:~$ 
did you actually finish the ubuntu install? if yes then try entering gdm with this command:
```
sudo killall gdm
sudo gdm
```
type your password when prompted and press enter.
this should enable you to enter xfree

> During bootup I get one error: "Temporary Failure in Name Resolution". Could this be some of my problems?
this means that you internet is not configured. it's the reason why you can't 'apt-get install' anything. your machine is not configured to use the internet yet.

btw did you use a full install or a server install?

---

### Post by mroark on 2006-03-03
I did a "server" install due to limited resources.  I am trying to learn using an older Dell P3 with an integrated video and 64mb Ram.  I posted the other day and I am trying some of the suggestions...server installation was one of them.  Also, I got Ubuntu to load fine (slowly, but fine).  It loaded all drivers, but resolution.  It was simply to slow to do anything.  Some suggestions wouldn't work because the machine is to slow.  I wanted to learn and learning I am on this machine before I migrate to my good pc.

Thanks for helping me out!  :-D

---

### Post by pestilence4hr on 2006-03-03
So I guess you were trying to avoid running gnome.  I would suggest doing "sudo aptitude install gdm xfce4"  and when that completes, run "sudo /etc/init.d/gdm start".  When you get to the gui prompt, make sure you select session "xfce4".

---

### Post by mroark on 2006-03-03
I jus ran the sudo command and got this:
GNU nano 1.3.8             File:  /var/log/Xorg.0.log

Blinking cursor (on black blank page)



bottom:                       [New File]
^G Get Info  ^O Write Out   ^R Read File   Prev Page ^K Cut out ^ C Cur Pos

^X Exit  ^J Justify  ^W Where Is  ^N Next page  ^U Uncut Text  ^T ToSpell 
:confused:

---

### Post by super on 2006-03-03
um, you must of entered something incorrectly
hit ctrl+X and try again

---

### Post by pestilence4hr on 2006-03-03
That's because xorg isn't installed.  Installing gdm and xfce4 will fix that.

---

### Post by mroark on 2006-03-04
Several things have occured.  1. 391Mb download from install disk  2. then unpacked  3. ran sudo /etc/init.d/gdm start  and two things happened - 1. got a blue screen: The X Server is now disabled. Restart GDM when configured correctly.  2. Gnome Display Manager - FAILED

I do not know when or where to load the GDM, either Gnome or xfce4

---

### Post by pestilence4hr on 2006-03-04
Hrmm.  Not good.  I would start with a

```

sudo dpkg-reconfigure xserver-xorg

```

This should take you through and ask a bunch of questions to correctly reconfigure the xserver.   Then again run

```

sudo /etc/init.d/gdm stop && sudo /etc/init.d/gdm start

```

If you again get the blue screen, now it is time to do

```

sudo nano /var/log/Xorg.0.log

```

and look for the line that is prefixed with (EE), report back.

---

### Post by steve.horsley on 2006-03-04
Can we restart this conversation? You say you "can't get past" the mike@ubuntu$ user prompt. What do you mean by this? What are you trying to do?

I see some people suggesting that you try and edit your GUI config, but since you chose a server install, this is clearly not what you want. Or did you not realise that a server install doesn't install a GUI? If this is the case, you can install the GUI with "**sudo apt-get install ubuntu-desktop**".

So what is the problem you are looking for help with?

---

