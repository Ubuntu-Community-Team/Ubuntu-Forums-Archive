---
title: "would like to switch to ubuntu, but need help getting over the first few hurdles..."
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by fflarex on 2007-03-09
First off I would like to say that I'm not an complete idiot when it comes to computers, but I've also never worked with a command line before. So here are my problems:

My computer is brand new, with an unsupported wireless card (Intel 4965AGN). I think that [this site here]("http://www.intel.com/support/wireless/wlan/sb/CS-025330.htm") indicates that Intel will be coming out with Linux drivers soon, but I'm not sure about that. Even if I'm right, how many hoops will I need to jump through to get it working?

Anyways, I think what I need is a good, cheap PC card adaptor for wireless internet in the mean time. Because believe it or not, I don't have the option of wired internet in my house. Suggestions?

Also, I have Vista working on my laptop as well (I know, I know, but I need to keep it...), and I can't find any good instructions on dual booting. I've found *some*, but each one has been a little different, so I'm wary as to what the right way for me would be. Is it possible to have my linux install on a USB external hard drive and boot from that? Disadvantages to this (besides being inconvenient for a laptop)?

I'm wary about the little stuff that linux might not support on my laptop. Stuff I don't use everyday, but might miss having eventually. Like the card reader, or bluetooth, or the function keyboard shortcuts. I'm even a little worried about the touch pad on my laptop. Will it support the touch scroll feature or clicking/dragging with just the touch pad (no buttons)? Anything I should be more concerned about?

I realize that it's possible to get any or all of these issues fixed if I'm technical enough, but I'm not, and what I'm really asking is if it will be easy enough for someone who has never programmed anything or used a command line before.

As a side note, what would I have to do to get both KDE and GNOME working on the same install?

EDIT: I'm going to try a live CD tomorrow. How indicative would that be of hardware support on the final install?

---

### Post by halitech on 2007-03-09
I haven't done much with wireless myself so can't really help you there but from what I have seen, if the livecd has all your hardware working, it will work on the install. Even if it doesn't work from the live cd, it will probably work once it's installed and if not, usually doesn;t take much to get it working.

far as the command line goes, there's actualy very little done from the command line anymore.

whichever one you install, you can install the other desktop from synaptic or the command line

---

### Post by mjh007 on 2007-03-09
Hi fflarex

First off, welcome to the forums.

I don't use wireless, so I'm afraid I'm not much help there, but something that I do recommend is that you try out the Live CD - you can try it without installing anything on your hard drive and it should give you a good indication as to what works and what doesn't (just be aware that it is a bit slow as it is running off a CD).

Dual booting is relatively painless, have a look at [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

It is possible to install on an external HD and boot off it (if your BIOS supports it).

> As a side note, what would I have to do to get both KDE and GNOME working on the same install?

This is very easy. Start with the default Ubuntu install CD (GNOME) and then afterwards you can install the kubuntu-desktop package (KDE) or the full KDE (kde package) then all you need to do when you login is change which DE you want to run for that particular session.

---

### Post by oranguman on 2007-03-09
hey!

well, the way has been hard but all in all i've really enjoyed it.  Billy Bob Gatestrap has NOTHIN on me for the last 2 months. 

Creating Dual Boot: I can't speak for Vista. You should get specific info on that. But I will tell you that Dual boot setup for XP was totally mindless. Just remember to let Ubuntu deal with the partitioning aspect of install. It's smart, it knows how not to mess up your windows install so let it. 

Bluetooth: Ubuntu has it. From what I read it's quality support too.

Wireless: I won't lie, this was a major snag for me and my Orinoco card. However I believe that even a cursory search for "ndiswrapper" on this site will show you that there is a solution, and that it's not too tough to implement. You can use this little util to get your windows drivers to work with ubuntu. I also recommend "Network Manager" for wireless net management. 

I think that USB drive install of Ubuntu leads to many more inconveniences. I recommend that you get a program in Vista to partition part of your drive, i'm sure there is one, and format it differently. Then, simply install ubuntu on that partition. The problem becomes whether Vista allow the tampering with the boot agent that is necessary for true dual boot. 

I say: Try it, Blog it. We need to know more about what happens in your situation anyway- that's why the how-tos tend to be wishy washy.

peace

---

### Post by dhughes on 2007-03-09
I bought a five year old laptop at a garage sale and put Xubuntu on it, then I bought a D-Link WNA-1330 wifi card and Xubuntu detected it.

 My biggest problem was WPA since I use WPA my router for encryption but all the Network Config too had available for connections was the inferior WEP.

 I did some searching and wound up installing WPA Supplicant. Remember that name you may need it.

 The command line is nothing to be afraid of, most times it's a lot easier than GUI tools t hat do the same thing.

 If you dual boot remember install and set up Windows first and then Ubuntu.

 Gparted is a great partition tool that is on a LiveCD, think Partition Magic only free, you may need it someday.

---

### Post by seshomaru samma on 2007-03-09
> **fflarex said:**
> 

I'm going to try a live CD tomorrow. How indicative would that be of hardware support on the final install?

If the hardware works on the live CD it will work on an installed system.
If it doesn't then it MIGHT work ,but you might need some tweaking. 
I suggest that if anything doesn't work on the Live CD ,use the search function in this forum to see if people manged to solve the problem of that specific hardware,
Also there are two versions of Ubuntu that you can try , Dapper and Edgy , sometimes one of them works with specific hardware better than the other.

I dual boot Vista and ubuntu before ,it was pretty painless. If you have Vista installed already Ubuntu should recognise it and add it to the boot menu . If , for some reason , it doesn't ,you can easily edit the boot menu yourself. 
It is advisable to back up all your data before and make sure you familiarize yourself with the way Linux sees partitions (no C , D , E but Hda1 , Hda2...)

---

