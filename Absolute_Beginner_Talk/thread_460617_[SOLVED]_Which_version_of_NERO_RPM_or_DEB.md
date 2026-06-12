---
title: "[SOLVED] Which version of NERO? RPM or DEB?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by crjackson on 2007-05-31
I recently installed the 32 bit version of ubuntu and know nothing about it so I'm moving ahead (pun) one step at a time.

BTW I couldn't get the 64bit LiveCD to boot up into a desktop A64 X2 system...

I've used NERO for years and although there are some free programs out there, I want to start with something I know.

There are 2 versions available for download on the NERO site, one is called the RPM version and the other is the DEB version.

What is the difference, and which one should I get for use with ubuntu 7.04?

TIA

---

### Post by deadgobby on 2007-05-31
You can install K3b in your synaptic and it is a great. If you are for sure you want Nero for linux. DL the Deb file and it should open right up. Ubuntu is Debian based system and should fly as long all the depends are met.
Gobby

---

### Post by starcraft.man on 2007-05-31
Uh, I'd say neither... I used Nero for a long time and I can honestly (did try it for a bit) say it will not feel like the same Nero (7.X was your last taste I assume). Don't bother with it, and in its stead a simple command to get you started with terminal:

```
sudo aptitude install k3b libk3b2-mp3
```

Drop that in the terminal (Applications > Accessories > Terminal) and then push enter and you've given your first terminal command :D.

That will install K3b when its done to the Applications > Sound & Video > K3b.

Trust me, k3b is better (no bloat and does all the burning tasks you need)....... if you absolutely must deb, but I wouldn't >.>.

---

### Post by 13thMonkey on 2007-05-31
The .deb version. But before you install Nero I too would recommend that you try K3B. It's much cleaner and easier to use than Nero but is fully featured (and free, unlike Nero!)

---

### Post by mikewhatever on 2007-05-31
You should go for the deb file since Ubuntu is the derivation of [Debian]("http://www.debian.org/")
RPM files are used in [Red Hat]("http://en.wikipedia.org/wiki/Red_Hat_Linux") and derivatives.
There is no free version of Nero to download, but you can get the trial, and meanwhile look at Graveman or Brasero. Both are in the repositories and very easy to use. Needless to say, they are free of charge.

---

### Post by Gmbrdilos on 2007-05-31
I used to use Nero on windows, currently use gnomebaker.

Ubuntu is a Debian-based distribution, hence you need the .deb package

---

### Post by starcraft.man on 2007-05-31
> **mikewhatever said:**
> You should go for the deb file since Ubuntu is the derivation of [Debian]("http://www.debian.org/")
RPM files are used in [Red Hat]("http://en.wikipedia.org/wiki/Red_Hat_Linux") and derivatives.
There is no free version of Nero to download, but you can get the trial, and meanwhile look at Graveman or Brasero. Both are in the repositories and very easy to use. Needless to say, they are free of charge.

Oh and I might add, gnomebaker. I really liked that one before I started using K3b, not that k3b is better I just prefer its layout and options.

So many options before downloading a trial of a paid program... its a wonder where to start? :D

Edit: Har, gmbrdilos hit post before me... grrrr >.>.

---

### Post by crjackson on 2007-05-31
WOW! You guys are great.  I've never gotten answers so fast before.  I actually intend to try them all out and see which I like the best.  I've owned every version of NERO for win since the start but I don't even use it on Win anymore.  I use Imgburn which is great, but there is no Linux version.

I'll install the K3B and give it a whril.  The reason I wanted Nero is because I need at least one app. on the maching that won't pose a learning curve for me.

Thanks a bunch...

---

### Post by deadgobby on 2007-05-31
K3B is very easy to learn and it uses the drag and drop method on most apps. Not only that, there is loads of support. Thus I need to take a bow to open source.
Gobby

---

### Post by crjackson on 2007-05-31
Well I have to admit it looks pretty sweet.  I'll install it tomorrow and give it a go...  I'm at work right now.

---

### Post by Dec on 2007-06-03
I bought and installed the paid version of Nero Linux (Deb) after the trial. It works perfectly and couldn't be hapier with it. It integrates with Gnome very well. I also feel that this way i can contribute to make other software companies look at Ubuntu as a serious and potential market.

---

### Post by dpzektor on 2007-06-03
> **Dec said:**
> I bought and installed the paid version of Nero Linux (Deb) after the trial. It works perfectly and couldn't be hapier with it. It integrates with Gnome very well. I also feel that this way i can contribute to make other software companies look at Ubuntu as a serious and potential market.

I did the same. Not that the other apps aren't nice as well, but Nero just has those little extras that I *need*. Burning is quite important to me, and Nero is all that I ever used in the Windows world (after test driving literally dozens of burning packages). It's nice to see that it is exactly the same in Linux, and even nicer to see that BD and HD-DVD are supported. Well worth the $20.

---

### Post by kelvin spratt on 2007-06-03
if you want the best and have used it before use Nero 3 as i do nothing in Linux or windows comes close

---

### Post by crjackson on 2007-06-04
Okay, so I installed the K3B and other Linux burning apps found in the synaptic thing.  They all look pretty nice.  I also installed the NERO demo for comparison.

Issues with All Burning Apps. I installed:

I have an 18x burner that burns most of my DVD needs at 16x-18x using verbatim blanks.  Under ubunto nothing will burn over 8x.

I'm thinking my my drive controllers aren't running in DMA mode or somthing, but I don't know where to check it or how to fix it.

Also, I decided to remove NERO for the time being, and can't figure out how to remove it.  It doesn't show up in and ADD/REMOVE lists, and it doesn't show up in the synaptic console either.

I made a good backup image of my HD prior to installing all this software so it only took about 2 minutes to restore to a state where NERO wasn't installed.  BUT... How would I remove the program the proper way, I don't have a clue?

Also, why do you think burning is slow?

---

