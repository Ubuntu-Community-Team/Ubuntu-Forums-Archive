---
title: "Connection speed bites, can't play MP3's?"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by RockinDolphin on 2007-01-06
Hi!


    This is my first time using Linux/Ubuntu. I had a brand-new hard-drive that I boght months ago, but couldn't afford WinXP, so I thought I'd give this a try.
    So far, so good. It has taken some getting used to. However, one problem is it didn't install my network card the first time. I shut it down, pulled-out the card, restarted it, shut it back down, and then started it back up and it found and installed it, so that went okay.
    But when Ubuntu said there were updates and I started trying to download them, I'm not even getting 1Kbs a lot of times! I thought maybe it was too many people pulling off of limited server resources, so I went to a music service to download a song and I was lucky to get 200Kbs when I typically get between 400-600Kbs, or better from them. 
    Then, I tried to play my song and Rhythmbox won't even play the file! What gives? I'm starting to become a little disenchanted, now. Also, I've got a 120Gig HD and Ubuntu doesn't seem to know how big the drive is. That's probably my fault for not being able to understand the dialog during set-up. The partitioning dialog is somewhat vague and not clearly defined, in my opinion. It could use some work.

---

### Post by jvc26 on 2007-01-06
Hi there:

1/ Ubuntu cannot play mp3s out of the box because they are proprietary codecs, and hence arent available with Ubuntu - for information on how to install them and a whole load of other stuff, check out:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

2/ The partitioning thing (especially under the live cd) is pretty self explanatory - you put a partition onto the whole disk (as in all bar 1GB) as ext3 (the filesystem) then you place a 1Gb partition for swap (which linux uses as extra resources) Thats fairly straightforward, so maybe there was just an issue with the way you formatted so the partitions dont take up the whole drive? Or perhaps it could be the fact you do not get the full 100% of the size printed on the disk, all drives are slightly smaller (in my experience) than they say on the top - for instance a 200GB being 194GB or an 80 being 76 - if its just a  few GB it may be down to this difference in drive space.

3/ Ubuntu is NOT a windows alternative, it is very different. It may work straight away, but more likely it will need tweaking and some time and effort to get everything up and running as you want. It does need you to come with an open mind and not expect a windows clone but free - especially as its based on Unix :)

4/ If you need help with the install check out the forums there is one heck of a lot of info here on how to install so any problems 'search' button will come in great help.

5/ Not sure whats up with your download - have you checked out your router/card on the forums here and seen whether there are issues other people have had and how they've solved them?

With a bit of work, Ubuntu is a viable OS - I run it without windows and with few problems now, but it does take some work :) Best of luck!
Il

---

### Post by RockinDolphin on 2007-01-06
Yeah. I can understand what you're saying about Ubuntu not being a Windows alternative, but in reality it is. We're trying this OS out because of various reasons, but I guess I'm namely doing it because of money. Also, it's good to have alternate OS's instead of just one, in my opinion. If one group goes down the 'wrong way' on a way to program with the example being Microsoft, then you're stuck with their problem until they can get it (hopefully) fixed. However, if you have a variety of OS's, you can switch.

Problem is, it seems to me that there should be more across the board usage of languages, or commands, etc. because it bothers me that there may be/is a lot of software that I'm going to miss out on by switching to Ubuntu.

Is there a way for me to go back and partition the drives without starting all over again? Also, when I was having network card problems, the 'device manager' seemed to be totally useless. In Windows, you've got options of deleting the device, or updating the driver, but double clicking/right clicking got me nothing! It [I]saw[I] the card, but that was all[I][I]I got out of it. As I said, I shut it down, pulled the card, restarted, shut it down again, reinstalled it, then started it again and I guess it worked 'cause I'm now able to get on the net.

Speaking of which, I can't seem to find much info on being able to get a firewall. I read that there are some, but I tried tyoing firewall in the Ubuntu search and didn't get anything.[/I][/I][/I][/I]

---

### Post by r4ik on 2007-01-06
Look for Firestarter in Synaptic.

Good luck !

---

### Post by Frak on 2007-01-06
There is a firewall built in, its called IPtables, if you want the GUI frontend to control the ports of it, there is a program called firestarter...

```
sudo aptitude install firestarter
```

and an anti-virus called ClamAV...

```
sudo aptitude install clamav
```

or if you want them both...

```
sudo aptitude install firestarter clamav
```

but there is **NO** need for these, as
1. the average user doesn't need that much access to the firewall, don't need FireStarter
2. there are no viruses or probably will never be any "dangerous" viruses for Linux, in fact ClamAV was made so a server running Linux could scan the Windows client computers.

And Ubuntu is **NOT** a replacement for Windows, More of a replacement for Slackware, Gentoo, or SuSe more than Windows, because nothing can be a replacement if they don't work the same way, like you can't say your Washing Machine is a replacement for Washing clothes, because your patatoe masher can mash potatoes, it makes NO sense, and nothing can be a replacement if nobody will (eventually) support it, Linux has very little hardware supporters, the big names (thankfully) are Nvidia and ATI, and for anybody who has problems with wireless cards, use an Orinocco card, the manufacturers made it **FOR** GNU/Linux, not for Windows/Mac OSX, but we do have a graciously large amount of supporters, reverse engineering and creating drivers for existing hardware, to run on GNU/Linux.

