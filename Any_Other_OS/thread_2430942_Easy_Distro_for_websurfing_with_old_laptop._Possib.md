---
title: "Easy Distro for websurfing with old laptop. Possible?"
date: 2019-11-09
forum: Any Other OS
---

### Post by gipsyshadow on 2019-11-09
I've got an old acer tm notebook with 1.6 ghz centrino cpu and 1.25gb ram (I guess DDR1 270mhz but I can be wrong). I still use it sometimes just as an "emergency" machine, eg. as an addition backup space for my storage, if I want to write something with old office within win xp environment and to run other old sw, but I can't use it to surf the web because I cannot install any AV else win xp would freeze.

I've been using only this machine from its "creation" until about 1 year ago and I solved the websurfing problem using PaleMoon browser and some plugin like adblock to avoid loading the "heavy" content of today web pages. It was a situation full of limitations because I couldn't open more than 2-3 pages at the same time -and dangerous too due to no AV and the obsolete OS- but it was good enough for me.
Now I'd like to use sometimes this old acer to surf the web, so I'm thinking to get a linux OS to avoid AV and a web browser with right plugins able to load only the fundamental content of the web pages, I mean avoiding to load flash content and everything the would freeze the 1.25gb ram.

My level of knowledge of linux is "dummy" because I've only been using ubuntu 18.04 from 1 year so I'm used to work almost with GUI and not with the terminal. That is fundamental because I couldn't use distro as archlinux based more on terminal then GUI and for his reason i specified "easy" :)

---

### Post by uRock on 2019-11-09
If it is 32bit, then I'd recommend Debian Buster with the LXDE desktop. It only uses about 200MB of RAM at idle on my old Asus Netbook.

---

### Post by gipsyshadow on 2019-11-09
Hi uRock, nice avatar :)
Yes, it's an old 32bit. Thanks for your suggestion, I'd just wanna ask a comparison between ubuntu + lxde (lubuntu) and debian + lxde as you suggested, because 4-5 years ago I had been running lubuntu for a while on that machine and it had been quite good.

By the way, will I be able to surf the web with debian+lxde "basically" (in the sense I wrote above)?

---

### Post by crip720 on 2019-11-09
Have an old Toshiba with a P4 cpu and about the same ram.  Use Lubuntu 16.04 on it and it can keep up, if you don't overload it with tabs open, a few are okay.  Chrome does not have a 32 bit version anymore, but think all the rest still do, have to check that.  Would check if your model can accept more ram, if it can you can probably find some cheap.  ebay should have it.

---

### Post by uRock on 2019-11-09
> **gipsyshadow said:**
> Hi uRock, nice avatar :)
Yes, it's an old 32bit. Thanks for your suggestion, I'd just wanna ask a comparison between ubuntu + lxde (lubuntu) and debian + lxde as you suggested, because 4-5 years ago I had been running lubuntu for a while on that machine and it had been quite good.

By the way, will I be able to surf the web with debian+lxde "basically" (in the sense I wrote above)?

Firefox can be a bit slow on it, but it should be fine as long as you don't try Facebook or any other resource intensive sites.

Lubuntu and Debian's LXDE are very similar. I used the Debian non-free image so it'd have non-free driver support. I mostly use it as a [Motion server]("https://motion-project.github.io/index.html").

The foreseeable problem with Lubuntu is the dropping of 32bit support. Canonical decided it's time to move on and invest developer time elsewhere.

16.04 only offers support for Ubuntu. The other DEs only get 3 years of support on LTSes.

---

### Post by gipsyshadow on 2019-11-09
Upgrading acer's ram from 1.25gb to 2gb is possible but 1) I'd like to avoid spending money on this old laptop though it'd cost about 10-15$ and 2) I'd dismantle it and that would take about 2h, so I could consider this upgrading if and only if that got this situation very much better, I mean the goal of this thread.

