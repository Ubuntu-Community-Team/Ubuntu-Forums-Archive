---
title: "New to linux/xubuntu stuck without gui and lost"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by jackblackhand on 2006-08-08
hello, i recently put together an old system with an amd 200 mhz and a 2 gig hdd, and i ended up putting xubuntu on it because i hav read that linux systems work well on older machines and well its free. but i cant get it to boot into a Graphical user interface, al i get a black screen with the commandline. since i dont know that much about linux i could use it, unless i could learn how to do everything without it..but can you surf the web and such?

---

### Post by aysiu on 2006-08-08
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by steve.horsley on 2006-08-08
Are you able to log in?

Assuming you are, try the command **startx** and see what kind of error messages you get.

Or read this thread [http://www.ubuntuforums.org/showthread.php?p=1351644#post1351644](http://www.ubuntuforums.org/showthread.php?p=1351644#post1351644)
for more details on how to configure the GUI.

Edit:
Beaten to it again.
Aysiu's web site is a good place to go too.

---

### Post by pdub on 2006-08-08
How much RAM does the system have?

What type of video card does it have?

Can you login to the console? 

If you can login then type startx to start XFCE (The graphical desktop used by Xububtu)

If this produces errors then please post them here.

---

### Post by jackblackhand on 2006-08-08
it seems to have 98 mb of ram and i have no clue about the vid card 
 i have installed in text and oem, in text mode it said it couldnt find /etc/x11/something or other and then in oem  it didnt even recognize startx as a command. i tryed apt-get install kdm and had to do apt-get install kdm --fix-missing. this is the system as it is now, which still doesnt consider startx as an option. should i reinstall? is it hopeless?

---

### Post by xpod on 2006-08-08
I tried installing xubunto and kbunto on a pc with only 124mb of ram and none of them would install.
I eventually managed to get the aternate Kbunto on it.

That was also after finding an old 64mb of ram lying around so im not sure how i`d have got on with just the 124.

I think you might need an even smaller distro....DSL???

---

### Post by pdub on 2006-08-08
With only 96MB you may wish to consider something like Damn Small Linux,

[http://www.damnsmalllinux.org](http://www.damnsmalllinux.org)

It's considerably scaled back compared to Xubuntu but it should work well on your hardware.

Otherwise ...

I have seen posts were people are running Xubuntu in just 96MB of RAM so if all else fails you can always try a re-install.

---

