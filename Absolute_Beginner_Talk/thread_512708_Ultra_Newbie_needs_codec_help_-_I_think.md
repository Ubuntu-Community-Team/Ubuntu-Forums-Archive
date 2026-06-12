---
title: "Ultra Newbie needs codec help - I think?"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by AnnaMary on 2007-07-29
I have Ubuntu dual booting with XP without any problems.  I was trying to follow directions to install codecs/plugins or something of the sort to be able to listen to radio on the internet.  I did figure out how to download and play videos, finally.  

I can't find any gstreamer files like the sticky thread says to do to enable multimedia stuff.  This may be because I was tinkering around in the terminal for the first time and now I am getting a message :

E:  dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.  

Well, it won't let me do this because I am not a superuser ?  Somewhere I found where root is and I checked a bunch of boxes, but it didn't help.

Sorry!  The Linux for Dummies book I ordered was out of stock!  I shouldn't have just started tinkering around.  I don't know what the terminal is supposed to do,  can't figure out synaptic stuff, etc......   

(Somewhere in here I was trying to get RealPlayer for Linux to work.  I have read instructions, and I did something really wrong.)

Thanks for any help.  The more basic the better.  If I broke Ubuntu, maybe I can just reinstall it and start over.  It has only been on my computer for a couple of days.

---

### Post by Warren Watts on 2007-07-29
You didn't "break" Ubuntu.... :-)

To issue a command in the terminal as root, preface it with "sudo"

example:

**sudo dpkg --configure -a**

---

### Post by AnnaMary on 2007-07-29
Me again - I was trying to follow directions from :

 Unofficial Ubuntu 7.04 (Feisty Fawn) Starter Guide   

and  Ubuntu Geek - Install Xine Mulitmedia Player in Ubuntu

---

### Post by AnnaMary on 2007-07-29
Thank you, Warren!

I typed the command with sudo in front.  Then I entered my password and it did some processing:

Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinstldebian1 (2.211-13) ...

Setting up unixodbc (2.211-13) ...


What on earth does this mean?

---

### Post by sailor2001 on 2007-07-29
broken files..........now anytime ou need to do most anything in the terminal remember to start with sudo. that is a temporary root administrator for you......as far as streaming radio...... try tunapie (in synaptics)

---

### Post by AnnaMary on 2007-07-30
Thank you, Sailor!

---

### Post by michael37 on 2007-07-30
My recommendation is to install a package called "VLC media player".  It seems to play the common formats much better than other players that come with default installation of Ubuntu Fiesty.

Simply go to System/Application/Synaptic Package Manager, search for "VLC" and install "vlc" - multimedia player and streamer.  

If you need encoding, again, another package that doesn't get installed by default is simple to use and has easier time with common codecs.  In Synaptic, search for "avidemux".  If you used VirtualDub for Windows before, you'll be pleasantly surprised by avidemux usability and speed.

Both applications shows up in "Applications/Sound & Video".

---

