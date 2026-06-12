---
title: "GeForce 4 MX 440 - help!"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by YouBurntYou on 2007-06-06
Hi all,

I have just started my linux adventure and installed ubuntu 6.06. I ran the 240 updates available.

I tried to runa game called trmulous but everytime I click the icon the screen flickers and nothing happens.Then i experiemnted around with the terminal and got it working but the game was very slow to play (was using mesa drivers). So I searched for a driver for my graphics card (Geforce 4 MX440 - 64mb).

I found a linux (couldn't install it) so I came searching here on this forum. I found some posts by tseliot. I tried Method 1 and it didn't work. I didn't want to try Method 2 because its too long and if it doesn't work it'll get frustrating. So I downloaded envy which didn't work (when i press the package an erro occur Error: dependencies not satisfiable:module-assistant or something like that).

Is there a way or a software that installs the driver automatically? Or an easier way to do it?Im a linux newbie and don't really like using the terminal.

Thank you in advanced and I hope someone will help ASAP.

---

### Post by Happy_Man on 2007-06-06
Hmmm..... feisty, i know, has the nvidia-glx drivers available........ try searching for those, see if dapper repos have it...

Did you use this link? [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.3-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.3-0ubuntu6_all.deb)

Was there a kernel update amongst all your 240 updates? If so, did you restart? That's needed to enable the new kernel. Perhaps envy won't work without it......

Try this in the terminal:
```
sudo apt-get install module-assistant
```

What does that give back? 

I'm only confused because I have a MX 420, and used to use Dapper. Never had these problems..... ah well. Try all that and post back.

---

### Post by YouBurntYou on 2007-06-07
Happy_Man thanks for trying to help me.

The code u gave me doesnt work.

```
root@ubuntu:~# sudo apt-get install module-assistant
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package module-assistant
```

I think there was a kernel update from the 240 updates available or possibly I updated it whilst using Method 1 of tseliot's tutorial and yes I restarted.

And where do I access the repositories from?

The graphics of the O/S looks ok but someone suggested that the game is running slow because the drivers aren't installed (they are using mesa) .

---

### Post by YouBurntYou on 2007-06-07
OK I manged to install the driver with Envy (thank you very much tseliot).

Thank you to Happy_Man and sorry for wasting your time.

---

