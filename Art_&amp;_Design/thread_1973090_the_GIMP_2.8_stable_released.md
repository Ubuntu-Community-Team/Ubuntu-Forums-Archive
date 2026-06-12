---
title: "the GIMP 2.8 stable released"
date: 2012-05-04
forum: Art &amp; Design
---

### Post by BcRich on 2012-05-04
Yay, it's finally here after 3.5 years of waiting ;) the latest 2.8 stable version of the GIMP with features including 
layer groups, 
on canvas text editing, 
cage transform tool 
and single-window mode (to name a few). 

the official release notes
[http://www.gimp.org/release-notes/gimp-2.8.html](http://www.gimp.org/release-notes/gimp-2.8.html)

---

### Post by *^kyfds( on 2012-05-04
i prefer paint.net over gimp.
 
the selection tool doesen't behave the way i'm used to.

---

### Post by BcRich on 2012-05-04
> **Thehumorouscheese said:**
> i prefer paint.net over gimp.
 
the selection tool doesen't behave the way i'm used to.
lol :D looks like it uses the .NET framework so I'm guessing it doen't have a native Ubuntu version?

---

### Post by *^kyfds( on 2012-05-04
> **BcRich said:**
> looks like it uses the .NET framework so I'm guessing it doen't have a native Ubuntu version?

i think it might work in wine, but i haven't tried it yet.

it's the main reason i dual boot with windows

:lol:

---

### Post by BcRich on 2012-05-04
> **Thehumorouscheese said:**
> i think it might work in wine, but i haven't tried it yet.

it's the main reason i dual boot with windows

:lol:

out of interest, is GIMP lacking features that paint.NET has or do you maybe prefer it's interface, or something else?
I use GIMP for making textures mainly, and two of the main features it lacked in 2.6 was absence of layer groups and a proper cage transform tool (which both help immensely regarding texture creation) so I guess that's probably what I'm most happiest about in this release :)

---

### Post by husnos on 2012-05-04
try mypaint

[http://mypaint.intilinux.com/](http://mypaint.intilinux.com/)

---

### Post by BcRich on 2012-05-04
> **husnos said:**
> try mypaint

[http://mypaint.intilinux.com/](http://mypaint.intilinux.com/)
I didn't initially recommend mypaint cause it's a paint program, GIMP and paint.NET are image manipulation programs. Although with a name like paint(...) I would have also thought it was a paint program if I hadn't checked out their website which likens it to photoshop and the gimp. 
:)

---

### Post by Dry Lips on 2012-05-05
I posted this question in a thread in the Cafe, but I didn't get any help, so I'll repost it here:

[I]"Have anyone here tried Gimp 2.8 in KDE? When I do something to the  image, the toolbox and layer dialogues disappear, and I have click on  them from the panel or the menu in order to bring them up again. 

They don't disappear when I enable Single-Window mode, though.[/I] *"*

---

### Post by BcRich on 2012-05-05
> **Dry Lips said:**
> I posted this question in a thread in the Cafe, but I didn't get any help, so I'll repost it here:

[I]"Have anyone here tried Gimp 2.8 in KDE? When I do something to the  image, the toolbox and layer dialogues disappear, and I have click on  them from the panel or the menu in order to bring them up again. 

They don't disappear when I enable Single-Window mode, though.[/I] *"*

Hi Dry Lips
I'm still in the process of installing GIMP 2.8 in ubuntu 10.10. Since I havn't come across any binaries, and last time I checked Ubuntu repos still has 2.6 (which probably won't change for a while) also I'm not keen on using the otto-kesselgulasch PPA cause it's for 12.04 and requires somewhat drastic purging (from what I've read) it seems like installing from source is my only option.
BTW do you still have older 2.6 or other GIMP installed? cause you r likely to run into problems with one of them if you did not pass a separate prefix to the configure script during compilation. eg
```
 ./configure --prefix=/opt/gimp-2.8
```
but like i said I haven't tried this yet, so maybe some one else has something more to add...

---

### Post by Ryupower on 2012-05-05
Oh my gosh, AWESOMENESS!!!
Thanks for sharing!!! :)

---

