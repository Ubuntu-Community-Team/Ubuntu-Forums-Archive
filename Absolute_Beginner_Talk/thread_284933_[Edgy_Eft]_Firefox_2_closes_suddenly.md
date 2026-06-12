---
title: "[Edgy Eft] Firefox 2 closes suddenly"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by rogierv on 2006-10-26
Today I upgraded Firefox to version 2.0 on my Linux system (Ubuntu 6.10 Edgy Eft). After I while I noticed that the new Firefox crashes when opening sites with Flash included. I downloaded the Flash plugin for Linux: version 7.0.68. Unfortunately is this the right solution for the problem, the browser still closes when opening sites like [http://www.nu.nl]("http://www.nu.nl") and [http://www.iex.nl]("http://www.iex.nl") (Dutch sites). Do someone have the same problem? And how can I solve this problem?

---

### Post by Esben Kramer on 2006-10-26
You could try installing the flash 9 beta, but I'm not sure. I never had this problem.

Automatix2 installs the 9 beta for you, if you already have that installed.

Edit:
If you don't have (or want) Automatix, heres a link with a quick guide:
[http://everythingelse.wordpress.com/2006/10/23/howto-install-flash-9-beta-on-ubuntu-the-easy-way/]("http://everythingelse.wordpress.com/2006/10/23/howto-install-flash-9-beta-on-ubuntu-the-easy-way/")

---

### Post by .aku on 2006-10-26
> **rogierv said:**
> Today I upgraded Firefox to version 2.0 on my Linux system (Ubuntu 6.10 Edgy Eft). After I while I noticed that the new Firefox crashes when opening sites with Flash included. I downloaded the Flash plugin for Linux: version 7.0.68. Unfortunately is this the right solution for the problem, the browser still closes when opening sites like [http://www.nu.nl](http://www.nu.nl) and [http://www.iex.nl](http://www.iex.nl) (Dutch sites). Do someone have the same problem? And how can I solve this problem?

Try changing the color depth from 16 to 24-bit in your xorg.conf
It worked for me..

---

### Post by rogierv on 2006-10-26
> **Esben Kramer said:**
> You could try installing the flash 9 beta, but I'm not sure. I never had this problem.

Automatix2 installs the 9 beta for you, if you already have that installed.

Edit:
If you don't have (or want) Automatix, heres a link with a quick guide:
[http://everythingelse.wordpress.com/2006/10/23/howto-install-flash-9-beta-on-ubuntu-the-easy-way/]("http://everythingelse.wordpress.com/2006/10/23/howto-install-flash-9-beta-on-ubuntu-the-easy-way/")
I installed Flash 9, unfortunately I won't help...

---

### Post by rogierv on 2006-10-26
> **.aku said:**
> Try changing the color depth from 16 to 24-bit in your xorg.conf
It worked for me..
n00v question: where can I find xorg.conf.
And what is the relationship between the colordepth and Firefox?

---

### Post by gruffy-06 on 2006-10-26
That is:

/etc/X11/xorg.conf

---

### Post by PriceChild on 2006-10-26
```
gksudo gedit /etc/X11/xorg.con
```
Find the "DefaultDepth" near the end and change it to 24.

I can't remember why it crashes firefox... it just does.

You'll need to restart X with ctrl+alt+backspace to fix it completely btw.

(close all saved work)

---

### Post by .aku on 2006-10-26
> **PriceChild said:**
> ```
gksudo gedit /etc/X11/xorg.con
```Find the "DefaultDepth" near the end and change it to 24.

I can't remember why it crashes firefox... it just does.

You'll need to restart X with ctrl+alt+backspace to fix it completely btw.

(close all saved work)

correction, ```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by rogierv on 2006-10-26
Yes it works!\\:D/ 

Thank you all! =D> 

ps. I really appreciate the very fast answers

---

### Post by faraazs on 2006-10-26
I was having the same problem and your fix solved the issue.

How do you know what to do and when to do it? The closing of Firefox randomly didn't make me think "Oh, maybe it's a depth problem."

---

### Post by nyko on 2006-11-03
uh oh...
what if my Xorg.conf is already set to 24 by default? :neutral:

---

### Post by 13east on 2006-11-05
thank you very much... i've been working with this problem for a while now and changing the default depth seemed to have worked...

---

### Post by ububaba on 2006-11-07
> **nyko said:**
> uh oh...
what if my Xorg.conf is already set to 24 by default? :neutral:

It is the same here. Default value is 24 yet FireFox(?) crashes the computer. Anyone ready to take up the challenge? At times I have just had one FireFox browser open (no extra tabs) yet it crashed!:(

---

### Post by TooRight on 2006-11-09
Firefox2 seems to be giving alot of people, windows and linux users alike, multiple crash problems. 

Mine has been it just stopping and refusing to do anything, a complete stall out of which restarting firefox is the only option. 

For my bf, a windows user, his firefox completely closes out of the blue...sometimes it does so when he hits the backspace key (heheh, he wasn't very amused at my suggestion to "just don't hit it then" lol :P )

I'm considering going back to the old version until they work out the kinks with this one.

---

### Post by ububaba on 2006-11-09
> **TooRight said:**
> Firefox2 seems to be giving alot of people, windows and linux users alike, multiple crash problems. 


I'm considering going back to the old version until they work out the kinks with this one.

A very tempting suggestion.:D But one needs solutions and betterment.

---

### Post by john262 on 2006-11-20
My color depth is already set to 24. Does anyone have any other suggestions? And if I decided to go back to FF 1.5, how do I do that? I'm a real beginner. Thanks for the help.

John

---

### Post by Cyfr on 2006-11-28
Just to avoid me having to make a new topic.. I dont think this is purly firefox related.

I too experience completly random firefox closures, just closes without warning, ive had it when clicking links, when saving files, just happens, then its fine second time around..

Ive had it with aMSN, i've also had it with amarok just now.

I have 24bit depth. I did think it was something to do with NV drivers, because it *seems* to happen less frequently when I changed to nvidia, but it still happens a lot.

If this is a completly different thing, could someone direct me to a new thread cause I couldnt find any...

---

### Post by syrleb on 2006-11-30
yeh mine does that too sometimes, well it used to, fixed itself

---

### Post by mistypotato on 2007-01-25
Hmmmm....

I'm having the same problem....but this didn't help :( 

My Default color depth was already set to 24

---

### Post by simpleclosure on 2007-02-04
i went to edit my xorg file and the default depth was already set to 24.  what now?

---

### Post by canopytruder on 2007-03-14
same problem, I went to change it but it was already set to 24...

---

### Post by waggingwabbit on 2008-04-15
im having this same problem too!! someone help!

---

