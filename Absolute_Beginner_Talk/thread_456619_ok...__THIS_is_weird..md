---
title: "ok...  THIS is weird."
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-05-27
SOLVED

i upgraded to feisty a while back, but just completely re-installed.  the only complaint i have is that firefox is REALLY slow.  i even have fasterfox and some other mods running that are supposed to make it faster (i've disabled them and that doesn't work either).  it takes FOREVER to load pages and sometimes it'll tell me the page can't be loaded.  but, RIGHT when i hit the try again button, it loads immediately.  any ideas?  i'd REALLY like to keep firefox as my browser.

---

### Post by deadgobby on 2007-05-27
In which way did you upgrade and from version did you try to up grade from?

---

### Post by Austin_KW on 2007-05-27
Did you try disabling ipv6?

---

### Post by starcraft.man on 2007-05-27
> **locke.dragon said:**
> i upgraded to feisty a while back, but just completely re-installed.  the only complaint i have is that firefox is REALLY slow.  i even have fasterfox and some other mods running that are supposed to make it faster (i've disabled them and that doesn't work either).  it takes FOREVER to load pages and sometimes it'll tell me the page can't be loaded.  but, RIGHT when i hit the try again button, it loads immediately.  any ideas?  i'd REALLY like to keep firefox as my browser.

Have you actually tried using other browsers? Try epiphany (sudo aptitude install epiphany-browser). If it equally loads slowly, it must a trouble with connection/network set up on the machine. If it doesn't load slow, then there is a problem with the connection set up in firefox. We can further narrow it down from there.

Edit: Gobby, it doesn't matter how he upgraded (you can only directly upgrade from the previous version). He did a reinstall, thats when the problem started.

---

### Post by locke.dragon on 2007-05-27
how do i disable ipv6?

---

### Post by starcraft.man on 2007-05-27
> **locke.dragon said:**
> how do i disable ipv6?

Question Answered :D

Speed up internet and google earth.

1. Open your Gnome Terminal/ KDE Konsole and type :-
For Gnome
Quote:
```
gksudo gedit /etc/modprobe.d/aliases 
```
or For KDE
Quote:
```
kdesu kate /etc/modprobe.d/aliases 
```
2. Kate or Gedit will open and show you this file :-
(scroll down to see what to copy and paste)
Quote:
# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ################################################## ########
alias net-pf-1 unix
alias net-pf-2 ipv4
alias net-pf-3 ax25
alias net-pf-4 ipx
alias net-pf-5 appletalk
alias net-pf-6 netrom
alias net-pf-7 bridge
alias net-pf-8 atm
alias net-pf-9 x25
# 1, 2, 3 new lines
[COLOR="Red"]alias net-pf-10 ipv6 off --
alias net-pf-10 off -- add these three lines here. 
alias ipv6 off --[/COLOR]
[COLOR="Blue"]#alias net-pf-10 ipv6 =========comment (put #) the original line[/COLOR]
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet 
3. Now "Save" and "Reboot" 

There's another way too: instead of changing aliases file, create fie named bad_list in /etc/modprobe.d containing this line:
Quote:
alias net-pf-10 off 
This method will work even if /etc/modprobe.d/aliases get replaced at some update.

Like I said these are NOT my ideas, I did them and now Google Earth and Firefox are noticeably faster for me.

I snagged that from a tut a while ago. Red is for adding, Blue is commented out, I prefer the first method myself. I found it made me faster. Oh and don't add the -- or text after the red lines, those are for note.

If this doesn't work, try epiphany browser like I said and tell us if its equally slow.

---

### Post by Austin_KW on 2007-05-27
Disable ipv6
System wide; edit /etc/modprobe.d/aliases and change the ipv6 line to 
alias net-pf-10 off #ipv6
Then reboot

Firefox only disable;
Enter about:config in the url address bar
search ipv6 in the filter then double click on network.dns.disableIPv6 to change to true
restart all running firefox instances.

---

