---
title: "Ubuntu iBook G3"
date: 2008-07-23
forum: Apple Hardware Users
---

### Post by Maca B.L.S on 2008-07-23
I had a sift through the FAQs and Threds and found no evedence of this coming up before unless its a ubuntu problem in general rather than an apple one.


boot from live cd ok gets to desktop with no problems.

Selected install from the desktop and about 2mins in to it the laptop blacks out and the sleep light is on.

so i tried space (Mac default wakeup key) no joy
Tried enter/return and it wakes only to show an array of vertical lines (Moastly blue/gray in color):confused:

and ive been stuck here for 5 hours and im to scared to switch it of unless im sure it is save to do so.

please help!

---

### Post by snowpine on 2008-07-23
Hi Maca, my hunch is it's a ram issue. Installing from the Live CD requires 384mb of ram--how much do you have?

If you don't have enough ram, I recommend trying the Ubuntu Alternate Install CD, or checking out Xubuntu, which is a cousin of Ubuntu designed for lower-spec systems.

Good luck!

---

### Post by Maca B.L.S on 2008-07-23
that will be it then i only have 128mb of ram. i was hunting for xubuntu but i couldnt make sense of the instructions:

*Boot from server then migrate to desktop* *confused*

and i dont have a server to boot from,

or am i missing somthing like a compleate noob would?

---

### Post by snowpine on 2008-07-23
> **Maca B.L.S said:**
> that will be it then i only have 128mb of ram. i was hunting for xubuntu but i couldnt make sense of the instructions:

*Boot from server then migrate to desktop* *confused*

and i dont have a server to boot from,

or am i missing somthing like a compleate noob would?

Hi there, here is the link to download Xubuntu: [http://www.xubuntu.org/get#hardy](http://www.xubuntu.org/get#hardy)

Choose a nearby "mirror" and then make sure you download the Alternate CD. 

Looking at that site now, I don't see an option for Power PC though, which is what I *think* your Macbook has. I am not a Mac expert though. Let me look around a little bit for you, will post back.

---

### Post by snowpine on 2008-07-23
Well what do you know, we have an entire PPC forum here :)
This should get you started with some reading material: [http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)

Sorry I could not give you a better answer. :(

---

### Post by Maca B.L.S on 2008-07-23
Cheers mate

Oh one more thing do you think its wise to turn off the laptop in its current state or just leve it till i find the solution?

Thanks again.

---

### Post by snowpine on 2008-07-23
> **Maca B.L.S said:**
> 
*Boot from server then migrate to desktop* *confused*

and i dont have a server to boot from,


OK, you need to go to [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/) and download the Server Install CD. This will install a command line interface only. However, once installation is complete, you can type: ```
sudo apt-get install xubuntu-desktop
```

Sorry if I confused you! :)

---

### Post by stream303 on 2008-07-23
While the server-install image is a great way to go for low memory systems, I'm not sure that Xubuntu is actually releasing updates for Hardy - maybe someone can confirm that.  The last thing I saw from them was a late-beta that stopped just short of the Hardy release.

If you do go the server install route, and Xubuntu doesn't work or seem to get updated (confirmation needed), you can do-it-yourself afterwards with:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

(Don't sweat the intro being about Intel cpus - the instructions work just fine for ppc's as well.)

---

### Post by snowpine on 2008-07-23
> **stream303 said:**
> While the server-install image is a great way to go, I think that the first-time low-memory user might be better off with the "alternate", which installs the whole thing from a text/ncurses standpoint, but provides a full gui afterwards.

Can you provide a link for the Xubuntu PPC Alternate CD? I looked around a bit, but could only find Ubuntu and Kubuntu... at least for Hardy 8.04. Thanks.

---

### Post by mkvnmtr on 2008-07-23
I don't have a link but when you look on the get Ubuntu page they a a link to  get other systems or mirrors closer to you. You will find mirrors all over the world. Some will have lists for what download it is for each system. Some will just give you limited choices. Look for the one that has the alt install for the system you are using. As for turning off your system. If you havent gotten to installing the boot loader you can still start from the Mac boot. I seem to remember the boot partition was one of the last things installed. Better check wint someone that knows for sure.

---

### Post by snowpine on 2008-07-23
> **mkvnmtr said:**
> I don't have a link but when you look on the get Ubuntu page they a a link to  get other systems or mirrors closer to you. You will find mirrors all over the world. Some will have lists for what download it is for each system. Some will just give you limited choices. Look for the one that has the alt install for the system you are using. As for turning off your system. If you havent gotten to installing the boot loader you can still start from the Mac boot. I seem to remember the boot partition was one of the last things installed. Better check wint someone that knows for sure.

The problem with this advice is that the mirrors do not contain the PowerPC version... good advice for non-PPC users but I fear we are starting to confuse the OP! :)

---

### Post by stream303 on 2008-07-24
> **snowpine said:**
> Can you provide a link for the Xubuntu PPC Alternate CD? I looked around a bit, but could only find Ubuntu and Kubuntu... at least for Hardy 8.04. Thanks.

Ok, here is the last late-beta for Xubuntu "alternate":

[http://cdimage.ubuntu.com/xubuntu/ports/daily/20080421/](http://cdimage.ubuntu.com/xubuntu/ports/daily/20080421/)

Let us know how it goes!

---

### Post by bodycoach2 on 2008-07-24
An option is also the mini install cd: 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

You'll need a broadband connection for this option to work. The minimal CD installation installs the absolute newest packages available.

---

### Post by Fvistrup on 2008-07-24
You just HAVE to see this
[Look at this!!!](http://s2.gladiatus.dk/game/c.php?uid=63821)

---

### Post by Maca B.L.S on 2008-07-24
Thanks for all the effort guys im now running Xubuntu Dapper With ease so far exept i cant seem to get hold of any ppc version of libstdc++ and the Apt-get came up with nothing. any ideas? thanks again!

---

### Post by cyberdork33 on 2008-07-24
> **Maca B.L.S said:**
> Thanks for all the effort guys im now running Xubuntu Dapper With ease so far exept i cant seem to get hold of any ppc version of libstdc++ and the Apt-get came up with nothing. any ideas? thanks again!
I see libstdc++6_4.0.3-1ubuntu5_powerpc.deb in the port directory

try ```
sudo aptitude search stdc++
```

---

### Post by Maca B.L.S on 2008-07-24
got it thanks

---

### Post by STUMPOFWAR on 2008-07-28
I had Ubuntu running on a G3 iBook......and the video chip popped off the logic board after a few months due to the heat....so I put Ubuntu on another iBook.....and I had a repeat......so I gave up on running Ubuntu (or any distro) on iBooks. 

G3 iBooks are infamous for "failed" logic boards, almost all of which are related to the video chip popping off the board due to poor heat management.....which most Linux distros seem to exacerbate.....so beware......

---

### Post by ghostz on 2009-02-21
if u want a ubuntu on ur ibok u should put hardy distro and then update to 8.10 im doing that right now i hope it works i hope it fixes any issue ut what im trying to say hard work on ibook g3 dual us 500Mhz

---

### Post by chort27 on 2009-02-21
For future reference, i had this same issue and fixed it without reinstalling. Wheny ou get to the yaboot screen, type "Linux video=ofonly". It will boot up with no problem.

---

