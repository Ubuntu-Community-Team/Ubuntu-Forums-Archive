---
title: "install grief, no wifi no gnome :("
date: 2006-07-19
forum: Apple PPC Users
---

### Post by x1um1n on 2006-07-19
ok, so i've been running gentoo on my powerbook pismo as i had some issues in the past with ubuntu.  but what gentoo really lacks is the funky lil wifi setup gui, my favourite bit of ubuntu.  an as i'm out of work for a bit i figured i'd give dapper a go..

booted the livecd, got as far as gnome, almost....

it was having issues with bonobo activation, which caused grief with the GSD, which in turn prevented nautilus from loading :(

so after figurin out the command to exec the installer from a term, equity crashed on python..  grrrrrrrrr..

"screw this" is said, an stuck my breezy cd in, as i knew for a fact that works fine..

finished installing, an it works, ish

after login i get a cursor an the little twinkly twinkly noise, but thats it

no splash screen, no panels, no applets, in short: no gnome

aaaaaaaaaaaargh!!!

now i've come across this issue once before, when i took my powerbook within range of a fairly unfriendly wifi network

but as i live in the middle of nowhere my wifi is quite safely open, so i've never ever had any probs here, an the issue resolved itself as soon as i took the machine away from the other net..

so i never actually had to solve the issue, now i do, an i'm stumped.  i've tried disabling eth1 on the term, but i don't know my way around ubuntu as well as i do gentoo, an all the init scripts etc are in diff places..

if anyones ever had similar issues an has a solution or suggestion i'd be most grateful :)

i really don't wanna have to put gentoo back on there, the machines in a dire need of more ram so it takes forever to compile the system :(

---

### Post by x1um1n on 2006-07-20
just had a thought, the wifi network which caused probs had been setup to only allow connections from MAC addresses the router knew about, as is mine..

and i was having problems down there because the MAC for my mac (sorry, i think i'm funny) wasn't listed..

now my mac's MAC is known by the router as one to allow, or at least it was..  now i seem to remember someone telling me that you can change your adaptors MAC address if you really want, its not set in HW..

if i AM remembering correctly and this is possible, is this something ubuntu would do during installation?  I can't see why it would want to, but then, in my experience *nix is a strange beast, an does strange things for no apparent reason sometimes.. its one of the things i love about the OS, quirkiness :)

---

### Post by x1um1n on 2006-07-20
ok, reinstalled, an it all appears to be workin now..

which is good, but i'm still confused, which is bad :)

if anyone has any ideas what the problem was, i'd love to hear em, in case the issue arises again..

---

### Post by gonorrento on 2006-07-23
Hi x1um1n,

This problem happened to me about 2 hours ago.
The live-install cannot execute nautilus due some error with bonobo-server.Trying solve the problem I execute the installer, which throws PROBLEM WITH PYTHON message ](*,) 
The bad news is: I do not have wifi network at home, so I cannot add my mac´s MAC into the router.
How can I solve this problem ?
Shutting down eth wifi´s interface ?

Please help me

---

### Post by gonorrento on 2006-07-27
please , somebody help me

---

### Post by rasec on 2006-07-27
If you want to change your MAC address, look at the man page for "interfaces". It says that you should be able to specify the MAC, or hw address as man page refers to it, by using the hwaddress option. Here's an untested example below on to change your MAC on an airport extreme using dhcp. Apply your changes to /etc/network/interfaces.

```

auto eth1
iface eth1 inet dhcp
    hwaddress ether 00:11:22:33:44:55

```

I never had the need to try it on my airport extreme nic so I don't know if it works.

By the way, have either of you tried the xubuntu or kubuntu installers? You can alway install gnome after you install xubuntu or kubuntu.

---

