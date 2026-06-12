---
title: "Newbee trying to get ubuntu installed"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by flash on 2005-10-09
I decided to try to get a machine going with ubuntu on it to try out. I tried the live disc and it ran real slow. So I decided that a full install might be the way to go to really try it out. Part way through the install (when it's undoing the packages) it locks up on "configuring xserver-xorg." So I shut it down and it came right back on. Now I'm on the sign on page with "richard@ubuntu:~$" and a flashing cursor. The machine is a pIII 500 ,128 ram, 4 g HD, a older video card. This is my first attempt at anything linux, but I have done a lot of windows stuff. I'm totally lost as what to do now. I've searched this sight and can't seem to come up with anything.

---

### Post by Kyral on 2005-10-09
Try opening your sources list ( sudo nano /etc/apt/sources.list  )  and  adding  the words multiverse and universe to the lines that say main and restricted on them and save it by hitting CTRL+X then answering yes when it asks you. Then do a sudo apt-get update && sudo apt-get dist-upgrade to apply any updates (always a Good Thing) then try sudo apt-get install xubuntu-desktop (I think thats the XFCE Meta Package now, someone correct me if I'm wrong)

This will update your computer and install XFCE, a lightweight GUI that should be perfect for your older system

---

### Post by aysiu on 2005-10-09
What happens when you type in ```
sudo dpkg-reconfigure xserver-xorg
```?

---

### Post by Fortigurn on 2005-10-09
I can't even get that far.  I downloaded the ISO, burned it to CD, and stuck it in a machine.  It won't boot.  :confused:

---

### Post by aysiu on 2005-10-09
[QUOTE=Fortigurn]I can't even get that far.  I downloaded the ISO, burned it to CD, and stuck it in a machine.  It won't boot.  :confused:[/QUOTE] Fortigurn, I'm sorry to hear your woes, but you're probably best off posting a new thread about your problem.

---

### Post by flash on 2005-10-09
I tried opening the list and there is a awful lot there to change. Am I looking at the right stuff? Plus, how do you exit from that program? As far as getting the upgrades, I just downloaded this yesterday and I don't have internet access on that machine. I also ran the reconfigure xserver and I get xserver is broken or not fully installed. My guess is it's not installed. I'm pretty lost right now, maybe I'm in over my head or there just isn't something I'm getting.

---

### Post by aysiu on 2005-10-09
Try following [these instructions](http://www.psychocats.net/sources.html), then typing ```
sudo apt-get update
sudo apt-get install xserver-xorg
```

---

### Post by flash on 2005-10-09
Wait a minute here, I don't have the slightist idea how to copy that stuff. I'm just getting my feet wet here and decided to try an install. If this is the kind of stuff I have to do to resolve this, I'm in trouble.

---

### Post by lean on 2005-10-09
Sounds like you are really unlucky. In 99% of people everything just installs. You are in the last percent :/

It seems that your system broke down during the installation. You could either try to install the whole thing again, or try the 'other' version. If you are running 5.10 (Breezy) try 5.04 (Hoary), and vica verca.

You could also try to login (if you know your username and password), and then write:
sudo apt-get update
sudo apt-get install ubuntu-desktop

If you are lucky this should solve all your problems.

---

### Post by flash on 2005-10-09
OK, when I ran update, I got 'E: The upgrade command takes no arguments'. When I ran install desktop, I got 'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem'. I got no idea what this means, good or bad? Could this be a bad CD that screwed up the install?

---

### Post by TheAreopagite on 2005-10-09
Hi Flash

Listen, you're trying to install linux on; "pIII 500 ,128 ram, 4 g HD, a older video card"

That's quite an old system, and now really kind of non-standard. Aysiu and others have tried to give you some sound advice, and they really know their stuff, but as a relative newbie myself I can see how difficult to understand and follow their instructions are.

If you put 'Michigan' and 'LUG' into google, you'll find a Linux Users' Group at Michigan Technological University. My advice would be to make contact with those guys and get some hands on help. Most LUG's are happy to help newbies install linux, and many even run special events to do just that.

Please try this, and let us know how you get on.

best wishes,

**TheAreopagite**

---

### Post by localhero on 2005-10-10
Hi,

I think, I have the same problem. I have installed ubuntu 5.04 nearly 10 times and now i tried ubuntu 5.10 and i have still the same problem. Problem comes when it tries start desktop. There is something wrong in xserver-xorg configurations.
I tried these commands: 
sudo apt-get update
sudo apt-get install xserver-xorg
sudo apt-get install ubuntu-desktop
and
sudo dpkg-reconfigure xserver-xorg
That last command looked good one, but i don't know what I should answer to those configurations.
My computer specs: AMD 64 3000+, 1024mb ddr400, ATI X800 256(pci-e).

I have also tried to install kubuntu 5.04, but it didn't worked. There were another problem.

Can the problem be in graphic card?

---

### Post by flash on 2005-10-10
I may have figured out the problem. I think it didn't like the video card I had installed. It was a pci card that might be w95 vintage. I changed it for a ati agp card and it seems to have configured it. I could never get past 72%, now it is at 76% and still going. I figured it might be something with the video after reading some more threads and a couple of other things that lead me to believe that xserver had something to do with video. At 82% now. Thanks for the help, you'll probably be hearing more from me when I try to get this going on my dsl.

---

### Post by Lord Illidan on 2005-10-10
And I would also have a go at upgrading the RAM from 128 to 196 mb.. I had a pc with a similar config, and that extra 64 mb made it extremely faster.

---

