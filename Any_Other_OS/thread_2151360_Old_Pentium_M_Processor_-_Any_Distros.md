---
title: "Old Pentium M Processor - Any Distros?"
date: 2013-06-04
forum: Any Other OS
---

### Post by punk4rock on 2013-06-04
Hi guys,

I apologise in advance if this is a stupid question or has been posted before :(

My Dad gave me an old laptop (Dell Inspiron D800 running with a Pentium M processor, it has 512MB of RAM and a 30GB hard drive) to try and get running somewhat well again. XP Home runs like a slug on it.


I've installed Lubuntu 12.04 (which runs like a dream) because of it's old kernel but I'm very aware of:

a) It is only supported until October 2013 

and 

b) If I upgrade it will also upgrade the kernel resulting in a kernel panic.

Are there any distros out there that won't result in kernel panic on a Pentium M processor, that will run on only 512MB RAM and that are also suitable for the beginner user.

I've looked and it seems to be a bit of minefield.

I've heard of "kernel pinning" and "fake PAE" but I'm not sure of their effectiveness and the "fake PAE" route also seems quite confusing to implement.

Many thanks guys! :D

---

### Post by Megaptera on 2013-06-04
You could have a look at Puppy Linux - very light but fully featured.
[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

### Post by punk4rock on 2013-06-04
> **Megaptera said:**
> You could have a look at Puppy Linux - very light but fully featured.
[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

I'd thought about Puppy but I've heard it's a bit tricky to install to hard disk (correct me if I'm wrong).

Also does anyone know if the current version of Debian (7.0 "Wheezy") would support the Pentium M processor? <-- scratch this, Wheezy looks like it uses 3.2 kernel which is on par with Lubuntu 12.04 :p

Thanks! :)

---

### Post by mips on 2013-06-04
Crunchbang & Manjaro Openbox will run fine on it. If Openbox is not to your linking install xfce (or lxde) as xfce minimal install without all the extra crap is light enough, I've done it on crunchbang just to test.

I would however suggest you get the RAM up to 1GB or more. This will make a big difference with any distro

For manjaro download the i686 image and for crunchbang download the 32-bit Waldorf for Older PCs (non PAE), you won't have to worry about future kernel updates etc.

[http://crunchbang.org/download](http://crunchbang.org/download)
[http://sourceforge.net/projects/manjarolinux/files/release/0.8.6/](http://sourceforge.net/projects/manjarolinux/files/release/0.8.6/)

They are both nice distros for that laptop and I've tried both on my old laptop which has a Celeron M based cpu (non-pae) but I upgraded my RAM, 512MB will work though.

---

### Post by mips on 2013-06-04
> **punk4rock said:**
> 
Also does anyone know if the current version of Debian (7.0 "Wheezy") would support the Pentium M processor?

See my post above about Crunchbang which is Debian 7 (Wheezy) and they have a version available with non-pae kernel.

---

### Post by sudodus on 2013-06-04
Pentium M has PAE capability, it only lacks the PAE flag. Therefore it is possible to use fake-PAE. I have prepared a way to install it. See the following link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

Lubuntu is the ultra-light-weight flavour of Ubuntu. I have an IBM Thinkpad T42 with Pentium M and it works very well with Lubuntu 13.04 installed with fake-PAE.

Edit: I can help you try it :-)

---

### Post by punk4rock on 2013-06-04
> **mips said:**
> Crunchbang & Manjaro Openbox will run fine on it. If Openbox is not to your linking install xfce (or lxde) as xfce minimal install without all the extra crap is light enough, I've done it on crunchbang just to test.


I think Crunchbang would be too confusing for them :( (I love it though :D)

Manjaro looks good but I don't know if I have enough experience with Arch to help my sister out if she runs into any trouble...

> **sudodus said:**
> Pentium M has PAE capability, it only lacks the PAE flag. Therefore it is possible to use fake-PAE. I have prepared a way to install it. See the following link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

Lubuntu is the ultra-light-weight flavour of Ubuntu. I have an IBM Thinkpad T42 with Pentium M and it works very well with Lubuntu 13.04 installed with fake-PAE.

Edit: I can help you try it :-)

I've heard of this but it looks really confusing :( (obvious noob is obvious haha) I wouldn't want to take up any more of your time.

I think I'll give Debian + LXDE a whirl and see how that goes.

Thanks again guys :)

---

