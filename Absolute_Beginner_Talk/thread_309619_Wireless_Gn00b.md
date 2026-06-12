---
title: "Wireless Gn00b"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by azaezel on 2006-11-29
So I've perused the forums extensively, looking for a simple, easy to understand solution for my problem, but most all of them seem to cater to people that have a little more knowledge of Linux than I do.

I'm using a Linksys WMP54GS Wirless adapter, and I am a complete idiot when it comes to Linux.  Does anyone have a link, or first hand step by step information on getting this card to work?

---

### Post by Ecthelion on 2006-12-01
Hi,

I've found you [this howto.]("http://ubuntuforums.org/showthread.php?p=1409752")
If you read it carefully and do as they say, it shouldn't be too hard.

Make sure you do have the right driver as said in the first step!

---

### Post by ninjaPants on 2006-12-01
If you connect to more than one network on a regular basis, you might consider rutilt. Do update the driver as in step 4 of the above howto.

Then to install rutilt:

Download the latest version from [here.]("http://cbbk.free.fr/bonrom/")

Put it on your Desktop, right click and select "Extract Here"

Open a terminal, type (or paste by selecting this text and middle-clicking into the terminal) Hit enter after each line.
```
cd Desktop/RutilTv0.13
./configure.sh
make
sudo make install

```
Any errors you may get are probably dependency issues. You should be able to decipher them on your own and install from synaptic or apt-get/aptitude. If you don't find anything there, try Ubuntu Package search to find the name of the package you really want. If all of these fail, post again here or pm me. 

You'll also want to make sure network manager is installed so you'll switch to a wired connection automatically and be able to disable wireless.

To install it, type in your terminal:

```
sudo apt-get install network-manager-gnome
```

Then navigate through your top panel menus to system>preferences>sessions
Click the "Startup programs" tab and make sure there's an entry that says "nm-applet --sm-disable". This is the command that will start the network manager applet on startup. 

Restart your computer here. Bookmark this post if you want to get back quicker.

After you restart, press alt+f2 and type "gksudo rutilt" (no quotes).
Enter your password and gaze at the pretty gui configuration tool!

The wrinkle here is that rutilt in the current version doesn't work right unless you run it as superuser. There are people that'll say this is a Very Bad Idea, but as long as you're careful and only run it while you're using the wireless network, you should be fine. Be careful because the 'x' button exits the rutilt program instead of sending it to the tray. Single click the tray icon instead. 

Any questions, feel free to ask.

---

