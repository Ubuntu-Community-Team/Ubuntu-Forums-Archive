---
title: "Just installed Ubuntu - a few early problems?"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by HawkST on 2007-09-07
Hey - it took a little while, but I've finally managed to get Ubuntu and Windows XP dual booting on my home PC.

The version I have installed is Ubuntu 7.04 (Fiesty Fawn), and whilst the install and everything went fine, since I started trying to use it I have had a few problems.

(Please note I have looked at other threads and as far as I can see there hasn't been anything that has helped)

I cannot get my Speedtouch USB to work, mostly because I can't find the CD, (I don't think that has any Linux drivers on anyway) and so I cannot use apt-get or anything to install programs, and I have been trying to install VLC version 0.8.6c with no success. I have used the Synaptic Package Manager to install all the things on the Ubuntu CD, but all that has seemed to do is make the ./configure run longer before it gives me errors. I can't remember quite what the error was, but I could use --disable-mad to overlook the error (or something), but that just gave me another error, a missing header, or something. There is nothing else I can install from the CD, I re-installed the 'build-essential' package, but that did nothing.

I'm just wondering is there anything I can do to help me install this program? 
If there is any information I am missing, please tell me, I am not sure entirely whether I am posting everything relevant.

---

### Post by Terl on 2007-09-07
I am not great with modems, but this page may help you:  [Speedtouch modem drivers for Linux]("http://www.linux-usb.org/SpeedTouch/")  The menu has specifics for Ubuntu

---

### Post by arochester on 2007-09-07
Ah the Speedtouch 330 again. See [http://www.tuxmachines.org/node/17403](http://www.tuxmachines.org/node/17403) and [http://ubuntuforums.org/showthread.php?t=445701](http://ubuntuforums.org/showthread.php?t=445701)

---

### Post by jnorthr on 2007-09-07
Welcome aboard :popcorn:

I had exactly the same problem with my install. My modem has an eagle chipset which i believe the speedtouch also has, so it will take a little effort on your part to get this up and running. Will try to find a howTo for you on this one - think there is a french ubuntu site who cover this - will see.

I was not able to setup any internet access, so could not use synaptic to load vlc or any other media player software as it is NOT part of the shipped CD due to legal restrictions on the codecs used in media decoders. My daughter just plugged a wireless pcmcia card into my machine and a wireless usb dongle into our home desktop to create a connection to internet thru the XP system, then i was able to use all those goodies and have loaded a shed-load of software - all really good stuff. You will really enjoy it once you get it up 8-)

another link - just found: [https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)

---

### Post by HawkST on 2007-09-07
> **Terl said:**
> I am not great with modems, but this page may help you:  [Speedtouch modem drivers for Linux]("http://www.linux-usb.org/SpeedTouch/")  The menu has specifics for Ubuntu

Link doesn't work?

So, is there no real way to do it besides getting the internet up and running?

---

### Post by Terl on 2007-09-07
> **HawkST said:**
> Link doesn't work?

So, is there no real way to do it besides getting the internet up and running?

The link works for me... anyway... the other posters also had useful links for you.  Sometimes modems can be a bear.  I had a modem when I first tried Linux 5 years ago and it took some research.  

If you have access to a working connection you will be able to get what you need and you should be able to get it going.  Check the Ubuntu specific help the other posters left for you.  I would especially start with this one that arochester left:  [http://ubuntuforums.org/showthread.php?t=445701]("http://ubuntuforums.org/showthread.php?t=445701")

---

### Post by th3rmite on 2007-09-07
As far as VLC goes, there's no need to build it from source. If you open up the "Add/Remove Applications" application, make sure where the drop down menu that says "Show:" is set to "All available applications". Yo u should be able to search for "VLC" in the search box and it should show up. Just check the box and hit "Apply".

---

### Post by HawkST on 2007-09-07
> **Terl said:**
> The link works for me... anyway... the other posters also had useful links for you.  Sometimes modems can be a bear.  I had a modem when I first tried Linux 5 years ago and it took some research.  

If you have access to a working connection you will be able to get what you need and you should be able to get it going.  Check the Ubuntu specific help the other posters left for you.  I would especially start with this one that arochester left:  [http://ubuntuforums.org/showthread.php?t=445701]("http://ubuntuforums.org/showthread.php?t=445701")

Whoever made that program is amazing. Hopefully I won't get any problems from using the modem with both XP and Ubuntu, doesn't seem like it though. I guess I'm now officially another Ubuntu convert.

---

### Post by Terl on 2007-09-07
> **HawkST said:**
> Whoever made that program is amazing. Hopefully I won't get any problems from using the modem with both XP and Ubuntu, doesn't seem like it though. I guess I'm now officially another Ubuntu convert.

You should not have any problems sharing the modem.  

Welcome to Ubuntu :)

---