### Post by mips on 2013-06-04
> **punk4rock said:**
> I think Crunchbang would be too confusing for them :( (I love it though :D)

Well install xfce or lxde for them...

---

### Post by punk4rock on 2013-06-04
> **mips said:**
> Well install xfce or lxde for them...

I didn't think of that, thanks :)

---

### Post by sudodus on 2013-06-04
> **punk4rock said:**
> I think Crunchbang would be too confusing for them :( (I love it though :D)

Manjaro looks good but I don't know if I have enough experience with Arch to help my sister out if she runs into any trouble...



I've heard of this but it looks really confusing :( (obvious noob is obvious haha) I wouldn't want to take up any more of your time.

I think I'll give Debian + LXDE a whirl and see how that goes.

Thanks again guys :)

The advantage with Lubuntu is that it is ready to run for multimedia and web browsing, and it is easy to add software.

My experience of Debian stable is that it is much harder to get these typical end user tasks running. So what you save avoiding fake-PAE is lost in installing and configuring software.

There are several distros that are based on Debian testing, for example Linux Mint Debian Edition (LMDE), that have multimedia and web software on par with the Ubuntu flavours, but (I'm citing LMDE's own web page)

> [h=5]4. How does LMDE compare to the Ubuntu-based editions?[/h] Pros:
 
[LIST]
[*]You don’t need to ever re-install the system. New versions of software and updates are continuously brought to you.
[*]It’s faster and more responsive than Ubuntu-based editions.
[/LIST]
 Cons:
 
[LIST]
[*]LMDE requires a deeper knowledge and experience with Linux, dpkg and APT.
[*]Debian is a less user-friendly/desktop-ready base than Ubuntu. Expect some rough edges.
[*]No EFI, GPT or secureBoot support.
[/LIST]


---

### Post by mips on 2013-06-04
> **sudodus said:**
> The advantage with Lubuntu is that it is ready to run for multimedia and web browsing, and it is easy to add software.

My experience of Debian stable is that it is much harder to get these typical end user tasks running. So what you save avoiding fake-PAE is lost in installing and configuring software.


Have you used Crunchbang? I don't recall having to install any extra stuff to make it work?

---

### Post by sudodus on 2013-06-04
I tried Crunchbang long ago, and don't remember exactly. You have probably tried it after me and know better about #! *mips* :-)

I have tried LMDE though, and I like it (but it has some rough edges, nothing to recommend to beginners).

But there is also [LXLE]("http://www.lxle.net/") (Lubuntu Extra Life Extension), that is promising support during the whole Ubuntu 12.04 LTS lifetime (until April 2017) for a special Lubuntu flavour, maintained by [ronniew]("http://ubuntuforums.org/showthread.php?t=2125764").

*@punk4rock*, you can also try LXLE, it might be perfect for this case, ready to run out of the box. The only small questionmark is if it wants more than 512 MB RAM. I have tried it with 1 GB.

---

### Post by DJWYMAN on 2013-06-05
I am glad I found this topic My mom gave me an old dell latitude 505d with a pentium M that had a dying hard drive that I made a PloP cd to boot to usb for and installed Lubuntu 12.04 on an external usb drive and it is running great and now I use it to play streaming videos and such on my tv but I was worried about the fact that it will not be able to be updated after October.  But now I am glad to know that there is a Lubuntu that is LTS in the way of LXLE.

---

### Post by mörgæs on 2013-06-05
As LXLE it built on Lubuntu 12.04 it has its share of bugs. I would recommend that you get to 13.04, though it takes a little more work.

---

### Post by punk4rock on 2013-06-05
I installed Debian 7 "Wheezy" on it with Gnome Classic as the DE and it is working like a dream, it's just a fraction slower than LXDE core. It idles at just over 100MB RAM, which I am very satisfied with. It seems to run faster my other half's netbook with Windows 7 and 1GB of RAM haha! :D

Very happy to have an up to date stable distro that works well on it :)

---

### Post by mips on 2013-06-05
Personally I would rather try XFCE as it will be lighter I reckon while still providing full functionality but if it works for you and you are happy then that's all that matters.

---

### Post by ronniew on 2013-06-05
> **mörgæs said:**
> As LXLE it built on Lubuntu 12.04 it has its share of bugs. I would recommend that you get to 13.04, though it takes a little more work.

may i ask what strange bugs in lxle? anything in particular?

---

### Post by DJWYMAN on 2013-06-05
> **mörgæs said:**
> As LXLE it built on Lubuntu 12.04 it has its share of bugs. I would recommend that you get to 13.04, though it takes a little more work.

