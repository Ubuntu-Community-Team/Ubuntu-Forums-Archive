---
title: "Help please - screen resolution stuck"
date: 2005-11-26
forum: Absolute Beginner Talk
---

### Post by forex on 2005-11-26
Hi there,

I am very excited to finally (after years of wanting to) have installed linux on my machine.  I'm "test driving" linux for the next 6 months to see if I can too break away from Gate's grip.  I am really pleased and will write another post about this shortly, but first I need to ask about a weird little problem I'm experiencing that I can't figure out.

I've reformated my computer & put XP & Ubuntu on it (dual boot).  When testing Ubuntu with the Live CD the screen resolution was set correctly by default (wide screen 12xx by whatever) but now after doing a real install I only have 640x480 (horrible as you'd understand).  I went to "System" / "Preferences" & tried to change the resolution but it is only giving one option (640x480) and no matter what I do it won't allow me to increase the res.  Any ideas on how to fix this???  I am greatful to whomever comes to my rescue, so "thanks" in advance.


[CENTER]*****************************************
$300 to $30,000 in 6 Months Trading Money?
Financial Freedom Is Possible - [TradeMoney.com]("http://www.rapidforex.com")
*****************************************[/CENTER]

---

### Post by binks on 2005-11-26
could you plz give some more info on your system plz ie what graphics card have you got etc

---

### Post by forex on 2005-11-26
Yes, I have an Averatec AV1050-EB1, but I'm sorry, I don't know what kind of graphics card it has.  BTW, earlier while using the Ubuntu Live CD it worked fine, just now with the install not.   Thanks for your assistance.

---

### Post by utcamperj on 2005-11-26
You should be able to boot off the live CD again, then use webmail to e-mail yourself a copy of your /etc/X11/xorg.conf file.  Reboot into your Ubuntu setup, then compare the conf file on your hard drive to the one you e-mailed to yourself.  Maybe the install got the driver wrong?  Or the defaultdepth and the corresponding Screen / Display subsections are different?

---

### Post by akiro.yamamoto on 2005-11-26
utcamperj has a good idea...
If the live cd was able to correctly identify and set up your Video card, why not make a backup of it to your home directory and use that as a starting point. You could save your /etx/X11/xorg.conf from the live cd to a floppy as well. No need to mail it to your self.

---

### Post by forex on 2005-11-26
Wow, sounds good, but could you please elaborate upon how you would do that?  I'll certainly give it a try.  I will have to mail it to myself as I don't have a floppy.

BTW, I am AMAZED with the stuff available (through "Add Applications").  This is a fantastic product!!!  I wish I got onto this years ago!

---

### Post by binks on 2005-11-26
firstly backup xorg.conf in hdd install 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
then boot live cd
 
then 

sudo cp /etc/X11/xorg.conf /home/xorg.conf

this will copy the file into your home folder then just attach the file to a mail client

then back in you hdd install

save the file from email to home 

and then sudo cp /home/xorg.conf /etc/X11/xorg.conf

---

### Post by forex on 2005-11-26
First of all  THANK YOU for helping!  You are truly a fine person and I am grateful for your assistance.

Ok, this will show how much of a newbie I am... do you type "sudo" in too?  And... (drum roll please) *where* do you type all the above stuff in?  Is it into "terminal" in "accessories"?  I don't want to *do* until I get a confirmation so as not to muck things up, as I don't know if I'd be able (yet) to recover from a fubar.  Thanks again for your help!

P.S.  Playing around with this new install of Ubuntu I am actually getting the feel that I can actually live exclusively within this OS.  As McDonald's would say, "*I'm lovin' it"*!

---

### Post by binks on 2005-11-26
yes type in sudo and yes into terminal 
ps if when you boot back into your hdd install and after copy the conf file into /etc/X11/xorg.conf #ie you copied the cong from you live install to your hdd install press ctrl/atl/backspace to restart xserver(xorg) if you get any errors and cant see the desktop 
then at the cmd promt type sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
this will restore your backup

---

### Post by forex on 2005-11-26
Binks,  Thank you.  I shall try this for sure.  I need to go to bed now (it is 6:30am... see how this has excited me against sleeping!).  I'll do what you suggested tomorrow as I can barely keep my eyes open.  I'll reply later re: how it went.  Thank you again!

---

### Post by forex on 2005-11-26
Hi again,

I just wanted to express my gratitude for everyone's help.  I've managed to use your advice, plus a little of my ingenuity to figure out a couple of things that wasn't specified, and now the screen resolution works.  

I am VERY HAPPY with ubuntu so far, and extremely impressed with some of the stuff it offers.  I seriously believe that I will now be able to drop 95% of Win & be almost exclusively a linux guy - something I was interested for years, but linux wasn't ready enough for me back them.  Though I am not a computer programmer I intend to provide my skills (which I have valuable skills) to the ubuntu community to continue the mission... plus I'll donate some $ to the cause.  I'll play around with Ubuntu for a while before I start contributing my talents so that I know what I'm actually doing.  

To ALL of you, thanks & happy computing!!!

---

### Post by binks on 2005-11-26
i an glad its ok m8 :):) 
this forum just makes people help others its in the water i love it

---

### Post by KermitJr on 2005-12-01
Forex

I was having trouble with several older video cards and a particular monitor and kept getting 640x480 no matter what I did for modes, etc.  

HOWEVER, when I went back one time and ran
```
sudo dpkg-reconfigure xserver-xorg
```

I entered the actually amount of RAM on the video card (one was 4096 and another 2048) and PRESTO! My Modes line worked as normal with or without monitor on boot.

So try entering in the actual video RAM you have and that should hopefully fix your error.

If not, troubleshoot by looking for the actual error messages in the /var/log/X11/xorg[tab].log file.

Hope this helps!
KermitJr

---

