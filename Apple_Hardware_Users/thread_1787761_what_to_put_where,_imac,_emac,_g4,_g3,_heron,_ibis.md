---
title: "what to put where, imac, emac, g4, g3, heron, ibis, eh?"
date: 2011-06-21
forum: Apple Hardware Users
---

### Post by chimerage on 2011-06-21
If this can be found elsewhere, please redirect me, but i've searched a bit already.  I have the small challenge of maintaining a fleet of computers at a small nonprofit farm school in the appalachian mountains.  most of our hardware is donated and old as rocks, and we run linux from principles and finance.  Folks love to drop their old boxes in our laps and call it generous, which it is, except that i get to try to figure out all the tech.  long backstory, hopefully to help understand the problem.

Not being mac-savvy, I am looking for suggestions on the best versions of ubuntu to install on several different computers.  Ubuntu is the preferred distro because we have a lot of non-tech people (staff and students) who get confused with too much difference between OS and appearances from box to box. the more we can have things seem the same, the better it is for everyone. 

(1)  imac g4, 800mhz, 512MB, 80G hd (tried 10.04, but way too slow.)
(1)  imac g4, 1g, 512 MB, 80G hd  (trying 10.04 now.)
(1)  emac from 2002 (can get specs, if needed)
(1)  emac from 2003  ("  "  "  ")
(2)  imac g3 from 2000 ("  "  "  ")

---

### Post by B_Free on 2011-06-29
[http://cdimage.ubuntu.com/ports/releases/8.04.1/release/](http://cdimage.ubuntu.com/ports/releases/8.04.1/release/)
update to 10.04 from there
You need a minimum of 256 ram
Check all your batteries (date and time) or just replace them. Linux needs accurate time. All problems that may arise, can be found on this forum. These are all PPC machines. NO INTEL! So, you need to take the advise only about these computers. Just perform a posts search at the top of the page.

or use Debian 

[http://www.debian.org/CD/http-ftp/#stable](http://www.debian.org/CD/http-ftp/#stable)
and pick which one you want .........cd or dvd

---

### Post by snafu006 on 2011-06-29
I have an old Imac G3 egg and its running ubuntu 10.04 just fine its cpu is 600mhz 1gb ram and 20gb HD. The only thing you will run into is the xorg.conf file the for the video card but its EZ to fix.

---

### Post by snowpine on 2011-06-29
When you say "tried it but it was too slow" do you mean you did a test install, or you tried it from the Live CD? If the latter, it is normal for the Live CD to be a bit slow and will be faster running from the hard drive after installing.

On older hardware you'll have better luck with a lightweight desktop environment (Xfce, LXDE, etc.) than the default Gnome.

I think 10.04 is a good choice (anything earlier is **unsupported**) but I also think B_Free has a good suggestion in Debian.

Good luck! :)

---

### Post by B_Free on 2011-06-29
I found the installer flawed in 10.04. That is why 8.04 then upgrade to 10.04 was suggested.

---

### Post by snowpine on 2011-06-29
> **B_Free said:**
> I found the installer flawed in 10.04. That is why 8.04 then upgrade to 10.04 was suggested.

OK, good advice! :) Have you tested whether this still works since 8.04 went "end of life" in April?

---

### Post by B_Free on 2011-06-29
Yes!

---

### Post by snafu006 on 2011-06-29
> **B_Free said:**
> I found the installer flawed in 10.04. That is why 8.04 then upgrade to 10.04 was suggested.

The install is not flawed in 10.04 it install the first time i install it. here is a post where i helped a guy in stall 10.04 on a Imac G3 and picturs i took of my little buddy. 