Let me understand "the dropping of 32bit support" better. If now I get lubuntu 18.04 (or 16.04) will it support 32b cpu only for few time more? If now I get debian lxde will it keep supporting 32b for long time? Is this the difference?
By the way, where can I read the system requirements of debian lxde? I've only found lubuntu's ones on wikipedia: Pentium M cpu (ok, mine is "banias"), RAM 1 GB (ok, mine is 1.25gb), 15 GB space (mhhhh... I guess 10gb can handle a "basic" lubuntu installation), video 1024×768 (ok).

A friend of mime has talked me about "puppy" linux. How can it be compared to lxde DEs about ram usage and usability (for a dummy linux user as me)?

---

### Post by uRock on 2019-11-09
[18.04 is the last 32bit Lubuntu release, which has support until 2021.]("http://cdimage.ubuntu.com/lubuntu/releases/18.04.3/release/") The packages that are shared with ubuntu, such as kernels, will get support until 2023. I went with Debian because I don't ever want to upgrade it again, but if I do, then it will be supported. The release will likely outlive the netbook.

I haven't tried Puppy for several years, so I can't say much about it.

---

### Post by crip720 on 2019-11-09
Puppy and other tiny linuxs are made to run on systems with even less specs than yours, think they can work with around 150 Mbs of ram.  Be a bit different OS than what ubuntu/lubuntu shows you.  Googling for small linux should give you their sites.  Remember that minimum specs is what an OS will work on, not that they will work well on.

---

### Post by jetsam on 2019-11-09
Absolutely give a live Puppy Linux a try.  I haven't run it in several years, but it was so easy to get running, it was a great test distro just to check the Linux compatibility of hardware like yours.  It can "install" itself by saving a big file to any hard drive partition you want; any file system, too.  That makes a few gigs of persistent storage, which is all the Puppy needs to sing.  It's easier to install Puppy than to not install Puppy.

Edited to add: Puppy uses a different memory paradigm than most distros... it's more efficient with ram than almost all of them.  I can't recall the details, but the net effect is that all your applications reside permanently in fast access ram, so starting programs is nearly instantaneous.  Puppy came out before SSDs were common, and it was a revelation that every single application on a computer could essentially have an instant start time.  It seemed really revolutionary when it first appeared.

---

### Post by gipsyshadow on 2019-11-10
> **crip720 said:**
> 
Googling for small linux should give you their sites

I know but I hope to get your direct experience with linux distros here :) Anyway I've been googling for a while and got other 2 interesting distros: antix and mx linux.
If I'm not wrong these 3 distros are systemd-free (opposite to ubuntu) and I'd like to know if this can help or not about ram usage for my personal case, considered that my goal is to get a distro with min ram usage because I'd like to surf the web. If I'm not wrong that's the ascending order of these 3 distros by ram usage: puppy, antix, mx, isn't that?
What about the 32b support of antix and mx?
If I'm not wrong both puppy and mx are good for noobs (as me), what about antix?

---

### Post by jetsam on 2019-11-10
Just try one and see!

We can't answer your questions because the answers are mostly up to you and what works for you and your system.

I'd suggest Puppy again, but you could also just try one I've never tried and tell me what it's like ;)

---

### Post by mörgæs on 2019-11-10
> **gipsyshadow said:**
> ...a web browser with right plugins able to load only the fundamental content of the web pages, I mean avoiding to load flash content...

You should try the browser **links2**. It is text-only and takes a while to get used to but it's worth the effort. 

The OS itself puts only a light workload onto the computer. The problem is finding light applications. 

I hope you have changed all passwords which have been entered while running XP. It's an easy target for attackers.

---

### Post by gipsyshadow on 2019-11-10
> **mörgæs said:**
> The OS itself puts only a light workload onto the computer.
Yes, we're dealing with the idle OS ram, so I'm looking for a light (and easy) distro for 1st, then I'll search a light web browser, anyway thanks for your suggestion :)

I think I'll try puppy xenial for 1st, just because there's a version in my language too while puppy bionic, antix and mx are only in EN :)

---