I ended up taking your advise I used the "installed system" version of the fake PAE since that was easiest for me and I could do it from my other computer since I am using an external hard drive to begin with(it was actually easier than the way I installed 12.04 because I did not have to open up my other computer and unplug my harddrives, sure I could have installed it without doing that but it kept grub from mucking up things and it was the way I found on a tutorial on installing to a usb drive.)  While I did not have many bugs when i was running 12.04, 13.04 seems to be a little cleaner looking.

---

### Post by mörgæs on 2013-06-05
> **ronniew said:**
> may i ask what strange bugs in lxle? anything in particular?

Strictly speaking I didn't try LXLE, only Lubuntu 12.04. 

Pcmanfm, file-roller and gpicview all had their problems but are in a better condition now. 

Of course the choice depends on how much people use these applications.

---

### Post by punk4rock on 2013-06-05
> **mips said:**
> Personally I would rather try XFCE as it will be lighter I reckon while still providing full functionality but if it works for you and you are happy then that's all that matters.

Yeah I was pleasantly surprised at how well Gnome Classic ran.

I tried LXDE but there was a strange bug were half the desktop background is black :confused: and it seems to only run slightly faster compared to Gnome Classic...

I might try XFCE on it to see how it compares to Gnome Classic performance-wise.

---

### Post by VinDSL on 2013-06-05
> **punk4rock said:**
> I've installed Lubuntu 12.04 (which runs like a dream) because of it's old kernel but [...] 
Personally, I run [Peppermint OS]("http://peppermintos.com/") (for too many reasons to list here) on all of my portables (bootable USB stick / Netbook / Laptop).

Example...

[INDENT]**[COLOR="Sienna"]ASUS Eee PC 1000HD Netbook / Peppermint Two OS (Lubuntu Fork) / Conky 1.8.0 / ConkyWX 0.7.9-1[/COLOR]**

[[IMG]http://vindsl.com/images/vindsl-eeepc-30-dec-2012-1(650x381).png[/IMG]]("http://vindsl.com/images/vindsl-eeepc-30-dec-2012-1.png")

* Please note the CPU / kernel version.[/INDENT]

Peppermint OS is a Lubuntu fork.  

Don't let all the Cloud tweaks put you off (if you're not into Cloud computing).  It'll operate like any other conventional distro, if you wish.

Put another way, Peppermint OS doesn't force you onto the cloud, like Google Chrome OS.  But, it IS available (pre-programmed).  It's your choice, to use the Cloud computing tweaks, or not.  And, the tweaks don't get in your way, if you decide NOT to use them...

Good luck!  ;)

---

### Post by mastablasta on 2013-06-05
as i understand only the desktop in Lubuntu is not supported beyond oct 2013. so having 12.04 and adding a PPA for later LXDE versions should solve it, no? perhaps that's what LXLE did. i don't know.

---

### Post by ronniew on 2013-06-05
> **mörgæs said:**
> Strictly speaking I didn't try LXLE, only Lubuntu 12.04. 

Pcmanfm, file-roller and gpicview all had their problems but are in a better condition now. 

Of course the choice depends on how much people use these applications.

yea, file roller has a crappy bug that won't let you drag drop the archive to extract it sometimes. Really annoys me at times.

---

### Post by sudodus on 2013-06-05
> **DJWYMAN said:**
> I ended up taking your advise I used the "installed system" version of the fake PAE since that was easiest for me and I could do it from my other computer since I am using an external hard drive to begin with(it was actually easier than the way I installed 12.04 because I did not have to open up my other computer and unplug my harddrives, sure I could have installed it without doing that but it kept grub from mucking up things and it was the way I found on a tutorial on installing to a usb drive.)  While I did not have many bugs when i was running 12.04, 13.04 seems to be a little cleaner looking.

I'm glad the fake-PAE "installed system" works for you. If you have any issues or questions about it, please tell us. We need feed-back to improve it :-)

---

### Post by sudodus on 2013-06-05
> **punk4rock said:**
> Yeah I was pleasantly surprised at how well Gnome Classic ran.

I tried LXDE but there was a strange bug were half the desktop background is black :confused: and it seems to only run slightly faster compared to Gnome Classic...

I might try XFCE on it to see how it compares to Gnome Classic performance-wise.

I'm glad you found a distro and flavour that works well for you! This is the charm with linux, there are many good solutions.

Good luck :-)

---

### Post by DJWYMAN on 2013-06-05
> **sudodus said:**
> I'm glad the fake-PAE "installed system" works for you. If you have any issues or questions about it, please tell us. We need feed-back to improve it :-)

the instructions were pretty straight forward.  I did have to redo it though because I broke somethings trying to change the name of the computer and the user but that was my fault.

