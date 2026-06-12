---
title: "Advice on installing Ubuntu on old PC please"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by jimbojames on 2007-07-25
Hi All,

I have been given 2 Compaq Deskpro's which have PIII (3) processors, 20 GB HDD's ans 64 MB Ram.  My aim is to do a fresh install on both (no windows!! hurray) and have one of them as a webserver.
I have an Ubuntu 7.04 Install disk but it isn't working???
Could someone tell me what the best version of Ubuntu to use is and where I would get it from?

Many thanks,

James.

---

### Post by Motoxrdude on 2007-07-25
Since they have low ram you have to use an alternative install cd. You can download it from ubuntu's main website. 
It basicly just installs ubuntu but without a gui (graphic user interface).

---

### Post by tgm4883 on 2007-07-25
Thats pretty limited RAM.  You're going to want to use Xubuntu on any that will have a gui, and the server disk on the webserver.  You will probably need to get an alternate disk of Xubuntu

---

### Post by Daveth on 2007-07-25
not working when you attempt to load Ubuntu onto the hard drive, or as a live cd? I think you ram may be too small, as this notes:
"If you have a computer with 128 MB of RAM or less, you will not be able to use the Desktop CD to install Ubuntu. For low-specification computers, the Desktop CD is too resource-intensive to be running and trying to install Ubuntu at the same time."

Is your motherboard capable of taking more RAM, and does it have space to upgrade?

There are, of course, other linux distros that run on very sparse resources.

---

### Post by tgm4883 on 2007-07-25
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by sad_iq on 2007-07-25
Read this guide also...it will help you a lot: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)
 Also if possible try swapping memory from one system and put it in another...it will be better for you!!!

---

### Post by jimbojames on 2007-07-25
I am so stupid sometimes!!!!  Yes - I can take the RAM out of one and put in the other to give me a wopping 128MB RAM (LOL).

What was happening was when I inserted the Ubuntu CD and restarted, I chose 'Install' and it all seemed to be going ok till after about 10 mins, it started to report that it was having to kill processes - I assume due to the lack of RAM???

Taking in to account the above, if I add the other 64 MB stick to the machine in question to give me 128MB, do you think the GUI 7.04 will work or should I go down the Xubuntu route?

PS - Thank you all for your quick responces - much appreciated :):):):):)

---

### Post by sad_iq on 2007-07-25
You may still get errors with 128...just try the LiveCd for a few tasks(open a few browser windows, play some solitaire, whatever) and see if it crasher...if it does it probably will do the same when you'll try to install! And xubuntu sounds better for that amount of ram!!!

Edit: Also when you burn your disk make sure you do it at a low speed(4x), check md5 sum, check your memory when you boot it (just to make sure :) )...if you fail to do these things you are prone to get failures at the install process or in an installed system!!!

---

### Post by jimbojames on 2007-07-25
ok - cheers sad_iq.  Do you know where I can get an install CD for Xubuntu?

---

### Post by sad_iq on 2007-07-25
There you go: [http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by tgm4883 on 2007-07-25
The live environment gets loaded into the RAM.  This is why you cannot use it for an install on a low ram system.  If you choose the alternate cd, it will take you through a text based installer, which consumes less ram.  Once you have it installed, it should run better.

---

### Post by gjrepicky on 2007-07-25
Another thought -- if your system has room, would you consider adding ram?  You may be able to get ram relatively inexpensively from a small computer repair shop.  I recently picked up a 128 MB stick of PC 100 ram for $25 to bring my system (800 MHz P3, 20 MB HD) up to 256 MB.  Made a huge difference -- I can't believe the difference in performance compared to 128 MB, and would make your install problems go away.  (I used the "alternate install" CD to install Feisty w/ 128 MB).

G

---

### Post by sonofusion82 on 2007-07-25
how about Damn Small Linux (DSL) or Puppy Linux?
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
[http://www.puppylinux.org/](http://www.puppylinux.org/)

both are designed for machines with low resources...
DSL claims to work with as little as 16MB RAM.

---

### Post by FleetAdmiral74 on 2007-07-25
With that low, I would suggest going right to fluxbuntu instead if xubuntu. Or even Damn Small Linux.

edit: ok, I was a bit too slow.

---

### Post by Paulmd on 2007-07-25
> **jimbojames said:**
> Hi All,

I have been given 2 Compaq Deskpro's which have PIII (3) processors, 20 GB HDD's ans 64 MB Ram.  My aim is to do a fresh install on both (no windows!! hurray) and have one of them as a webserver.
I have an Ubuntu 7.04 Install disk but it isn't working???
Could someone tell me what the best version of Ubuntu to use is and where I would get it from?

Many thanks,

James.


You need 256MB or more ram to run the desktop.  Fortunately PC-133 is easy to find cheap (pulled from other machines)

You should have 3 slots for ram on most Deskpros in that generation.

---

### Post by jimbojames on 2007-07-26
Ok - I've installed Xubuntu and it's up and running with no (initial) problems as far as I can see!! :)

Now for stage 2 - I am fairly knowledgable when it come's to computers and how they work, it's just Linux I'm a complete noob with.  Am I right in thinking I can now install Apache on to my machine over Xubuntu so that I can point my domain address at my IP address and get my router to forward all port 80 requests to my Linux machine where Apache will listen out for the requests and present my visitors with my required homepage?

If so - is there a certain version of Apache I shoudl be using that wont be so heavet on the system?  Where can I get a version and is there anything I should know to get my website up and running?

Thanks in advance,

James.

---

### Post by jimbojames on 2007-07-27
bump :)

---

### Post by zach12 on 2007-07-27
xubuntu would work well with that computer 
i would install xubuntu on it

---

### Post by jimbojames on 2007-07-27
Thanks for the reply but that issue is now sorted, my question was relating to apache (see above)

---

### Post by tomcheng76 on 2007-07-27
if you dont need gui
install xubuntu alternative CD would be great

if you need a gui, see [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

---

