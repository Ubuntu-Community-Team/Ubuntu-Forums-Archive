---
title: "Limewire"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by Stiks on 2005-09-28
Hi all,

I'm returning to Linux after a long break..... about 6 years  :-)   ( mighty fed up with WinXP ... sorry for swearing!! )  Wow,, how things have progressed !!

I'm running Breezy Badger on my Sony Vaio Laptop.... It's working great !

I'm extremely rusty... or more accurately forgot virtually everything... my old brain is begining to remember slowly.

I've just installed Limewire using the "howto" guide for Hoary Hedgehog.... it is in the opt folder and appears in the dropdown app list.... but when I click on the icon nothing happens  :-((

Can any one help ?    I've installed ClamAV and that opperates fine from command line... so that install was fine..........   LimeWire has me stumped !!

Help please,

Cheers,

Stiks.

---

### Post by DJ_Max on 2005-09-28
Run limewire from the command line to see what error(s) you get.

---

### Post by Mustard on 2005-09-28
I'm not really sure how to solve your issue, but while your waiting I thought I might ask a question. :)

What is the difference, for you, between installing Limewire vs Gtk-Gnutella?

---

### Post by az on 2005-09-28
Okay, I haven't read the HOWto, but just a shot in the dark.

I seem to think that Limewire is written in java, right?  Did you install Java?

---

### Post by manicka on 2005-09-28
In breezy I just downloaded the rpm installer for 4.9.3 and used alien to make a deb

From the directory you downloaded it to

sudo alien LimeWireLinux.rpm

sudo dpkg -i limewire*.deb

Works perfectly with the jre (1.4) that comes with breezy

---

### Post by openmind on 2005-09-28
I had problems with Limewire installation on both installs (Hoary and Breezy). Both turned out to be Java related issues. I think I did a reinstall of java last time, and limewire came up straightaway.

---

### Post by DJ_Max on 2005-09-29
Yeah, it's written in Java. Which I'm sure is where his problem lies.

---

### Post by bored2k on 2005-09-29
1. [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)
2. Download Linux self-extracting file .bin
3. ```
sudo apt-get install fakeroot java-package
```
4. ```
fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin
```
5. ```
sudo dpkg -i *.deb
```

That could work.

---

### Post by Stiks on 2005-09-29
[QUOTE=Mustard]I'm not really sure how to solve your issue, but while your waiting I thought I might ask a question. :)

What is the difference, for you, between installing Limewire vs Gtk-Gnutella?[/QUOTE]

Hi,

Thanks for your interest :)  I'm not familiar with Gtk-Gnutella, thats the only reason.

Should I be looking at that? Does it out perform Limewire in your opinion?

Stiks

---

### Post by az on 2005-09-29
Follow bored2k's advice on installing java and reinstall Limewire first.  If it then does not work, try gtk-gnutella if you are sick and tired of trying to figure out the problem.

---

### Post by Stiks on 2005-09-30
Thank you all,

I've managed it after re-booting my old brain !!

Limewire up and running :-)

Cheers,

Stiks.

---

### Post by Stiks on 2005-09-30
Also have Gtk-Gnutell running, interesting program, not quite as intuative as limewire but it will be interesting comparing the search results etc.

When trying to download jre-1_5_0_04 I failed, discovered it is now jre-1_5_0_05 update, that did the trick!
Strangely when I tried a Java update command ( before all this ) it said "no update available".
Is there a simple reason for that anyone ? Just out of interest.

Cheers,

Stiks.

---

