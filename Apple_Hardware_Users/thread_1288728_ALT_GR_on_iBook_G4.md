---
title: "ALT GR on iBook G4"
date: 2009-10-11
forum: Apple Hardware Users
---

### Post by DSB5 on 2009-10-11
[FONT=Arial]Hi

**Longer version:** I´ve been taking care of my girlfriends iBook G4 since this summer and i installed PPC ubuntu 9.04 on it to get it up and running and everything work (very slowly). Resently i desided to do a command line install of ppc ubuntu 9.04 and build it upp from there since ubuntu with gnome was a little to much for this old mac. I install lxde and have everything working like i want it except for one thing,

This summer when i installed the desktop version of ubuntu 9.04 i set the right command key as the alt gr key so that i could use the third layer character, by going to system> preferences> keyboard. But now since i did a command line install i cant do this any more and i need to be able to use those characters since ive just started a c++ programming class in school.[/FONT]

**Shorter version:** did a command line install of PPC ubuntu 9.04, installed lxde and i want to change the command key into alt gr so i can use third layer characters.+


is there a program that i can get with synaptic to change this?
or anything other solution would be great.

thanks!

---

### Post by fbugnon on 2009-10-12
I think you'll need to install kdb which should let you remap and/or personalize keys of your keyboard.

Alternatively, you could manually play with the file /etc/X11/xkb/base.html, but it wouldn't be of much help if you're not sure what you're doing.

Hope this works for you and solve your problem!

---

### Post by DSB5 on 2009-10-13
> **fbugnon said:**
> I think you'll need to install kdb which should let you remap and/or personalize keys of your keyboard.

Alternatively, you could manually play with the file /etc/X11/xkb/base.html, but it wouldn't be of much help if you're not sure what you're doing.

Hope this works for you and solve your problem!

thank you very much for the help, but im such a noob. so i need to ask u how to install kdb. i cant find it with synaptic and sudo apt-get install kdb doesnt seem to work (is that the right command).

and no it would probably not help for me to play wil base.html since i wouldnt know what to do.

hope to hear from you.
thanks

---

### Post by fbugnon on 2009-10-13
OK, sorry, my mistake :oops:.  The package you should install is

**kbd** - as in _K_ey_B_oar_D_ (not kdb as I've written previously).

Now you'll probably find it either in Sypaptic or through the command line

- sudo aptitude install kbd
OR
- sudo apt-get install kbd

Just to be fair with you: 1. I also wouldn't know how to play with the html file; and 2. I actually never done this installation, but I found this information in: [http://packages.ubuntu.com/jaunty/kbd](http://packages.ubuntu.com/jaunty/kbd) and it seems to me like what you were looking for...

Well, now I hope this do help.  Please post back your experience.

---

### Post by DSB5 on 2009-10-19
sorry for taking so long, i havent had time to see to this matter.

ive installed kbd and have the newest version, but i cant figure out how to use it, or even start it for that matter. i dont see it under the start button with all the other programs.

could it be that it wount work on lxde?

any help would be appreciated.

---

### Post by fbugnon on 2009-10-19
hum, could it be this is gnome specific?  I'm sorry if this is the case...

Maybe then [_LXInput_]("http://manpages.ubuntu.com/manpages/karmic/man1/lxinput.1.html") is what you're looking for:

> **LXInput**
    A config tool to configure your keyboard and mouse under LXDE # lxde-settings-daemon, configure theme, keyboard and mouse for you. (works with lxinput config tool) 

From: [http://www.lxde.org/lxde](http://www.lxde.org/lxde)

---