### Post by charlessmall18 on 2012-05-06
As a newcomer to Ubuntu, I am wondering how long it takes Ubuntu to make the latest version of programs available for easy installation and how we find out that they are available? Not only The GIMP, but Calibre and Mozilla Thunderbird have newer versions out than Ubuntu carries. The Calibre site has some really scary looking terminal commands that got the the latest version of Calibre for me. Is there someplace I can find such step-by-step direction of what to do to install The GIMP 2.8? I am a technical writer/illustrator and I use The GIMP professionally every day. So I would like to upgrade ASAP.

---

### Post by LillyDragon on 2012-05-06
Er, v2.8 has been in the Software Center since some time before the announcement on GIMP's official site. [s]Or at least that's how it is on Precise, dunno if 11.10's repos differ in this case. Open Arena's been at v8.8 for quite a while, but only 8.5 is on the Software Center.[/s] EDIT : Disregard if you like, I have a gut feeling I'm seeing 2.8 in the Software Center because of that unofficial PPA I added. [http://ubuntuforums.org/showthread.php?t=1972088&page=2](http://ubuntuforums.org/showthread.php?t=1972088&page=2)

Either way, I've been loving all the improvements, on both Windows and Ubuntu! Finally, I don't have to juggle multiple windows into comfortable positions with Single Window mode, and grouping layers and paths makes things so much easier to sift through in more complex project files! ^_^ I'm no advanced user yet, (mostly intermediate) but this is definitely everything that I felt like GIMP's been missing so far.

---

### Post by catlover2 on 2012-05-06
Ha. I hadn't even noticed that The GIMP has been upgraded. [s]The first glitch that I see is that none of the drawing tools work, period. I guess I have some fiddling to do..[/s] Lol, I just accidentally selected a tiny region and didn't notice.

@Dry Lips: I'm using KDE 4.8.3 with QtCurve, and everything looks fine here.

---

### Post by BcRich on 2012-05-06
@Ryupower : It's my pleasure :)
@ charlessmall18 : Welcome to the Ubuntuforums! :)
What version of ubuntu are you using? If you are using a version as old as the one I'm using 10.10 then you're probably going to need to compile it from source, which I'm sure sounds like a terrible suggestion for newcomers, sorry :(
The problem with the current version of the GIMP 2.6  in the Ubuntu repositories is when the latest version of Ubuntu is released the repositories favour stable versions rather than the latest versions of software such as GIMP, Calibre etc. Since the GIMP's 2.8 stable version release just missed the Ubuntu 12.04 release (by a few weeks/days as far as I know), the current stable version which was 2.6 (at the time) was used. Generally the official Ubuntu repositories will not reflect the latest version of software until it becomes stable but will release patches that are usually related to bug fixes (and generally not feature upgrades). What this means is that you can expect to see the 2.8 version of the GIMP in Ubuntu 12.10 and probably only expect to see patches for GIMP 2.6 updated in the Ubuntu repositories till then. But who know's maybe they'll make an exception this time :)
Anyway my suggestion to you is, if possible, get the latest version of Ubuntu 12.04 and you are more likely to find an easy to follow step by step procedure for installing the GIMP, which does not involve compiling or dependency hell issues but is simple and friendly the way that Ubuntu is supposed to be. 
Also bear in mind the latest version of the GIMP has only been out for a short space of time so although there might not be much documentation on how to get it working in Ubuntu, I'm sure that in a relatively short space of time we'll see quite alot of documentation and help appearing online. After all the GIMP is quite a major tool for many Linux-based-systems users :)

---

### Post by Cæncel on 2012-05-06
just wondering if someone besides me is trying to figure out how to disable the gimp banner over the toolbox, in 2.6 i was able to remove it, i would like to use that space for a new row of tools

---

### Post by 4museman on 2012-05-06
Hi everybody!

I tried two times install commands from "otto-kesselgulasch" and always got problems. As a result it always make Ubuntu Software Center crash upon start.

My console reading (in second attempt) was:

