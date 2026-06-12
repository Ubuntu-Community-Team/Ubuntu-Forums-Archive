---
title: "lost gui, no internet connection"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by yamel on 2007-03-09
Good evening.

I followed some advice a week or two ago to try to get sound functioning on a Gateway MX3414.  That advice is found here: [http://www.ubuntuforums.org/showpost.php?p=1973286&postcount=34](http://www.ubuntuforums.org/showpost.php?p=1973286&postcount=34)

The second line of this advice reads: sudo apt-get --purge remove alsa-base alsa-utils.  The purge that happens afterward is very thorough.  Unfortunately, the cpu locked a couple of lines later and my gui is just gone.  Booting up ubuntu goes from the logo to the terminal login.

I assume one of the later commands in those instructions was going to get and reload some of the items that were purged, but I don't know which ones and my only connection to the internet is wireless.  I believe that's currently unavailable, unless I can log on to a wireless network from the terminal.

I am so new to this that I'm not sure what information people will need in order to help me.  I am running 6.10.  I have read several unresolved posts with similar problems, perhaps stemming from the exact same instructions.

Thanks very much in advance.

---

### Post by luke411 on 2007-03-09
Did you try typing "startx" at the prompt?

---

### Post by yamel on 2007-03-09
I'm sorry; I should have mentioned that.  I did try 'startx' as suggested in another thread I was following.  The result was the NVidia splash screen followed by some sickly gray/black fuzz.

Thanks.

---

### Post by zubrug on 2007-03-09
sudo dpkg-reconfigure gnome-desktop-data 
sudo dpkg-reconfigure gnome-control-center
sudo dpkg-reconfigure gnome-menus 
sudo dpkg-reconfigure gnome-system-tools 
sudo dpkg-reconfigure gnome-applets
sudo dpkg-reconfigure gnome-session
 from tty and then ctrl+alt+f7

good luck

---

### Post by yamel on 2007-03-09
Thanks for your prompt reply.

The first command went through without comment.  The second returns, "/usr/sbin/dpkg-reconfigure: gnome-control-center is not installed"

I'm guessing that was one of the 'purged' items.  They flew by so fast I couldn't write them down.

Thanks again.

---

### Post by luke411 on 2007-03-10
So maybe you should try the above commands and try using "apt-get install" for anything it reports not found until you have them all back and reconfigured?

apt-get install gnome-control-center

---

### Post by yamel on 2007-03-10
Perhaps I shouldn't respond until I've tried that, but I don't have access to the machine with the problem right now.  So, as a preliminary question, will I be able to apt-get anything if I'm not connected to a wireless network?  Is there a way to log on to a wireless network from the terminal so that I can?

Thanks for your patience if the above questions are really ignorant.

---

### Post by luke411 on 2007-03-10
I don't know if your network is encrypted or not but try this.

sudo ifconfig wlan0 up
sudo iwconfig wlan0 mode managed key [Your key]
sudo iwconfig wlan0 essid "name of your router ssid"
sudo ping [www.google.com](www.google.com)

---

### Post by yamel on 2007-03-10
Thanks for the advice.

I'm having trouble fetching, though, even having gone through the wireless steps above.  It won't ping.  I've temporarily disabled encryption to see if that would help, but it doesn't seem to connect.  No trouble scanning available networks, though.

Are there any outputs I can give that might help folks determine what I'm doing wrong here?

Or, maybe this should have been considered earlier.  I still have the live cd for 6.10.  Can I get any of the missing/purged gui data from that?  Or do I need to just reinstall the whole thing?

Thanks again for all of your help.  Hope the extra questions don't muddy the waters too much.

---

### Post by yamel on 2007-03-12
Hi, there.

I'm still floundering here.  I haven't been able to connect to the internet using the above instructions, so I cannot fetch other files that are needed to dpkg the rest of the files.  Any advice would greatly appreciated.

Enjoy your evening!

---

### Post by yamel on 2007-03-13
Good morning, again.

Perhaps I'm not posting this in the correct place, or not using the correct keywords and tags.  If I'm not in the proper forum, can anyone advise as to the best place to have my problem addressed?

Using the manuals and forums I have not been able to find a solution that will get me past my current state.

Thanks very much in advance.

---

### Post by rabbi1337 on 2007-03-13
This is probably the best place to ask, just sometimes threads go slow for a response.
 I have a MX3414 myself, and as far as the sickly grey stuff when you start X, I had the same issues with NVidia drivers causing that. It ended up in me reinstalling the 64 bit version of Ubuntu and the new NVidia 1.0-9755 drivers and everything works smooth now.

Just to ask, have you tried sudo apt-get install gnome yet before losing internet? Otherwise your best bet is to copy the files from the Live CD to get the 'net up and running. Also if you have done previous kernel updates, in GRUB you could boot from a previous kernel and a lot of times your wireless drivers will still be available from that kernel.

---

### Post by yamel on 2007-03-13
Thanks so much, rabbi1337.

It took a good bit to get the MX3414 going, didn't it?  My problem now, I think, is that I'm stuck operating only with the terminal until I get the gui back.  At the terminal I've been unable to gain access to any of the wireless networks generally available to me using the instructions in the post above.  If I can get access through the terminal, I should then be able to apt-get install the rest.

As an alternative, do you think I can use the Live CD to copy the files that were lost in the purge?  If you think reinstalling is the best option, I'm completely willing but a little nervous about it.  It's dual booted with XP and there's so much listed in the GRUB menu that I don't think I'd know where to reinstall.  As you can tell, I'm pretty new to this.

I'll try not to be a pest here, but I'll ask you later if you ever managed to get sound working on your laptop.

Thanks!

---

### Post by rabbi1337 on 2007-03-15
Yes, you can copy the files, but the best option is to re-install. When you run the live CD, it will allow you to reformat the linux partition like you did before and still keep your XP GRUB option. I've ended up reinstalling 3 times.

---

### Post by STREETURCHINE on 2007-03-15
hi you could give resetting your instalation back to the defaults a go

  ctrl+alt+f1

login and enter

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```


then 
ctrl+alt+f7

not sure this will work for your problem but it has saved me several reinstalls
it sets ubuntu back to it was just after you first installed it

---

### Post by yamel on 2007-03-16
It was worth a try, but restarting puts me right back to the terminal.  I should mention, I've followed a couple of instructions that and ctrl+alt+f7.  What is that supposed to do?  It never has a visible result and I'm still staring at the command prompt.  Invariably, I end up doing a complete restart and maybe that's not what I'm supposed to be doing when ctrl+alt+f7 doesn't work.

Thanks for your advice!

---