---

### Post by sudodus on 2013-06-05
Changing the name of the computer should be easy. I think it is enough to edit /etc/hostname and /etc/hosts. But I think it is easier to create a new user instead of changing the existing user. But don't remove the original one unless the new user is member of the sudo group and you have verified that it is able to perform system tasks.

---

### Post by DJWYMAN on 2013-06-05
> **sudodus said:**
> Changing the name of the computer should be easy. I think it is enough to edit /etc/hostname and /etc/hosts. But I think it is easier to create a new user instead of changing the existing user. But don't remove the original one unless the new user is member of the sudo group and you have verified that it is be able to perform system tasks.

well you hit the nail on the head as to what I did wrong on the user part.  on the host part I only changed the hostname and didn't change the hosts so it caused problems as well.  I just went ahead and started over and now it works fine.

---

### Post by sudodus on 2013-06-06
> **DJWYMAN said:**
> well you hit the nail on the head as to what I did wrong on the user part.  on the host part I only changed the hostname and didn't change the hosts so it caused problems as well.  I just went ahead and started over and now it works fine.

I will add tips about this in the wiki page instructions :-)

---

### Post by DJWYMAN on 2013-06-06
> **sudodus said:**
> I will add tips about this in the wiki page instructions :-)

good Idea so people don't make the same mistakes I made.

---

### Post by DJWYMAN on 2013-06-09
Well i ended up jumping back down to 12.04 last night.  I only need that computer to do 1 thing...Play videos online.  For what ever reason 13.04 did not want to do that or at least not well.  I was having issues with flash being glitchy and I had to steal the divx plugin from my desktop (with normal 13.04) to get divx to play but it was laggy.  once I put 12.04 back on all those issues went away.  

The way I see it is I have until october to come up with a new solution and by then.  Besides i have been thinking of buying a raspbean PI since it will run XMBC and this old laptop wont.

---

### Post by mips on 2013-06-10
> **DJWYMAN said:**
> Besides i have been thinking of buying a raspbean PI since it will run **XMBC** and this old laptop wont.