```
milos@Sam:~$ sudo add-apt-repository ppa:otto-kesselgulasch/gimp
[sudo] password for milos: 
You are about to add the following PPA to your system:
 CAUTION!

This PPA could break your installed OS. There are dependency issues especially for Oneiric (11.10). Only use it if you know what you do! I'm working with others on a stable and reliable solution.

Regards
 More info: https://launchpad.net/~otto-kesselgulasch/+archive/gimp
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.rZIG5EzXfT --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv FB97E9C3A97F85C095AEA7903BDAAC08614C4B38
gpg: requesting key 614C4B38 from hkp server keyserver.ubuntu.com
gpg: key 614C4B38: "Launchpad otto06217" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
milos@Sam:~$ sudo apt-get update && sudo apt-get install gimp
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/otto-kesselgulasch-gimp-precise.list
E: The list of sources could not be read.
milos@Sam:~$ 
```Am I the only one who got this problem or it's something outside my computer? Can anyone recognize the cause of the problem?

Thanks in advance!

PS: Ubuntu 12.04 (64-bit), GNOME 3.4.1

---

### Post by jcolyn on 2012-05-06
Just installed it on my Kubuntu 12.04 computer. Far better than the 2.6.12 version.

[[IMG]http://fc09.deviantart.net/fs71/i/2012/127/3/2/gimp_2_8_by_colynsfotografs-d4yvdiu.png[/IMG]]("http://fc09.deviantart.net/fs71/i/2012/127/3/2/gimp_2_8_by_colynsfotografs-d4yvdiu.png")

---

### Post by 4museman on 2012-05-06
I just solve the problem.
I had to delete by hand two "otto-kesselgulasch" files from "/etc/apt/sources.list.c/" and then apply the procedure suggested by [vVvSHADOWvVv]("http://ubuntuforums.org/member.php?u=1317420") in this thread: [http://ubuntuforums.org/showthread.php?t=1967043](http://ubuntuforums.org/showthread.php?t=1967043)

Cheers!

---

### Post by BcRich on 2012-05-06
@jcolyn oooooh that looks so shiny nice and new, I'm sooo envious :) can't wait to get mine installed. The cage transform tool is something I can't wait to try. I also read on the GIMP website that they are planning on redoing the iwarp tool and replacing it with something alot more advanced. I might be mistaken but I think I read something about on-canvas editing (now if I can only find the wiki-page I read it at)
@4museman that's awesome! glad to hear you got it working and thanks for sharing the link, I'll need that (and I'm sure alot of other people too) when upgrading to 12.04 and hoping to run GIMP 2.8 :)

---

### Post by jcolyn on 2012-05-06
> **BcRich said:**
> @jcolyn oooooh that looks so shiny nice and new, I'm sooo envious :) can't wait to get mine installed. The cage transform tool is something I can't wait to try. I also read on the GIMP website that they are planning on redoing the iwarp tool and replacing it with something alot more advanced. I might be mistaken but I think I read something about on-canvas editing (now if I can only find the wiki-page I read it at)

I do a lot of digital image work and this new version works wonders.

I would advise that you uninstall gimp and gimp data for a lot less trouble..

Or you could run ```
sudo apt-get purge Gimp*
``` in the terminal before installing the ppa.

Then ```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
```

```
sudo apt-get update
```

```
sudo apt-get install gimp
```

---

### Post by mmesantos1 on 2012-05-07
Thank you for the tip, this worked well for me. :)

---

### Post by BcRich on 2012-05-07
@ Cæncel did you find a solution? Sounds like something I'd like to know when I get GIMP installed :-)
@Jaclyn thanks 4 posting a very clear set of instructions for installing on 12.04 will definitely try them out when I install latest ubuntu :-)

---

### Post by Stewie2kill on 2012-05-08
Thank heavens for Single Window mode!

I could never use Gimp because everything was always all over the place. Guess I was never one to really 'put my brain to use' on how to configure it and get used to it.

It's definitely amazing and a solid release!

Thank you devs! Great job!

---

### Post by rojaasensei on 2012-05-09
> **jcolyn said:**
> I do a lot of digital image work and this new version works wonders.

I would advise that you uninstall gimp and gimp data for a lot less trouble..

Or you could run ```
sudo apt-get purge Gimp*
``` in the terminal before installing the ppa.

Then ```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
```

```
sudo apt-get update
```

```
sudo apt-get install gimp
```


Thank you for your advice.  I was able to install the new Gimp on Xubuntu 12.04 machines (64 & 32bit).  Works like a charm

---

### Post by eulu on 2012-05-09
> **jcolyn said:**
> I do a lot of digital image work and this new version works wonders.

I would advise that you uninstall gimp and gimp data for a lot less trouble..

Or you could run ```
sudo apt-get purge Gimp*
``` in the terminal before installing the ppa.

Then ```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
``````
sudo apt-get update
``````
sudo apt-get install gimp
```

I followed these steps and now have 2.8 installed (Pangolin 12.04 64-bit), but with one annoying issue: If I have 2.8 running it doesn't show up when I ALT+TAB, so the only way to get to it is to minimize the other windows. Any suggestions? Thanks 
Edit: Looks to be buggin others too.. [http://ubuntuforums.org/showthread.php?p=11922001#post11922001](http://ubuntuforums.org/showthread.php?p=11922001#post11922001)

---

### Post by Lugar on 2012-05-09
Followed the steps just now on 12.04 64bit with no issues regarding unity and alt-tab. 2.8 is well worth it.

---

### Post by ahso4271 on 2012-05-10
Hi
Should I wait for the plugin repo or install as above? How long would it take to wait for all of Gimp 2.8 in the software manager to appear? Do I need to install updates to Ubuntu 12.04 or alike?
Thanks

---

### Post by BcRich on 2012-05-10
> **ahso4271 said:**
> Hi
Should I wait for the plugin repo or install as above? How long would it take to wait for all of Gimp 2.8 in the software manager to appear? Do I need to install updates to Ubuntu 12.04 or alike?
Thanks
Hi ahso4271 
It's unlikely that GIMP 2.8 will appear in the official ubuntu 12.04 software repos before the next official release of ubuntu 12.10
If you are using 12.04, jcolyn's (above mentioned) instructions should work for you, but if you are using another version of ubuntu such as 11.10 or 10.10 (or older) it would be more advisable to update to 12.04 (if that is possible for you?) then follow the instructions. I mention this because I have read several posts where the otto-kesselgulasch PPA causes conflicts and unresolved dependencies on non-12.04 installations.
Also running the latest ubuntu 12.04 updates will not likely effect the above mentioned installation, however it doesn't hurt to have an up to date system especially when several of the updates are related to security fixes.
Hope that helps?
:)

---

### Post by Sableyes on 2012-05-10
Installed and running ^^

Ola I cant use single window mode! :oops:

---

### Post by ahso4271 on 2012-05-11
Just followed the above steps and had a look at the Software Center. Can I also install those addons from the Software Center or will that not work in 2.8?

---

### Post by BcRich on 2012-05-11
> **ahso4271 said:**
> Just followed the above steps and had a look at the Software Center. Can I also install those addons from the Software Center or will that not work in 2.8?

Hi asho4271
the addons in the software center will apply to GIMP 2.6, but here's a recent post on installing GIMP Paint Studio for 2.8 [http://ubuntuforums.org/showthread.php?t=1977883](http://ubuntuforums.org/showthread.php?t=1977883) if u r interested? 
if there are other addons that have been developed for 2.6 that you would like to use in 2.8 rather look at the developers website (if they have one) or do a google search for a version that is intended for 2.8

---

### Post by Paddy Landau on 2012-06-05
> **jcolyn said:**
> Or you could run ```
sudo apt-get purge Gimp*
```
Shouldn't that be a lower-case "g"?
```
sudo apt-get purge gimp*
```

---

### Post by jrela2000 on 2012-06-10
> **jcolyn said:**
> I do a lot of digital image work and this new version works wonders.

I would advise that you uninstall gimp and gimp data for a lot less trouble..

Or you could run ```
sudo apt-get purge Gimp*
``` in the terminal before installing the ppa.

Then ```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
```

```
sudo apt-get update
```

```
sudo apt-get install gimp
```

Let me thank you for this.  If I keep finding answers like this, I'll never ask them and therefore my post count will go up.

---