### Post by gipsyshadow on 2019-11-12
I'm back but with bad news.
I've just tried puppy xenial live and I've opened the terminal to give some commands as "inxi -Cx" but I've got "command not found". I've tried with "sudo" but got the same output, I've tried "lshw" and the same bad output. After that I've tried "lsusb" and "uname -a" and I've got proper output with the required infos. So what's wrong?
Other important matter for me: touchpad doesn't work. I 've gone to setup-> touch -> flSynclient and got "couldn't find synaptics properties. no synaptics driver loaded".
Other (maybe more important) matter is that I'm not able to connect to internet. I use only an internet key for that and I set the right provider from FF loading 192.168.1.1 page. I've tried to load that page from palemoon (which is the default puppy browser) but I couldn't access it, I think there have been some hw troubles related to this huawei key.

Now I wonder what's the best way to go for me: 1) working on puppy with your help to solve those troubles, 2) trying knoppix or the other mentioned distros. As said I need a "small" in size distro (max 8gb), I mean after hdd installation and with a "proper" web browser on it, with low ram usage and easy to use, as puppy seemed to me. What can you suggest me?

By the way, is still this the right thread to discuss about installation problems or I've to move to [mörgæs' signature thread]("https://ubuntuforums.org/showthread.php?t=2130640")?

---

### Post by jetsam on 2019-11-12
My guess is neither inxi nor lshw are installed in the default Puppy install.  I can get back to you with more details later (I installed Puppy Xenial last night myself), but you basically just need to install the software you want to use.

There's always some transition pains using a new distro; it's unavoidable that there will be some learning curve.  Some general advice: be a bit flexible.  Sometimes a distro will have a better preferred solution than what you're used to.  I believe Puppy comes default with Abiword, for example, and it's the best Word-clone word processor in existence.  I use it on every OS now including Windows, but I discovered it because Puppy introduced me to it.

If you stick with Puppy, you may want to explore the Puppy forum.  There will be advanced knowledge about Puppy represented there that nobody here has.

---

### Post by mörgæs on 2019-11-12
You are welcome to open your own thread like this one and you are welcome in mine. Your decision.

I suggest that you install using a wired internet connection regardless of the distro you try.

---

### Post by gipsyshadow on 2019-11-12
> **mörgæs said:**
> you are welcome in mine
Thanks mörgæs but let me understand this: your thread starts with [solved] so I guess I can't ask my linux distro request within yours nor ask help to make my huawei key to work on puppy, can I?

Anyway I'm oriented to just try knoppix and see if my internet key works "out of the box", my only doubt is about the minimum disk space knoppix lxde requires because I couldn't find it anywhere and my downloaded iso is more than 4GB (vs 300MB puppy .iso), do you know it?

---

### Post by mörgæs on 2019-11-13
I marked the thread solved because the main contents is the five initial posts. They are now followed by 22 pages of old hardware related discussion and everybody is invited both for asking and answering BUT since you already have your own thread here I suggest that you stay faithful to it.

If there is 15 GB of hard disk space you have plenty of space for all the distros mentioned. 

One thing at a time. First the install using a wired connection and then the Huawei dongle.

---

### Post by gipsyshadow on 2019-11-13
All right, I go on here with my struggles :)
Let me point to and summarize what I'm looking for. I'd like to get this old acer into an "emergency" device so it's fundamental my usb huawei key and touchpad work "out of the box", I mean suddenly with "the" distro running in live session. Acer's an ethernet port too but I've only got this huawei key to connect to internet so neither wireless nor ethernet solution for me.
15GB is about twice what I can afford. If (and only if) I'll have success with a distro so "big" in live session than I'll re-arrange my hdd to get extra space.
I think I'll give another chance to puppy trying bionic version, we can never tell. If I won't get success I'll move to the "bigger" distros mentioned here, both in size and in ram usage.

---

