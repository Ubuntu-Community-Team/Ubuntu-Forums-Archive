---
title: "Total noob, would really appreciate some helpful tips."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by newbiesupreme on 2007-06-14
Okay, I just installed a dual-boot with Ubuntu 7.notsurewhichversion.thefirstonereleasedas7.

I have a few issues that I want to fix before I can really get to using it as my main OS:

My sound is not working.  As near as I could tell in the Sound under.. something, my card is recognized, but I am getting no sound anywhere, in a player or in the testing center place for system sounds.

My Usb hard drive is not working.  320gb Seagate USB 2.0 HD, plug and play on windows, not getting anything in Ubuntu.  During LiveCD install, it asked me if I wanted to install it on there, but I did not, no I did not.

A common problem, I think here, my Wireless Internet is not working.  I have a realtek 8185 card and my wireless network is Security-enabled, the Wireless Networks window in Windows says.

How do I install things?  I download what I think are programs, the equivalent to an .exe in windows, a tar.gz i think, but when I extract I just get around 10 or so files.  


Any help to any of these problems would be amazingly appreciated.

---

### Post by steveneddy on 2007-06-14
Are you on a desktop or laptop?

What kind? Year model if known, model number, manufacturer

System specs? what kind of HD, processor, how much memory

What type of video card?

This may help the next guy - I'm not very good at hardware troubleshooting - everything I have ever installed Ubuntu on works every time.

---

### Post by Shazaam on 2007-06-14
As for the tar.gz look at this page...
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
As far as the sound double-click the sound icon and make sure nothings muted.

---

### Post by newbiesupreme on 2007-06-14
um.  512 of ram, but everything inspect with says 446 or something around there.  1.6ghz.. Mobile AMD Sempron Processor 3200+?

Nvidia GeForce Go 6100 gfx card .

emachines computer, model n1 laptop, thats as much as I know. its only a year old or so.

---

### Post by CautionaryX on 2007-06-14
for the graphics card, a program called Envy may be what your looking for.

for the sound issues, did you install the restricted codecs?

---

### Post by newbiesupreme on 2007-06-14
I haven't installed anything.  Can I install the codecs right now?  I have no internet going in until I can get the wireless network going, and I have no usb storage besides the one that is not being picked up.  I can't really try anything until I get one or the other to work, and I'm stumped on both.

---

### Post by newbiesupreme on 2007-06-14
I tried to enable desktop effects and it said my card was not enabled.  So, thats the same thign tahts happening with the sound?

Ubuntu keeps mounting my windows partition and the recovery partition for windows.  I will be fine with links to any place that could help with either the usb hard drive or the wireless network.

---

### Post by tideline on 2007-06-14
For the sound problem try using alsamixer.  You can unmute everything, it will have a MM at the bottom of each column if it is muted.  Hit m to unmute.

Just type alsemixer ad a shell prompt.  In Applications > Accessories > Terminal.  That will bring up a ncurses based mixer.  Use your right and left arrows to move to the different chanels and if there is an MM punch the m key.

Let us know how it works.

---

### Post by wolfen69 on 2007-06-14
this is a great place to start. [www.ubuntuguide.org](www.ubuntuguide.org) (if you can get online)  just copy and paste the command lines, but try to understand what is going on. and soon enough you'll be helping other people.

---

### Post by newbiesupreme on 2007-06-15
I tried alsemixer and alsamixer.  nothing.  The guide was somewhat informative, but I still can't get the wireless net working.  I need to use ndiswrapper to install the drivers, but to get the sourcecode for ndiswrapper compiled and installed, I need something else installed, and there are like no guides around for installing without internet access.  If I could just get the net working I could figure it out myself in time(preferably with music from my usb hard drive).

---

### Post by Tomosaur on 2007-06-15
To install software, you just click Applications > Add/Remove. The list of available software is there (however, you need an internet connection). Linux uses a repository system, rather than forcing you to go and find websites with software on. The Ubuntu repositories contain thousands upon thousands of different pieces of software - it's usually very unlikely that something you want to install is not in the repos.

However, this is all pretty pointless without a net connection, so I assume that is what you're trying to get working when you downloaded the .tar.gz file? Without knowing what it is you downloaded, it's difficult to help, since a .tar.gz file (or a tarball, as many people call them) are really just archived files, like .zip files on Windows. They could contain anything.

---

### Post by Soybean on 2007-06-15
It's true... not having an internet connection is a huge problem when trying to get set up initially, especially if you're new to Ubuntu.

Does your laptop have a wired network jack? If you can plug into normal ethernet to get internet access, just while you're setting things up, it should make things a lot easier.

---

### Post by newbiesupreme on 2007-06-15
I hooked up the computer to the wired net, this is as far as I got with the wireless network.

*image removed*

I just copied over the settings I used in um um windows.  Are there different settings?  I would really like to make ubuntu my default OS, as I get nearly 3.5 hours of battery life with it while with XP MCE I get just under two.


edit:  I got wireless working!!  I'm so happy, I could offer to send everyone that posted here 20$, but I don't have the money.

Now, the usb hard drive, the graphics and the sound.

---

