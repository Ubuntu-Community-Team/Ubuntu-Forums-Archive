---
title: "Need Wireless driver on HP laptop"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by rock0nman on 2007-12-14
I've been working overtime here trying to get this d-a-m-n wireless card to work.   I think i've found the thread that will help but.....I can't understand what i'm supposed to do with the commands given.   Here's what i'm supposed to type in the terminal but i'm not sure how.

# Install ndiswrapper from source :

    sudo apt-get update
    sudo apt-get install build-essential
    sudo apt-get install linux-headers-`uname -r`
    sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
    mkdir -p ~/bcm43xx/ndiswrapper
    cd ~/bcm43xx/ndiswrapper
    sudo wget [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz)
    tar xvzf ndiswrapper-1.49.tar.gz
    cd ndiswrapper*
    make distclean
    make
    sudo make install

# Install windows driver (BCM94311MCG wlan mini-PCI) with ndiswrapper

    cd /home/yourname/WLANBroadcom/
    sudo ndiswrapper -i bcmwl5.inf
    ndiswrapper -l

    sudo vim /etc/modules
    add this line “ndiswrapper” (without “”)

    sudo modprobe ndiswrapper
    sudo ndiswrapper -m




Could anybody provide some guidance?

---

### Post by siciliancasanova on 2007-12-14
Each of those commands is one line at a time.

Paste commands into the terminal with ctrl + shift + v

---

### Post by rock0nman on 2007-12-14
When i typed this line it said something about it not being there...or not a good command...

sudo apt-get install linux-headers-`uname -r`

---

### Post by unknown user on 2007-12-14
I had a few issues with my wireless on my HP NC6220 laptop a few day ago.  When I booted from the CD, Ubuntu was picking up my wireless driver from the exe files that I had already installed.  However, when I installed Ubuntu fresh, it didnt have any drivers and didn't work.

I was given a number of lines to put into the command line and nothing would work.  Then I read this one post which said that the Bios settings needed to be reset back to default.  So I booted into the Bios settings and done this.  When I went into the Ubuntu system next time the wireless picked up my network (and all my neighbours lol).  All working fine and I am a very happy bunny.  

May be a a path to go down.:):)

---

### Post by rock0nman on 2007-12-14
I'll have to give that a shot

---