### Post by locke.dragon on 2007-05-27
and what exactly is ipv6?  what does it do?

---

### Post by Austin_KW on 2007-05-27
An extension to the IP protocol, so that every device in the universe can have its own IP address.

A couple of other thing too see [http://en.wikipedia.org/wiki/Ipv6](http://en.wikipedia.org/wiki/Ipv6)

---

### Post by locke.dragon on 2007-05-27
ok.  here's the deal.  it's already set to the proper setting in firefox, and i don't want to change anything big on my computer, mess it up, and freak my parents (they're not techies like me and they freak every time i re-install or re-format or re-partition.  :P )

---

### Post by homergreg on 2007-05-27
epiphany web browser is available through the add software tab, it will help isolate what is causing things to be slow.  

it will be interesting that pluto could have an ipv6 address, but I'll bet it will have latency issues.

---

### Post by Austin_KW on 2007-05-27
You are not going to mess up your computer just by disabling ipv6 (you are just commenting out the alias to stop the ipv6 driver loading). All you will do is speed up dns lookup as almost nobody has an ipv6 dns entry and some dns lookups appear to stall/hang.

---

### Post by locke.dragon on 2007-05-27
ok.  well i actually just went back through about:config and re-enabled the mods that somehow got un-enabled and firefox is back up to speed.  thanks for the help and speedy replies everyone!  :D

(in case you're wondering, i re-followed this guide on my website [http://paperclipsandscrambledeggs.blogspot.com/2007/04/how-to-speed-up-firefox.html](http://paperclipsandscrambledeggs.blogspot.com/2007/04/how-to-speed-up-firefox.html) )

cheers!

---

### Post by starcraft.man on 2007-05-27
I agree with Austin, please follow my 3 step guide. It is entirely reversible if your internet fails (it won't, and even if you mess something up, you can just remove the 3 lines and uncomment the blue one).

> **starcraft.man said:**
> Question Answered :D

Speed up internet and google earth.

1. Open your Gnome Terminal/ KDE Konsole and type :-
For Gnome
Quote:
```
gksudo gedit /etc/modprobe.d/aliases 
```
or For KDE
Quote:
```
kdesu kate /etc/modprobe.d/aliases 
```
2. Kate or Gedit will open and show you this file :-
(scroll down to see what to copy and paste)
Quote:
```
# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ################################################## ########
alias net-pf-1 unix
alias net-pf-2 ipv4
alias net-pf-3 ax25
alias net-pf-4 ipx
alias net-pf-5 appletalk
alias net-pf-6 netrom
alias net-pf-7 bridge
alias net-pf-8 atm
alias net-pf-9 x25
# 1, 2, 3 new lines
[COLOR="Red"]alias net-pf-10 ipv6 off --
alias net-pf-10 off -- add these three lines here. 
alias ipv6 off --[/COLOR]
[COLOR="Blue"]#alias net-pf-10 ipv6 =========comment (put #) the original line[/COLOR]
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet 
```
3. Now "Save" and "Reboot" 

I snagged that from a tut a while ago. You have to copy and insert the red lines, take off the text after them (the lines and text) and comment out the blue line (put # in front).

If this doesn't work, try epiphany browser like I said and tell us if its equally slow.

We can't help you if your too scared of modifying files... >.>.

Edit: Uh, ok... you can still do the IPv6 edit btw, it only speeds up the internet.

---

### Post by Austin_KW on 2007-05-27
Also as a general principle before editing config files you should always make a backup

sudo cp /path/filename /path/filename.bak

then to undo any change you can always
sudo cp /path/filename.bak /path/filename

---

### Post by locke.dragon on 2007-05-27
ok.  thanks for the help.  but just for future reference, i'm not afraid of modifying files.  i do it ALOT ALOT.  :P  that's my duty in life.  customize my ubuntu computer.  :P  it's my parents that are afraid i'll screw something up.  but i won't.  and even if i do, i can just re-install.  oh noes!  what a tragedy!  :P  that's what live cd's are for right?

---

