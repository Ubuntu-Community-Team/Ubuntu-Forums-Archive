---
title: "[SOLVED] Slow.... Laptop"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-20
I've been running Xubuntu 6.06 LTS on my laptop for about 3 weeks now and it
works great but just seems very sluggish. I know that Ubuntu is way to
much for it to handle so I went the Xubuntu route.  The Laptop I am running
it on is a Compaq Presario 1685 AMD 400mhz, 192 Ram machine. I was
told Puppy Linux or DSL Linux would be a lot fast but I do not want to Format
and go through the reinstalling process again.  Since Laptops are very
propriatary, I'd prob have a time getting the Video card and Wireless to work.
Pretty much I'd like to stay right where I am but maybe change Desktops.
Does the Desktop have anything to do with speeding up the computer or
is it deeper than that?  I really like this distro and would like to stick with it.
I've tried Fluxbox, BlackBox, and they just won't work for some reason.
Anything else I can try?

Anyways, This Laptop came with Windows 98SE and at the time was very
fast (1999). Is it that over time programs required more processor or do 
computers just wear out over time and loose preformace? Windows 98SE
has been unsupproted by MS for some time and now I consider this to
be very Risky when surfing the Web.  Linux is the perfect solution for me
since I loaded the LTS version.  With this, I get Udates for a long time.

Could someone help me on this issue. I'd like this Laptop to be almost
as speedy as it was back in the day.  All I do with it is Surf the Net, Play
streaming Music, and write documents. The Laptop does have a DVD
player but I never use it.  Funny but back then CD Writers were not put in
Laptops so I won't be doing any CD Writing. 

If someone could please help me out. thank you

---

### Post by RedSquirrel on 2007-10-20
I would try using a window manager instead of a desktop environment. IceWM and Openbox are two more you could try.

When you say Fluxbox didn't work, can you be more specific? Was it the menu? You can create the default menu by running the following command in a terminal and then logging in to Fluxbox:

```
sudo update-menus
```

---

### Post by Linux_Man on 2007-10-20
Just use Puppy Linux or DSL, you don't install them, you just pop in the CD and its a live-CD that you CAN install if you want to, Puppy works faster then my Ubuntu install (On a Pentium M 1.5 GHZ) on a Pentium III Windows 98 Desktop with like 100 MB of RAM. Most older hardware is supported just fine in Linux, the cutting-edge ATI and NVidia cards are a bit harder, but most older hardware has had time to be supported.

---

### Post by runemaste644 on 2007-10-20
Dude, just get more ram! It would be a bit hard getting a new processor, though. If you have a big enough HDD, there is something where you can make a partition of your HDD into extra ram, though i have no idea how.

---

### Post by Orbital75 on 2007-10-20
Yes, that's correct the menu didn't work..... When I right click anywhere on
the desktop in Fluxbox, it just show the word FluxBox and then in a way
locks up. Since there are no way to logout or open a command line, I have
to push the power button and restart the computer. As far as another
Windows Manager, what would you suggest?  I am assuming that the
default is MetaCity which I'm prob using as we speak.

As far a Puppy goes, I tried the LiveCD and for the life of me
can't get my Wireless card to show up. If I did get it to work
I would have to keep going through the process everytime
I wanted to use it. I prefer something on the HardDrive where
the settings are concret and stay set.

---

### Post by RedSquirrel on 2007-10-20
> **Orbital75 said:**
> Yes, that's correct the menu didn't work..... When I right click anywhere on
the desktop in Fluxbox, it just show the word FluxBox and then in a way
locks up. Since there are no way to logout or open a command line, I have
to push the power button and restart the computer. As far as another
Windows Manager, what would you suggest?  I am assuming that the
default is MetaCity which I'm prob using as we speak.

If you're using Xubuntu (Xfce), the window manager is xfwm4.

You can usually press Ctrl-Alt-Backspace to get back to the login screen when there seems to be no other way to exit the window manager. ;)

Just run the command I gave above. That will create the default menu for Fluxbox and you'll be on your way.

I would recommend Fluxbox since that is what I use pretty much 100% of the time. It takes some getting used to and it is kind of "hands on". It is easiest to configure it by editing its configuration files *directly*. Some users are not up for that.

IceWM has a "Windows-like" interface which should feel familiar. It's lightweight and has some cool themes.

I suggest you give them a try and see which one(s) you like best. Just install and then select the one you want to try from the Sessions menu at the login screen.

---

### Post by kerry_s on 2007-10-20
try the debian xfced4 version->
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

it's much faster on the old stuff, xubuntu has gotten to bloated. i would also recommend a custom install like everyone else, but you sound like your still getting your feet wet and xfce4 can help you do that easier. :)

---

### Post by RedSquirrel on 2007-10-20
Still, if you don't feel like trying a whole new installation, it might be worth a try to see how a different window manager does with your current Xubuntu installation. It should be a little lighter than running the whole Xfce desktop environment (it was for me, when I had Fluxbox running on top of Xubuntu 6.10).

If running a light window manager doesn't make enough difference in speed, then it's time to try a minimal installation or what kerry_s suggested above. :)

---

### Post by Orbital75 on 2007-10-20
Yeah, I'm going to try the Fluxbox suggestion and see how that turns out.
I'd love to add more Ram but The motherboard Specs states that it's
Maxed at 192 Megs.

As far as running this command below, Do I just
boot up with Xfce normally then open a command prompt
and type it in or is there a certain way I have to run it.

```
sudo update-menus
```

---

### Post by RedSquirrel on 2007-10-20
> **Orbital75 said:**
> Yeah, I'm going to try the Fluxbox suggestion and see how that turns out.
I'd love to add more Ram but The motherboard Specs states that it's
Maxed at 192 Megs.

As far as running this command below, Do I just
boot up with Xfce normally then open a command prompt
and type it in or is there a certain way I have to run it.

```
sudo update-menus
```

You can just open a terminal in Xfce and run the command, then the next time you login to Fluxbox you will have a menu.

(This is covered in the first link in my signature. Guess I should have mentioned that... :))

---

### Post by Orbital75 on 2007-10-21
Thanks..... I'm going to give that a try

---

### Post by Orbital75 on 2007-10-22
Thanks again for the FluxBox Menu Information.  That did the trick an my machine
is much faster now.  thanks  :)

---

### Post by RedSquirrel on 2007-10-22
> **Orbital75 said:**
> Thanks again for the FluxBox Menu Information.  That did the trick an my machine
is much faster now.  thanks  :)
You're welcome. Glad to hear it's faster. :)

---