### Post by westie457 on 2019-11-13
Take a look at Peppermint os. [https://peppermintos.com/](https://peppermintos.com/)

I ran this on an Acer Iconia tablet, no keyboard only a touch screen. Everything worked out of the box.
Can you tell us which wireless chip is in your box please.

---

### Post by gipsyshadow on 2019-11-14
I've a sort of idea though I'm very noob. As said it's fundamental for me to get a ready-to-use internet connection during the live session of the distro I'm searching. Afaik some distros carry a "persistent" live session, in other words I can modify everything during the live session and save it on the usb flashdrive as it was a portable "full" OS. My idea is to work on puppy live session to make my usb huawei dongle to connect the web, save this "job" to the pendrive and then get the modified puppy into a new .iso file. In this way I guess I'll get a puppy iso with internet connection working out of the box and I could put it into my flashdrive for emergencies. Is it possible? Do you think it's the best way to get my goal?

---

### Post by jetsam on 2019-11-14
I like your plan, and think you should proceed at your own pace, and keep us posted...

We might be able to help if you hit a roadblock on the way, but I suspect things will go pretty well, barring unknowable difficulties getting the wireless USB device working.

---

### Post by gipsyshadow on 2019-11-14
Here we are, my first roadblock and of course it's about my usb huawei dongle because it doesn't appear in "lsusb" list. If the idea is good let me know if it's the case to go on posting here these troubles about puppy or it's better for me to ask to another outside specific puppy linux forum, I remember from my lubuntu adventure how it can be hard to make a linux OS to recognize an internet key. By the way, I've got only this usb dongle to connect to the internet so no wireless or ethernet devices, else it'd be easier :)
Anyway I copied some reports got from puppy bionic live session, I mean the infos from "pup-sysinfo", if they can be useful to solve my main/only problem:
- System [https://paste.ubuntu.com/p/QpyWMH95sp/](https://paste.ubuntu.com/p/QpyWMH95sp/)
- HW [https://paste.ubuntu.com/p/HSMH8G7qMj/](https://paste.ubuntu.com/p/HSMH8G7qMj/)
They do not expire if I'm not wrong.

---

### Post by jetsam on 2019-11-14
It can't hurt to start a thread on the Puppy forums.  

I'm no good with help on your problem.  Hopefully someone else on this forum is and will be along to help out shortly.

---

### Post by gipsyshadow on 2019-11-17
Good news. I've tried with puppy again but this time I connected my huawei usb internet dongle before running puppy live session and it was recognized as
```
Bus 001 Device 005: ID 12d1:14db Huawei Technologies Co., Ltd. E353/E3131
```
so I think now I've only to set my ISP, as I do on ubuntu. The difference is that I configure my dongle on 192.168.1.1 firefox page on ubuntu (hilink huawei sw) while I've to set my ISP in a different way on puppy because I can't from palemoon. 
Do you know how to set that? I've opened "internet connectionwizard" window, is this the way to go? If yes, where and how to proceed to set a usb dongle internet connection? See attachment

---

### Post by jetsam on 2019-11-17
Does this walk through work for you?
[How to Wi-Fi Connect to the Internet With Puppy Linux]("https://itstillworks.com/wifi-connect-internet-puppy-linux-20789.html")

What happens if it doesn't work?

---

### Post by gipsyshadow on 2019-11-17
As said in my post #19 I've got only this usb dongle to connect to internet else everything'd be easier especially with a wifi device :)
> **jetsam said:**
> 
What happens if it doesn't work?
Getting an internet connection on my acer is the goal of this thread, if I didn't misunderstand what you meant.

---

### Post by jetsam on 2019-11-17
Right...   I'm playing catch up on some of this stuff, which is why I keep begging off ;)

Brief Googling reveals you now need to muck about with drivers for the thing.  It's an area I've never spent any time on.

You might look into getting an easier to configure USB device, at least as an option.  They aren't that expensive, and saving time is worth something in situations like these.  There's a sticky at the top of the networking forum with buying advice for usb wifi dongles if you're interested.

There's options for using wrappers for windows drivers and stuff like that.  Most things can be made to work with enough effort.  You just gotta translate the one set of numbers that come from thing 'a' into the other set of numbers to connect to thing 'b.'  That's really all a driver does.

---

