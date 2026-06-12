---
title: "two questions before i install ubuntu"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by thekidxp on 2007-03-03
I'm installing ubuntu hopefully tonight but i have two quick questions for you.

first, How could i find out if my wireless card will work with it. its belkin (802.11g) it needs a cd to install so im going to assume thats why its not working with my live cd but i would like to know if i can use the internet before i wipe my hard drive.

and second, and this one isnt as important, this is my first distro of linux and i heard its wonderful to learn on, but where do i go to find some info. im not even sure what to look for. command line is one thing i need to know more about but i dont even know what else to look up for customizing different things.

---

### Post by floke on 2007-03-03
Ok, first - you'll need to be more specific about your wireless model etc. - but it shouldn't be a problem. You might have to use 'ndiswrapper' to set it up, but there are a zillion howtos on the forum. As (Q2) there is for most stuff. For all the info you need just look around here. Search box is top right of the page. 

BTW: If this is your first drive with Linux then PLEASE don't 'wipe your hard drive'. Set up a dual-boot system so that you can continue to use Windows if you need to - e.g. to get info on how to use ndiswrapper, for a start!

And welcome to Ubuntu :)

---

### Post by thekidxp on 2007-03-03
thanks for helping so fast ill look for more info on the card and check a little longer on the site and im wiping my hard drive because im doing it on my personal computer, meaning im trying to get as much info as possible before i do it but if worst came to worst i would be able to use the family computer to get help, thanks for all the advice though. and yeah i have no clue what  ndiswrapper is lol, ill check some stuff out though.

---

### Post by floke on 2007-03-03
Still a bad idea to jump straight in and wipe the entire hard drive IMHO. Why would you want to do that? What advantages do you gain by it? Why not dual-boot and wait for six months or so before finally deleting the Windows partition?

BTWL If you're going to install tonight - and if you're going to dual-boot - I would go into Windows now and start the defragment - it could take some time but its something you'll need to do. Use the family PC to look up info on ndiswrapper and your card type while the Wincrap defrags itself (btw2 - you'll never have to do this again!).

Any problems then just post back here.

---

### Post by bmathis on 2007-03-03
To see if your model of wireless card is support check out this link:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin")

To get help with everything else here is a couple of sites:

[http://ubuntuguide.org]("http://ubuntuguide.org")
[http://psychocats.net/ubuntu/index]("http://psychocats.net/ubuntu/index")
and of course the forums.

I also highly recommend Ubuntu Hacks from O'Reilly, you can get it for less than $20 (almost half off) from Nerdbooks.com [http://www.nerdbooks.com/item.php?id=0596527209]("http://www.nerdbooks.com/item.php?id=0596527209")

---

### Post by thekidxp on 2007-03-03
idk i may but its an old computer with a small hard drive and ive been wanting to wipe it for a while still. i was going to save some things i would want if i put windows back on and so far  i like ubuntu from the live cd. overall its getting bogged down and i wanted to start over anyway. and so as opposed to taking up more of my limited hard drive than necessary i was just going to use linux. (BTW i only have 20gb of Hard drive) i may still but both on but at the moment im down to like 1.5gb (not sure exactly how much though) but i may still wipe it and then dual boot. other than buying a new hard drive which ill probably be doing soon anyways my only other option is waiting to do it and get the hard drive or just go through my hard drive finding all the little things i dont need anymore (it used to be a family computer and they did a lot of work on it,lots of useless things because most dont know much about computers) the biggest problem is there is a lot of left over junk in files folders that they made hard to find. so do you suggest i wait then=( because i was so exited about finaly getting ubuntu up and running.

---

### Post by thekidxp on 2007-03-03
and btw thanks for the links im going through them now

---

### Post by thekidxp on 2007-03-03
umm do you have a way to find my cards model without the box i know there is a way but im not sure how thanks for all of the help so far btw

---

### Post by justifier on 2007-03-03
I have a belkin (802.11g) wireless card, and i found the best, may not be the correct way, but the easiest way of getting it working is on installation of ubuntu have it plugged in and use it to download the packages, DO NOT USE A CAT/ETHERNET/NETWORK CABLE. I found it just works of you do this

---

### Post by bmathis on 2007-03-03
> **thekidxp said:**
> umm do you have a way to find my cards model without the box i know there is a way but im not sure how thanks for all of the help so far btw

It should be located somewhere on the card... probably next to the serial number and/or bar code.

---

### Post by oilchangeguy on 2007-03-03
in xp check device manager, click on the + sign next to network cards (or something like that, i'm not running windows right now) and right click on the device and select properties.

---

### Post by thekidxp on 2007-03-03
ok thanks for the help on  the card but now does anyone have a suggestion about whether i should go ahead an install or use a dual boot ill be checking to see if i can get the card to work so i guess thats my main question do you guys think i should wait, dual boot, or just go ahead and install(im finaly thinking try to clean up the hard drive as much as possible and get ubuntu to dual boot)

---

### Post by oilchangeguy on 2007-03-03
you'll find that linux has a fairly large learning curve. i'd dual boot for now. make sure to cleanup windows, defrag. etc. then load the live cd and when you get to the part about partitioning select the option to use the largest available space (not take over the entire drive). alot of posts talk about manually creating partitions for swap, etc. this is not needed. just let ubuntu handle the partition itself.

---

### Post by floke on 2007-03-03
Try this.

(to shrink Windows by even more - turn off hibernation feature (power settings) and get rid of the page file (under my computer somewhere).
Defragment Windows + run scandisc.
BACK-UP ALL DATA (things can always go wrong)
Use LiveCD - system/admin-gparted - shrink Windows partition to the size you want.
Double click install icon on desktop - select install in largest available free space option.

Enjoy dual-booting ubuntu,

When you want to - delete the windows partition and use it for something else!

Good luck.

** IMPORTANT - You might actually need the Windows partition for ndiswrapper - it needs to run the Windows driver for the wireless card. Am not sure about this since have never used ndiswrapper - but better safe than sorry.

---

### Post by bmathis on 2007-03-03
my opinion, if you have another box that you can jump on in case of emergency, go for it and wipe the box. Sometimes its just easier to dive right in and have a backup then it is to dual-boot, have an issue, reboot into windows, right down steps, reboot into ubuntu, try the steps out only to find out that you didnt write down something correctly, and repeat the process.

If all else fails you can always reinstall and have a clean hard drive!

---

### Post by thekidxp on 2007-03-03
thanks for all of your help thats probably what ill do(dual boot) but now i checked the site [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)
and it looks like my card may work with a lot of work though i may just go buy a new because it sounds really complicated its a F5D7000 if you guys want to check and thanks other than the fact that a new problem has arose you guys answered my original questions. thanks again

---

### Post by igknighted on 2007-03-03
On a 20 GB drive?  And you have another comp?  And you were already going to wipe windows for a clean install (I think you said that above)? Go ahead and wipe your drive.  10GB really isnt enough for win XP, and while Ubuntu can run on it, you will feel cramped.

As for the F5D7000, I have an F5D7010 v.5100 and it works absolutely perfectly via ndiswrapper.  Follow the directions and it is no trouble at all.

---

### Post by oilchangeguy on 2007-03-03
xp will run fine on 10gb. (as long as you don't fill it with other programs) i've got xp pro on a 10gb slave drive on this computer. with open office 2.1, adobe 8.0, scribus, and a few other things it uses a little over 5 gigs. xp with sp2 by itself will use over 2 gigs.

---

### Post by floke on 2007-03-03
My apologies.
I missed the post with the 20Gb details in it.

I agree with the last post. With 20Gs you should just wipe the entire drive. Far easier too.

---

### Post by thekidxp on 2007-03-03
yeah ive got almost no hard drive i may wait and see if i can find a new hard drive and start from that im really not sure because ive wanted to clean this thing up for a while and that was the best way could think to do it. ill see how much i can clean up and wait and re-weigh my options but im glad i could get such great opinions from all of you so far

---

### Post by thekidxp on 2007-03-03
k looks like ill be starting over and this computer im instlling to is basically a junker anyway its the old family computer and was given to me so i have my own im looking into getting a laptop for me soon anyway so i should be fine with the starting anew it make take a while but once i get it done ill let you guys know how it went(hopefully on a computer using ubuntu) 

wish me luck

and thanks ill be using this forum from now on for all of my ubuntu needs

---

### Post by halitech on 2007-03-03
good luck with the install and just so you know, I wiped my drive and went completely Ubuntu after only using the live cd for about 2 weeks and then dual booting for a month because I found I kept going back to windows when I couldn't figure something out in Ubuntu. having a backup system is a good thing but only having linux on your main system will force you to try to learn things. however, having said that, when you find yourself getting frustrated cause you can't figure something out, get up and walk away, go watch some tv, get a drink, have a smoke, anything to let the issue out of your mind so you can come back with a clear head.

---

### Post by Edgy_brewer on 2007-03-03
I wanted to put your mind at rest regarding the second question, re how to learn. I am literally just a few days old on my first linux system. I was new to the 'different' way of installing apps, still haven't got my head completely around compiling BUT almost everything I have wanted to do I have found people have been there before me.

 For example I had some broken dependancy message and i went into yahoo and typed 'ubuntu <error message>' and bingo the answer was on this forum!! This was the case with a few questions. I would now describe my system as 'cuddly' as I am learning more each hour that passes (is Ubuntu addictive anyone?). I scratched an old machine i didn't care about to learn on - low risk, but I AM impressed.

One last thing, I am keeping a log of my commands, I am sure there's quicker ways around how I navigate through directories on the command prompt, but the log of commands used, and what  i was working on is probably going to be a lifesaver in making this learning stick.

Thanks for listening!! Now go for it!

---