And if you want a proxy (because you will eventually think you need one) use TOR, as I remember it is in Synaptics, and ready for download.

---

### Post by quartzy on 2007-01-06
> **RockinDolphin said:**
> But when Ubuntu said there were updates and I started trying to download them, I'm not even getting 1Kbs a lot of times!

You should change your sources.list to use a mirror close to you, [this]("http://www.ubuntu-nl.org/source-o-matic/") link may help you.

---

### Post by Ergo on 2007-01-06
Unlike other OSes, Ubuntu (linux) is made to be a core unit.  Something to be added to and configured the way the USER prefers.  You will have to keep an open mind about something new.  Redmond for years has taken surveys and dumped everything every end user wants (paperclips that offer advice!) into it's OS.  As long as you are not willing to decide what YOU want out of Ubuntu and MAKE it that way, it will never work for you.  Nothing is free.  You have a great piece of software in your hands, if you are willing to give it the same amount of time as you have other OSes in you past.  Learning something new makes you intelligent about computers, rather than being just another one of the point and click generation.  Everything you are having problems with can be fixed with a little research.  Give it a try.  It will not cost anything except time.  I hope you stick with it.

---

### Post by RockinDolphin on 2007-01-08
I *was[I] using the mirror in Georgia, USA*[/I]. But the download speeds were horrific. I have seen a few solutions given as removing "us." from a command line, but no idea where this is. Also, the people giving these nuggets of info made the comments that, "We don't want to spread that around too much or the servers will get flooded and slow down." or something to that effect...

[http://www.ubuntuforums.org/showthread.php?t=333800&highlight=slow](http://www.ubuntuforums.org/showthread.php?t=333800&highlight=slow)

Gosh. I don't know what to think about that. I mean, do we want this thing to succeed, or not? 

I was able to finally play MP3's, though. However, I'm starting over on my install because I wasn't sure how my hard-drive was partitioned. Still confused about that. The partition dialog sucks, in my opinion, because I wanted to divide this 120Gig drive into roughly three 40gig drives.

---

### Post by kj1h234lkj1234 on 2007-01-08
Let's get rid of IPv6! (If you don't know what it is, you're definitely not using it!)

Edit /etc/modprobe.d/aliases in your preferred text editor.

Put a # in front of the following line: 

```
alias net-pf-10 ipv6
```and add the following line below it:

```
alias net-pf-10 off
```Save the file and reboot.

(Should look like this before you save):

```
#alias net-pf-10 ipv6
alias net-pf-10 off
```

This disabled IPv6, which is the #1 cause of slowdowns with Internet stuff in Ubuntu.

After rebooting, open Firefox, enter "about:config" into the address bar. Find "network.dns.disableIPv6" in the list, and edit it to be True. Restart Firefox.

Enjoy fast downloads. :)

If you ever need to reenable IPv6, do the exact opposite of the above instructions.

---

### Post by RockinDolphin on 2007-01-08
I'm using a cable modem via Ethernet card. Will this still affect me?

---

### Post by NovaNine on 2007-01-08
I have the same problem... but how do you edit this "aliases" file ?
It won't let me overwrite it, as it's read only... How do I fix this ?

---

### Post by kj1h234lkj1234 on 2007-01-08
> **NovaNine said:**
> I have the same problem... but how do you edit this "aliases" file ?
It won't let me overwrite it, as it's read only... How do I fix this ?

```
gksudo gedit /etc/modprobe.d/aliases
```

gksudo will launch a GUI application with the permission of the superuser (aka you can edit anything)

---

### Post by RockinDolphin on 2007-01-08
Well, so far so good! My speeds are kick-*** and I've got the MP3 player going! Hopefully, if all goes well, I'll have this thing all specced-out like I want it when Micro$oft starts screwing people over even more with Vista! Many thanks to all who have helped me!

---

### Post by kj1h234lkj1234 on 2007-01-08
> **RockinDolphin said:**
> Well, so far so good! My speeds are kick-*** and I've got the MP3 player going! Hopefully, if all goes well, I'll have this thing all specced-out like I want it when Micro$oft starts screwing people over even more with Vista! Many thanks to all who have helped me!

Don't get discouraged if things aren't as easy as you had hoped. It will come with time.

As you make small victories such as these, you'll become more familiar with the layout of Linux itself, and understand why things are the way they are. (for example, why sources.list is in /etc/apt/, because all config files go in /etc/ under a directory named after the program for the most part)

Don't forget, there's also the Ubuntu IRC channel for assistance as well as these forums. You can pick up good tips and tricks from many places.

---

### Post by NovaNine on 2007-01-08
Works ! Thanks a lot !

---

