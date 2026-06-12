---
title: "[SOLVED] how do i find out my video card driver number?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by maryjanua on 2007-10-01
iv been fighting to get 3s effects with my pc its got a  radeon x1550 according to windos but a radeon x1300 in ubuntu
iv been on the ati site to find out if they actually do a linux driver for this card
but in their support section they want all the driver numbers and i have no idea how to find this out. they also want the 3rd party makers name(i dunno that either as it came in a plain white box) this is gettin annoying i payed a lot more than i did for my old ati card and i dont really want to have to go out and buy an equivalent nvidia unless there is truly no other option.
iv tried installing envy and although the pc will start in gnome with xgl now and i can see my desktop, all the windows are really slow in responding and when i select to enable desktop effects it just hangs for a couple of minutes then does nothing?
iv been fighting with 3d that long i'm not so bothered now (tho itd b nice)
i just  wana complain at ati  for having crappy support :):)

---

### Post by SpiritIsReality on 2007-10-01
howdy
preparing to be flamed....
ok, I advanced search, ati keyword, because there was a thread about x1300 that I wanted to tell you about. voided3 among others seems to have the ati proprietary figured. [http://ubuntuforums.org/showthread.php?t=560766&highlight=ati&page=2](http://ubuntuforums.org/showthread.php?t=560766&highlight=ati&page=2)
I searched voided3 threads and found this [http://ubuntuforums.org/showthread.php?t=560071&highlight=x1300](http://ubuntuforums.org/showthread.php?t=560071&highlight=x1300)

I don't know if this is what you are after, but for the product and vendor numbers
I found this:
lspci gives you the list, find your graphics card, then run lspci -n and find the 
first number of your graphics card, then you can see the product and vendor numbers xxxx : xxxx.
buds

---

### Post by maryjanua on 2007-10-01
nope iv been searchin for weeks now and no joy
i tried what some1 said on 1 of those links  and now my screen res is waaaayyy down. how do i fix it? the options in sys/prefs/res dont go high enough?

---

### Post by maryjanua on 2007-10-01
iv marked this as solved but its not and unless gutsy fixes it i dont think its going to be and i'll be getting a new card it marked solved but its not :(:(

---

### Post by SpiritIsReality on 2007-10-01
howdy
Look up your monitor's vertical and horizontal refresh rates, and when you
get to a question that allows choice of simple, medium, or expert, choose expert.or advanced
The refresh rates should be in your monitor's manual, or the manufacturer's web page, or go to google.com type in the make and model, and vert horiz.
You could open a terminal. Applications > Accessories > Terminal
Type in or copy and paste```
 sudo dpkg-reconfigure xserver-xorg
```After you are done. You can type in the terminal ```
sudo shutdown -r now
``` to restart your computer, or sudo shutdown -h now 
to halt , stop.
some links that might help
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=resolution&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=resolution&titlesearch=Titles)
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=video&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=video&titlesearch=Titles)
buds

---

### Post by maryjanua on 2007-10-03
i tried all those links and nothing worked. the 1st one actuallyreduced my resolution to 800x600 and it wouldnt go any higher but i got that fixed (im learnin how to do little things like that now without help)
erm the last link was very interesting to read and im sure it'll come in handy at a l8r date but none of it really applied
thanks anyway :):)

---

### Post by nowshining on 2007-10-03
what's the link to the page that asks for the drivers version number?

---

### Post by Terl on 2007-10-03
The ati linux driver is on their site for the X1300, searching even their site for X1550 yields little.  Have you tried the drivers via synaptic?  [http://ati.amd.com/support/drivers/linux/linux-radeon.html]("http://ati.amd.com/support/drivers/linux/linux-radeon.html")

As for the desktop 3D, I had an X1600 and never got it to work well with the 3D effects even with the driver installed.  I popped in an nVidia card, installed the driver and all done, 3d worked like a charm.  I am not saying you need a new card, only that ati has not been linux friendly (current news indicates that is changing).

I notice you mention waiting on Gutsy to see if it is fixed.  This is an ati thing not ubuntu.  If ATI won't provide the support at this time noit much can be done.

As for your resolution issues coult you post your xorg.conf?

Lastly:  Thread on Compiz in feisty with an ati card [http://ubuntuforums.org/showthread.php?t=488385]("http://ubuntuforums.org/showthread.php?t=488385")

---

### Post by maryjanua on 2007-10-03
thanks but iv tried those links before and ended up with no desktop just a cmd line (im gettin quite good at fixing that now :)) and iv just about given up on the 3d stuff. but i have fixed my resolution and its back up to normal . as for compiz etc i'll just leave the pretty stuff alone i think and learn more about cmd line stuff. not quite ready to make the full changeover yet but ubuntus on more than windos so  im not being deterred by these early setbacks i just wish the folk at ati would get their fingers out and support linux drivers because i prefer this kind of software to making the windowcleaner richer still :)

---