[http://ubuntuforums.org/showthread.php?t=1689694&page=2](http://ubuntuforums.org/showthread.php?t=1689694&page=2)

and this is the Xorg.Conf files you will need. 

[http://mac.linux.be/content/xorgconf-files](http://mac.linux.be/content/xorgconf-files)

---

### Post by snafu006 on 2011-06-29
what computer are you working on frist?

---

### Post by B_Free on 2011-06-29
The installer can't find the hard drive. This is either the Live CD or the alternative. If you have a link to the version you speak of, let everyone know. I have 6 different CDs or DVDs that say you are wrong.

---

### Post by snafu006 on 2011-06-29
> **B_Free said:**
> The installer can't find the hard drive. This is either the Live CD or the alternative. If you have a link to the version you speak of, let everyone know. I have 6 different CDs or DVDs that say you are wrong. 

Go here [http://cdimage.ubuntu.com/ports/releases/10.04/release/](http://cdimage.ubuntu.com/ports/releases/10.04/release/)  i can remember if i used Alternative or DeskTop But find the one with the old installer its better. but i think i just use [http://cdimage.ubuntu.com/ports/releases/10.04/release/ubuntu-10.04-desktop-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/10.04/release/ubuntu-10.04-desktop-powerpc.iso)

---

### Post by rsavage on 2011-06-30
Just thought I'd back up what snafu006 is saying.  Not had a problem installing with the 10.04 live cd at all.  The only problems I've had when installing ubuntu is with the alternate and minimal CDs, but that was because I had 'burned' them to a USB stick I think.  I've solved that (for the alternate certainly) and have written the solution on the forum for others.
 
I'm going to install lubuntu.  I'll probably post on the forum how I get on.

---

### Post by LtPitt on 2011-06-30
If I can suggest MintPPC is really the best you could ask for those old machines...
I've turned my 350 mhz imac into a wonderful and fully automated jukebox (controlled by android remote).

[http://ubuntuforums.org/showthread.php?p=10975937#post10975937](http://ubuntuforums.org/showthread.php?p=10975937#post10975937)

---

### Post by snafu006 on 2011-06-30
i know mintppc is really good but i dont like it as much ubuntu 10.04 with xubuntu just as fast.

---

### Post by LtPitt on 2011-06-30
xubuntu is everything but fast and light (at least in my humble experience)

LXDE is faster...
enlightment faster than LXDE...
And fluxbox is the fastest :)

I choose mint's lxde because is a good compromise between graphics / functionality / speed.

But everyone has preferences :)

---

### Post by snafu006 on 2011-06-30
> **LtPitt said:**
> If I can suggest MintPPC is really the best you could ask for those old machines...
I've turned my 350 mhz imac into a wonderful and fully automated jukebox (controlled by android remote).

[http://ubuntuforums.org/showthread.php?p=10975937#post10975937](http://ubuntuforums.org/showthread.php?p=10975937#post10975937) thats because you have a 350 mhz IMac you will never be able to run xubuntu as well as i can. i an just saying if this guy wants help he need to run 10.04 LTS

---

### Post by rsavage on 2011-07-01
@LtPitt Installing MintPPC to create a jukebox is probably a little OTT. MintPPC seems to install everything and then the kitchen sink. So it is not the lightest. A minimal 10.04 ubuntu installation is really quick to boot. You can then add what you want. There are non graphical music players.  If you are just running a single xorg application then possibly you don't need a window manager at all (not sure about pop-ups?)? You can certainly install fluxbox in ubuntu. You can of course install LXDE and there is a distro called lubuntu which is based around this. All installable on powerpc. 
 
To answer the original question. I would install lubuntu if the machines are really very slow. The reason I wouldn't intall mintppc is becasue presumably the school has intel machines also? You could install lubuntu on these as well so they are all the same. There is also an edubuntu project for schools. Don't know much about it, but you could install their packages on an existing lubuntu setup maybe? [http://www.edubuntu.org/download](http://www.edubuntu.org/download)
 
I will be having a play with lubuntu over the next few days.

---

### Post by LtPitt on 2011-07-01
@Rsavage
Thinking about what you wrote I realize you're right...
I'd just neet to install a superminimal system with just what I need.
But since I'm not very skilled I thought about getting a distro that has a lot of applications pre-installed and a robust ppc repository so I'd not run into dependecies problems.
I needed graphical players because I've found remote control for android and I got just banshee and rhythmbox on the market :)



Reading better Lubuntu would be a good choice because of the uniformity (and performance) between one mac and the other for the question that opened this thread.

Excuse me for being a OT too :)

---

### Post by linuxopjemac on 2011-07-01
The good thing about Linux is: there is plenty choice :)

---

### Post by JYx70 on 2011-07-23
> **B_Free said:**
> The installer can't find the hard drive. This is either the Live CD or the alternative. If you have a link to the version you speak of, let everyone know. I have 6 different CDs or DVDs that say you are wrong.

I had this problem with my g3 blue & white... I reinstalled mac os 8.6 and updated firmware from there and formatted the HD with disk utility. Apparently linux needs a HFS, not HFS+, partition to communicate with apple hardware??? Anyway, I formatted the HD with "swap" 1GB = standard, the 2nd partition on the rest of the HD "OS" = journaled. I also used the ubuntu 8.04 live cd, which was then able to recognize the HD then updated to 10.04, after install of and applying update manager from 8.04.
I would go with the cd version and make sure you are burning it at slowest speed possible, either on a linux or apple machine.

---

### Post by Denver79 on 2011-07-25
> **JYx70 said:**
> I had this problem with my g3 blue & white... I reinstalled mac os 8.6 and updated firmware from there and formatted the HD with disk utility. Apparently linux needs a HFS, not HFS+, partition to communicate with apple hardware??? Anyway, I formatted the HD with "swap" 1GB = standard, the 2nd partition on the rest of the HD "OS" = journaled. I also used the ubuntu 8.04 live cd, which was then able to recognize the HD then updated to 10.04, after install of and applying update manager from 8.04.
I would go with the cd version and make sure you are burning it at slowest speed possible, either on a linux or apple machine.

I have a similar problem.:popcorn:

---

### Post by blueridgedog on 2011-07-25
I suggest you take one machine at at time and work through the install via a dedicated thread.  Each may have singular issues other than age that may need to be sorted out.

---

