---
title: "Firefox on 64bit"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by captcaveman on 2007-01-24
I have Ubuntu for my 64-bit system, so I was looking around trying to figure out how to get the Flash and Java plug-ins to work. Well, I got that all figured out, but if I opened a link from outside Firefox, it would still default to the 64-bit version of Firefox instead of the 32-bit version I had just installed. I thought if I got rid of the 64-bit version, then things would have to default to the correct one, but the Add/Remove thing under "Applications" wouldn't let me, so I went thru the Synaptic thing. Well, now my Add/Remove thing is gone entirely, which for me is a big deal because I have no idea what I'm doing. How do I get 32-bit Firefox to show up under the Applications menu and how do I get my Add/Remove option back?

---

### Post by %hMa@?b&lt;C on 2007-01-24
use GNASH flash is evil :)

---

### Post by captcaveman on 2007-01-24
does that still play flash files thru firefox? I don't really care what plugin I use... but I still want my Add/Remove back, and Firefox to go in the Applications menu...

---

### Post by %hMa@?b&lt;C on 2007-01-24
> **captcaveman said:**
> does that still play flash files thru firefox? I don't really care what plugin I use... but I still want my Add/Remove back, and Firefox to go in the Applications menu...
gnash still plays through firefox, you will need to enable universe and multiverse
post the outputs of 
"aptitude search firefox" 
and 
"cat /etc/apt/sources.list"

---

### Post by captcaveman on 2007-01-24
Ok, sorry, my first real encounter with the OS was two days ago when I installed it, so I really have no idea what's going on here... First, I'm assuming those are commands that will make gnash work in 64-bit Firefox? Which I don't have right now, and I don't know how to get it back without the Add/Remove thing, which I still don't have... Also, will there be a way to make Java work? That was why I switched to 32-bit, I thought there wasn't another way to get both flash and java to work...

---

### Post by %hMa@?b&lt;C on 2007-01-24
> **captcaveman said:**
> Ok, sorry, my first real encounter with the OS was two days ago when I installed it, so I really have no idea what's going on here... First, I'm assuming those are commands that will make gnash work in 64-bit Firefox? Which I don't have right now, and I don't know how to get it back without the Add/Remove thing, which I still don't have... Also, will there be a way to make Java work? That was why I switched to 32-bit, I thought there wasn't another way to get both flash and java to work...
java does not work with 64 bit, you will ned to create a separated chrooted environment for that google for "64 bit chroot" for help with that. those will allow me to further assist you in your installation of 64 bit firefox

---

### Post by captcaveman on 2007-01-24
Well, is there any way I can just have the 32 bit one show up in the Applications menu like the normal Firefox? All I really want to do is have my normal menu back...

---

### Post by %hMa@?b&lt;C on 2007-01-24
> **captcaveman said:**
> Well, is there any way I can just have the 32 bit one show up in the Applications menu like the normal Firefox? All I really want to do is have my normal menu back...
cant you just use the applications menu editor "alacarte" it is I think (i dont know, i use KDE)

---

### Post by captcaveman on 2007-01-24
I don't know how to get it... I don't have the Add/Remove thing anymore... and I don't know how to get that pack (I'm very, very unfamiliar with the Terminal)

---

### Post by %hMa@?b&lt;C on 2007-01-24
> **captcaveman said:**
> I don't know how to get it... I don't have the Add/Remove thing anymore... and I don't know how to get that pack (I'm very, very unfamiliar with the Terminal)
type in "alacarte" in the terminal

---

### Post by captcaveman on 2007-01-24
oh wait, nevermind, I got the menu back... cool, thanks.

---

### Post by captcaveman on 2007-01-25
Ok, new problem. I figured out how to put 32 bit firefox in the applications menu and make it the default browser, but the problem now is that when I click a link outside of the browser (for instance, a link in an e-mail or to a homepage for something in the Add/Remove menu), Firefox opens up to the homepage rather than to the link address. If I can just get gnash and java working with the 64 bit version, that might make my life easier... how do I do that? I've never used Linux before two days ago, so I'm pretty clueless...

---

### Post by 3rdalbum on 2007-01-25
> **captcaveman said:**
> Ok, new problem. I figured out how to put 32 bit firefox in the applications menu and make it the default browser, but the problem now is that when I click a link outside of the browser (for instance, a link in an e-mail or to a homepage for something in the Add/Remove menu), Firefox opens up to the homepage rather than to the link address.

In your Preferred Applications control panel (System > Preferences > Preferred Applications), does the command for "web browser" have " %s" at the end?

For 32-bit users, if the command in the field is just "firefox", then you get the same problem that you've got. 32-bit users have "firefox %s" in that field, which tells Firefox what page you want to open.

---

