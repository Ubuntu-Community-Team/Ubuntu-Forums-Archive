---
title: "First time startup"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by buck8 on 2005-12-29
I'm a newbie to this. I loaded Ubuntu 5.10,; everthing seemed fine until reboot. FIRST during startup, I have a '**Temporary failure in name resolution**'         **FAIL**. HuH?

first I get a ...**~$** prompt...what command do I enter? 

And, what do I do when:  ***root@myusername:~#***    pops up? What do I enter?

---

### Post by thekiller on 2005-12-30
please give more information, are you able to see the login screen when your computer reboots ?

---

### Post by prizrak on 2005-12-30
Temporary failure in name resolution generally means that you cannot connect to the network, beyond that we need more info.

---

### Post by buck8 on 2005-12-30
OK - I'm not connected to the network. This is an old machine from the garage that I'm experimenting with Linux on.

It boots up fine, then on the login screen it will show (buck8 is the computer name and buck8 is my login - keepin' it simple...) so it will look like this:
[B]
buck8buck8~$[/B]

it's a prompt. What is it asking me to enter?

PS - this is right after the 'Ubuntu has no warranty' spiel...


THX****

---

### Post by Suger on 2005-12-30
Did you install the server version of ubuntu ? You should not start in console mode if you made a full install. Before the no-warranty, what does it say ?

---

### Post by buck8 on 2005-12-30
I'm away from that computer so I can't remember what else was on the screen...

How would I know if I downloaded the Server v. or not?

I just downloaded a CD image from **[http://ubuntu.cs.utah.edu/releases/5.10/](http://ubuntu.cs.utah.edu/releases/5.10/)** the PC version

---

### Post by Rxke on 2005-12-30
you were installing it for the first time, and it said eject your disk, and reboot to finish install, or did this happen later?

---

### Post by buck8 on 2005-12-30
That happend first; the new prompt show'd up @ reboot

---

### Post by thekiller on 2005-12-30
I am just shooting in the blind now. So based on what info you've given, I think your xserver is not configured properly. At that login prompt, type [COLOR="Red"]startx [/COLOR]and see if it does anything. Normally you should see a crosshair with two (or three) terminal windows. If xserver isnt configured then it will bomb. Then you need to do :

```

dpkg-reconfigure xserver-xorg

```

Before you do that you need to know make, model and specifications of your keyboard, mouse, monitor, video card etc etc. Monitor refresh rates are the most important 'cos otherwise you might not see what u want to see. Google on it.

---

### Post by Rxke on 2005-12-30
Hmmm... It looks like the base install went okay, or you wouldn't get that 'no warranty' stuff...
But I'm confused 
> first I get a ...~$ prompt...what command do I enter?

And, what do I do when: root@myusername:~# pops up? What do I enter?

How does that happen? did you get a 
login:       prompt and you entered your name and password (slaps head) nevermind, of course you did... yes you did....

hm. What happens when you type > startx
or > gdm   ?

(EDIT) heh, two people saying the same thing...

---