Have a look at [http://openelec.tv/](http://openelec.tv/) rather ;)

---

### Post by sudodus on 2013-06-10
> **DJWYMAN said:**
> Well i ended up jumping back down to 12.04 last night.  I only need that computer to do 1 thing...Play videos online.  For what ever reason 13.04 did not want to do that or at least not well.  I was having issues with flash being glitchy and I had to steal the divx plugin from my desktop (with normal 13.04) to get divx to play but it was laggy.  once I put 12.04 back on all those issues went away.  

The way I see it is I have until october to come up with a new solution and by then.  Besides i have been thinking of buying a raspbean PI since it will run XMBC and this old laptop wont.

It is a good idea to wait and see, as long as your present Lubuntu 12.04 is supported. 

Keep this in your mind until October: If still problems with flash in Lubuntu 13.04 and 13.10, I suggest that you try

- ***Xubuntu 12.04***, which has LTS until April 2015

- Continue with Lubuntu 12.04 but ***use only the simple window manager Openbox ***without any LXDE desktop environment. Openbox has LTS due to a special flavour of Kubuntu, so it should be safe. It is there already as a choice at the login screen, so you can try it. You see only a grey screen, but it is running. Right-click and you get a menu. Select the terminal window and you can do 'everything' from there (or choose the web browser, or exit directly from that menu).

---

### Post by DJWYMAN on 2013-06-10
> **mips said:**
> Have a look at [http://openelec.tv/](http://openelec.tv/) rather ;)

I would love to use that unforunatly xbmc does not support my graphics.  It requires at least an intel 950 and and i have and 845.

> **sudodus said:**
> It is a good idea to wait and see, as long as your present Lubuntu 12.04 is supported. 

Keep this in your mind until October: If still problems with flash in Lubuntu 13.04 and 13.10, I suggest that you try

- ***Xubuntu 12.04***, which has LTS until April 2015

- Continue with Lubuntu 12.04 but ***use only the simple window manager Openbox ***without any LXDE desktop environment. Openbox has LTS due to a special flavour of Kubuntu, so it should be safe. It is there already as a choice at the login screen, so you can try it. You see only a grey screen, but it is running. Right-click and you get a menu. Select the terminal window and you can do 'everything' from there (or choose the web browser, or exit directly from that menu).

I will keep that in mind.

---

### Post by mips on 2013-06-11
> **DJWYMAN said:**
> I would love to use that unforunatly xbmc does not support my graphics.  It requires at least an intel 950 and and i have and 845.


I meant for when you eventually get another machine.

---

### Post by DJWYMAN on 2013-06-11
> **mips said:**
> I meant for when you eventually get another machine.

oh ok yea I got you now.  Yea that's why I am thinking about getting one of those raspberry PIs as that would be a perfect solution to what I already do with this old thing.  

This thing was given too me and the fact that I got it working at all was a total surprise.  I mean heck it is like 10 years old, the internal hard drive is dead, and the poor old processor runs at 100% when doing anything other than just staring at the screen saver.  but it at this moment it is doing what I want it to do.


edit:

change to my current setups I ended up hooking up my desktop which is a much newer system up to my tv for now since I can run XBMC on it and plugged the old laptop up to my desktop monitor and I am going to use it as a desktop for now and see how long I can do that before I miss my more modern spec computer (2.66ghz core 2 duo, 2gb ram, radeon 5450 video card all still old stuff but newer than the setups we are talking about here)  or until I get something else I can use as a media player.

---

### Post by VanillaMozilla on 2013-06-11
EDIT:  I just looked up fake PAE for Pentium M.  It turns out you can ignore most of this message.

Wait a minute.  Are you sure you need another distro?  I'm currently running Lubuntu 12.04 and Ubuntu Classic on a Pentium III with 369 MB.  The release notes say you can't run the *installer* on a non-PAE system, but it doesn't say anything about updating a non-pae system.  Ultimately I updated to this version, and it just installed the *non*-PAE kernel.

And as it turned out, I have PAE, as you apparently do, even though I have no reason to use it.  There's more discussion of this here:  [http://ubuntuforums.org/showthread.php?t=2102509](http://ubuntuforums.org/showthread.php?t=2102509) .

Besides, I'm surprised you can't run Windows XP on it.  I use that old computer mostly for Windows.  I would say it runs even a bit faster than Lubuntu.

Yeah, I know you've been there and back again, but I have to wonder if it's for nothing.

---

### Post by DJWYMAN on 2013-06-11
> **VanillaMozilla said:**
> EDIT:  I just looked up fake PAE for Pentium M.  It turns out you can ignore most of this message.

Wait a minute.  Are you sure you need another distro?  I'm currently running Lubuntu 12.04 and Ubuntu Classic on a Pentium III with 369 MB.  The release notes say you can't run the *installer* on a non-PAE system, but it doesn't say anything about updating a non-pae system.  Ultimately I updated to this version, and it just installed the *non*-PAE kernel.

And as it turned out, I have PAE, as you apparently do, even though I have no reason to use it.  There's more discussion of this here:  [http://ubuntuforums.org/showthread.php?t=2102509](http://ubuntuforums.org/showthread.php?t=2102509) .

Besides, I'm surprised you can't run Windows XP on it.  I use that old computer mostly for Windows.  I would say it runs even a bit faster than Lubuntu.

Yeah, I know you've been there and back again, but I have to wonder if it's for nothing.
 
the problem with with the pentium m is not that it does not have PAE it is that it does not have the flag saying it has PAE which is why when you try to install a distro that is newer than 12.04 it will not let you without one of the PAE fake workarounds.

---

### Post by irv on 2013-06-13
Just for the record I have an old laptop with the M pentium processor running my sound system and the OS is Ubuntu Studio 12.04 (non PAE). It installed without a hitch and works great. It is a little slow booting, but once it is up and running with the software loaded it runs great. It has the FCE desktop which is very easy to use.
I didn't look back on all the posts in the thread, but in case this was not mention I thought I would jut post here.

---

### Post by essex lad on 2013-07-11
I use Bodhi 2.3 version
It runs very well on a non pae machine
Try it - I was very impressed with it

---

### Post by TNFrank on 2013-07-11
I guess I must have a "newer" Pentium "M" in my HP NC8230(buss speed 533MHz) because I've been running 12.04 flawlessly or any other Distro that I care to try for that matter.
I think it was just the older Pentium "M" with the 400MHz bus speeds that didn't have the PAE IIRC so just check your bus speed for the memory and if it's 533MHz then you'll be fine.

P.S.
This might give you some insight into the good ol' Pentium "M" processor. From what I've read they look like a pretty good CPU actually.
[https://en.wikipedia.org/wiki/Pentium_M](https://en.wikipedia.org/wiki/Pentium_M)

P.S.S.
Also, just saw this on DistroWatch, you might give it a try.
[http://sourceforge.net/projects/legacyoslinux/](http://sourceforge.net/projects/legacyoslinux/)

---

