---
title: "Internet Radio Problem 2"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-12-04
Sorry ....seems my screen dump did not attach to previous post.
Running Ubuntu 7.10

When I try to connect I get:

"xine-plugin: no mrl found in playlist" !!

Having investigated the forum I did download Real Player but cannot install it.... please see
screen dump attached.

How can I proceed please?


Thanks


Bernard

---

### Post by jken146 on 2007-12-04
Please don't start a multiple threads on the same topic.

You could try Helix Player (a free alternative to real player) - it's in the repositories.

---

### Post by candtalan on 2007-12-04
if you really want the proprietary item (a binary) then these instructions are a slightly edited vwersion of what is offered at
[http://www.real.com/%28rnnocache%29/moreinfo/playerplus_install.html?src=080204os_linux_1_2_2_1_1_2&date_code=080204&pagesrc=080204os_linux_1_2_2_1_1_2&product=playerplus&system=linux](http://www.real.com/%28rnnocache%29/moreinfo/playerplus_install.html?src=080204os_linux_1_2_2_1_1_2&date_code=080204&pagesrc=080204os_linux_1_2_2_1_1_2&product=playerplus&system=linux)

Installation Instructions
(use your own password when requested)
- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "sudo chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

CD into the folder containing the binary, might be /home/user1/downloads (??)
- Run the .bin file by typing "sudo ./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

a place to install into might be for example
/opt
and you might want to accept a system wide install (I did)

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!


note - There are open alternatives to realplaer, and I use mplayer now, with mozilla mplayer plugins, and also install win32codecs.

---

### Post by bern1939 on 2007-12-04
Thanks.....installed Real Player as you suggest but still having problems.

When I click on a radio station I get the following:

"Could not find an appropriate hxplay or realplay in the system path to use as an embedded player"

I wonder what precisely that means? What shd. I do please.


Thanks


Bernard

---

### Post by fenian on 2007-12-04
The best way to listen to Real Streams is to use mplayer with the mozilla plugin.To install open a terminal and type...
> 
sudo apt-get install mplayer mozilla-mplayer

You can the listen to your station by connecting with firefox,connectin through the mplayer GUI or directly from the terminal with a command like this (for BBC1)...
> 
mplayer -playlist [http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram](http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram)

---

### Post by TekNullOG on 2007-12-04
Oh, I see that people are answering you. I answered your previous thread about this. (or at least was attempting to)

What type of music are you trying to listen to with Real Player? (off-topic) The only station worth listening to that is in Real format is BBC Radio.

---

### Post by candtalan on 2007-12-04
> **bern1939 said:**
> Thanks.....installed Real Player as you suggest but still having problems.
When I click on a radio station I get the following:
"Could not find an appropriate hxplay or realplay in the system path to use as an embedded player"
I wonder what precisely that means? What shd. I do please.
Bernard

It might mean it needs plugins, not sure. When I installed it put mozilla plugins in ok.
Did you choose the 'system' option when installing realplayer binary?
Someone may be able to comment helpfully about path?

---

### Post by bern1939 on 2007-12-04
The real Player is contained within a folder in my 'HOME' directory.

When I tried to run the BBC site address I got the attached screen dump.....seemed to start but buffering remained at zero !!!

I wonder how this can be fixed. By the way the mplayer and plugins are already installed.

Thanks


Bernard

---

### Post by bern1939 on 2007-12-04
Just to attach the screen dump from the previous post.


Thanks

Bernard

---

### Post by candtalan on 2007-12-05
> **bern1939 said:**
> The real Player is contained within a folder in my 'HOME' directory.
When I tried to run the BBC site address I got the attached screen dump.....seemed to start but buffering remained at zero !!!
I wonder how this can be fixed. By the way the mplayer and plugins are already installed.
I do not know enough about it to be sure, but
did you use the file RealPlayerGOLD.bin (?)
did you  say Y to the offer to install system wide?
did you use sudo before each command (which would I think give the option late to choose system wide install?

Installing proprietary binaries in linux is fairly unusual, so be aware you are into fringe activities, it is not like windows world like that.

---

### Post by bern1939 on 2007-12-05
Thanks

From the terminal this is the file I used to install the RealPlayer:

bernard@bernard-desktop:~$ ./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin

It did install and sits in my home directory now.

The attached screen dump shows what happens when I try to connect to the BBC... no activity...

Bernard

---

### Post by candtalan on 2007-12-05
'./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin'
mmm. this is not the Real Player binary installer which I have used, and I do not know enough to comment I think

---

### Post by bern1939 on 2007-12-06
I still cannot get the Internet radio service working in Ubuntu 7.10

From previous posts I have carried out the suggestions and have moved the problem on a little...but still no activity .....

Please see the attached 2 screendumps. They are the result of I  trying to open the BBC channel with the two different players!!

What do you think might be the problem?

Thanks


Bernard

---

### Post by bern1939 on 2007-12-06
As an additional point to my previous post:

Could this _**terminal result**_ have anything to do with I being unable to get Internet Radio woring in Ubuntu 7.10?

bernard@bernard-desktop:~$ sudo aptitude install libstdc++5

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Reading package lists... Done

Building dependency tree       

Reading state information... Done

Reading extended state information       

Initializing package states... Done

Building tag database... Done      

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

bernard@bernard-desktop:~$ 


I did suceed in downloading RealPlayer 10.0.9.809(gold) and it resides now in a RealPlayer folder in my 'HOME' folder.

Many thanks ... I might get there yet!

Bernard

---

