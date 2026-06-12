---
title: "PC will soon fly out my window!!"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by nikolas68 on 2007-11-06
GUYS....need some help please. Spent the all night up in front of the PC: JUST FOR SETTING THE INTERNET CONNECTION!!!! And i'm not a dum dum (or that's what i thought!)

ok....i'm single user, single pc, my internet connection is working perfectly (with windows). I'm setting up the static ip connection...entering all the stuff in the right places (IP, subnet, getaway, dns) I'm checking all the relevant boxes. Still not connecting! try to Ping.....nothing. When i enter all the ip settings, on the top of the windows it shows ETH0.then i read somewhere that i have to add in the folder **/etc/network/interfaces** the line** iface eth0 inet dhcp** TRIED to do that from within the directory folder but it says i don't have enough privilege to change it (i'm the only user!)

to me looks like the network configuration is not right... 

PLS help me or i can't go to work today!!:lolflag:

thanks

---

### Post by llamakc on 2007-11-06
Open a terminal.

Type:

```

sudo cat /etc/network/interfaces

```

CUT/PASTE that into here. On many Linux systems you can do that by merely holding down the left mouse button and dragging the mouse OVER the text you want selected.

Then use middle-click on the mouse to paste into here. Wrap it in the bbcode code tags.

You are going to ALWAYS prepend the administrative command with "sudo" which allows you to make administrative changes.

FWIW if you want a static IP, you do NOT want to set 'dhcp' in /etc/network/interfaces.

Also, tell us if you are on GNOME or KDE and which version you installed.

---

### Post by nikolas68 on 2007-11-06
cheers for helping. using Gnome with GG latest 7.10.

---

### Post by llamakc on 2007-11-06
Is your computer wired to your network? Do you have a CAT5/6 cable plugged into the jack?

---

### Post by PooingCavy on 2007-11-06
if U are going to plz youtube it thx

---

### Post by nikolas68 on 2007-11-06
> **llamakc said:**
> Is your computer wired to your network? Do you have a CAT5/6 cable plugged into the jack?

yes...i have a CAT plugged in.

sorry i'm a real newbe here and with Linux: what do you mean with** FWIW if you want a static IP** what do i actually have to do??

sorry....but i have to understand before i log on to Ubuntu 'cause then i won't be able to read the replies...and yr help...

---

### Post by nikolas68 on 2007-11-06
> **PooingCavy said:**
> if U are going to plz youtube it thx


.....getting ready for launching.....stand by with the cameras...

---

### Post by llamakc on 2007-11-06
Answer this: what does your computer connect to? A router? A cable modem? What?

Open the terminal and show me what the output of this command looks like:

```

ifconfig

```

Since that computer isn't connected to the web, just type the first two lines in. I'm interested in the entry for "eth0".

---

### Post by nikolas68 on 2007-11-06
> **llamakc said:**
> Answer this: what does your computer connect to? A router? A cable modem? What?

Open the terminal and show me what the output of this command looks like:

```

ifconfig

```

Since that computer isn't connected to the web, just type the first two lines in. I'm interested in the entry for "eth0".

i'll do that but you'll have to be patient for a while since i have to reboot and try....and write it down....and come back here....

---

### Post by nikolas68 on 2007-11-06
ok...sorry if it took me sooo long but my fiance' was yelling at me 'cause i look like **** since i have't slept:(

i did **sudo cat /etc/network/interfaces**

this what came out

[B]auto lo
iface lo inet loopback

iface eth0 inet static
address 10.80.28.33
netmask 255.255.252.0
gateway 10.80.0.1

auto eth0[/B]

if i do** ifconfig** i get **>**  and nothing else...:mad:

---

### Post by llamakc on 2007-11-06
So are you connected to a router or what?

---

### Post by nikolas68 on 2007-11-06
it's a "dummy" modem from my isp

---

### Post by llamakc on 2007-11-06
That's beyond me and I don't know how to help you.

This I do know: if you're using GG and GNOME you need to edit your network settings through the menu: SYSTEM | ADMINISTRATION | NETWORK. When you try to fire up one of those menus, and it prompts for a password enter YOUR PASSWORD.

Make the changes there. If you expect internet connectivity from there on out either you'll need to provide more information or know how that modem gets out to the internet.

Good luck and good night.

---

### Post by nikolas68 on 2007-11-06
thanks m8 you're a :KS

---

### Post by HermanAB on 2007-11-06
Hmm, if you have difficulty getting things done, then you should run a Live CD version for a while, till you are more used to things.  The Ubuntu CD is OK, but Knoppix is better.  Knoppix usually manges to get everything to work with zero effort on your part.  After a couple of weeks you'll be amazed at what you have learned and then the trouble with Ubuntu will evaporate.

---

