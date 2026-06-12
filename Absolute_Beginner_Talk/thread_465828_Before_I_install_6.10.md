---
title: "Before I install 6.10"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by jamesbrooks101 on 2007-06-06
Hey,

I am new to linux and I just wanted to know a couple of things before I start having problems. I have been using Windows for over 10 years, but now is the time I change (Thanks Vista ;) )

I have a home-made computer using the following:

Netgear WG311v3 Wireless Card
Intel Pentium 4 Motherboard
Nvidia Graphics card

All works fine on XP, no errors with any hardware :) But after reading for some time, and my friend having the same hardware, we came to the conclusion:

Netgear requires a ndiswrapper (And with no internet access untill the card is installed, we cannot do anything) & Nvidia doesnt work well with Beryl/XGL.

We could download the Ndiswrapper files on XP, save them to a memory stick and compile them whilst on Linux. But we do not know how to do that either :(

Thankyou for the time to read this topic, we are both newbies to linux and we would love to use it.

Thanks again for any help that we recieve.

James and Rob

**Edit: Changed title to new version.**

---

### Post by viciouslime on 2007-06-06
I'm not sure about downloading the debs beforehand, it is possible but I can't remember how...

However, a nvidia card is one of the very best for using Beryl. You do NOT, however, want to use XGL. XGL is the "old-fashioned" way of getting beryl/compiz to work. The much better, and now completely integrated way, is AIGLX. Basically if you want to use compiz all you'll have to do is go to the desktop effects menu and press enable...simple. If you want to use beryl, you'll just have to install it using synaptic (a simple two click process) and then run it...also simple. :)

---

### Post by steve.horsley on 2007-06-06
You are right about the netgear, I believe. The package may be on the CD - I'm not sure. Maybe someone else can shed light here?

As for XGL and Beryl, if you install 7.04 (known as Feisty Fawn), the repositories contain nVidia drivers (package nvidia-glx-new) that work with Beryl. I know this because I use them.

---

### Post by buuntuu! on 2007-06-06
about ndiswrapper:
you could download the packages from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/")
just use the search function.
be cautious though to get all the dependencies, you have to take care of it manually that way.
i installed network-manager like this (had problems accessing the wireless network at my university) and it worked out find.
have fun

---

### Post by jamesbrooks101 on 2007-06-06
OK, thankyou. So now I know the following:

Nvidia is great for Beryl

I have 6.06 and 6.10 so I will need to download 7.04 now.

Does anyone know if I can get ther correct drivers to work? I have the CD containing them, which came with my hardware.

Thanks again,
James

---

### Post by viciouslime on 2007-06-06
Ah ha! Got it :) I thought it was possible to download from [http://packages.ubuntu.com]("http://packages.ubuntu.com") but having found the ndiswrapper package I couldn't find the link to actually download it (doh!) It is there though. under the heading "Download ndiswrapper-common" :oops:

You'll need to make sure you download all the dependencies too. Though there don't seem to be any for the ndiswrapper-common package, ndiswrapper-utils-1.9, which I *think* you also need, does have some... and each of those has dependencies and so on. However, I think you can ignore the perl dependency as I *think* this is already installed by default.

---

### Post by viciouslime on 2007-06-06
Beaten to it. Thinking about one of the posts above now though, I think ndiswrapper DOES come on the CD it just isn't installed by default. So, when you go to install it just make sure you have the CD in the drive. if you want to test whether the drivers you have work or not. You can install it while using the liveCD and try it. You'd need to copy the drivers to a pen drive or something though, as you won't be able to use your cd drive.

---

### Post by jamesbrooks101 on 2007-06-06
Right, so if I was to copy all the drivers from the Netgear CD to my pendrive then run the LiveCD I should be able to get it working.

But how do I test they work etc? I'm sure it has something to do with the terminal, but thats it.

---

### Post by jamesbrooks101 on 2007-06-06
I am currently downloading Feisty Fawn 7.04

Could I not install 6.10 then:

sudo apt-get upgrade or something along the lines?

---

### Post by jamesbrooks101 on 2007-06-06
I just read somewhere that Beryl will not work well with Feisty. Is this true? At the moment, I am only concerned about the internet and my wireless card.

Thankyou.

---

### Post by steve.horsley on 2007-06-06
Since you are downloading 7.04, I advise against installing and upgrading 6.10. A clean instlall has a better chance of working - less chance for errors creeping in.

Beryl seems to work rather nicely with Feisty. I installed the nvidia-glx-new and loads of beryl stuff from the repositories, and everytihing liiks sweet to me. As a newbie, don't be tempted to download drivers/beryl etc from sources other than the Ubuntu repositories or you may end up with all kinds of compatibility issues.

---

### Post by Zzl1xndd on 2007-06-06
I am using Beryl on one of my 7.04 machines and Compiz on another of and beryl on my laptop too all work really well.

---

### Post by Nekiruhs on 2007-06-06
> **jamesbrooks101 said:**
> I just read somewhere that Beryl will not work well with Feisty. Is this true? At the moment, I am only concerned about the internet and my wireless card.

Thankyou.
Beryl works very well with Feisty, better than in 6.10 because of the new drivers. Having an Nvidia card makes installing Beryl absolutely painless.

---

### Post by jverkamp on 2007-06-06
If you install using 6.10 and then upgrade you will have to download new, upgraded versions of most of the software anyways, so you will still be using most of the bandwidth and time required for a clean install of 7.04.  Also, you run the risk of something breaking when doing the upgrade, so you would probably be safer installing from the 7.04 CD.

As far as the network: with two of the computers I installed it on, the 7.04 CD automatically configured the network, but on my school laptop I can't even boot because of the network card (so far).  Once you have the 7.04 CD, you could try booting it as a LiveCD, if the network is recognized it will show as such in the panel.

In any case, good luck and welcome to Ubuntu. :-D

---

### Post by jamesbrooks101 on 2007-06-06
Thanks everyone. I just got back from school. And I will now try it.

---

### Post by jamesbrooks101 on 2007-06-06
Noo!!!!

I started up, and it loaded. And I get a boot i/o error. I go back to XP, and find it was missing 30mb of data. I have to now download it all again. And my internet keeps crashing :(

Any suggestions?

---

### Post by steve.horsley on 2007-06-06
If you're having real trouble downloading, let me know and I'll drop a CD in the post for you. You can email me on [email]steve.horsley@gmail.com[/email].

---

### Post by jamesbrooks101 on 2007-06-07
Thanks.

I'm telling you, this place is alot nicer than when I have windows problems.

I will e-mail you now.

---

### Post by jamesbrooks101 on 2007-06-07
I have another question.

I like to send music and videos back and forth between my computer and phone, via bluetooth and I am just wandering, will my bluetooth dongle work with 7.04? 

Its is made by mikomi and it didnt come with any drivers.

---

### Post by jamesbrooks101 on 2007-06-07
All right, I have installed 7.04 on my computer, Windows has gone :P, end of.

Now, I have my wiresless drivers on a CD, what do I do with them? My internet doesnt work :( I have to be on my Dads computer.

---

### Post by Mazza558 on 2007-06-07
> **jamesbrooks101 said:**
> All right, I have installed 7.04 on my computer, Windows has gone :P, end of.

Now, I have my wiresless drivers on a CD, what do I do with them? My internet doesnt work :( I have to be on my Dads computer.

Install the file that I've attached (put it on the memory stick and plug it into your Ubuntu PC). Restart and you're set.

---

### Post by jamesbrooks101 on 2007-06-07
I installed it, but nothing happens :(

I read what it said when it had installed: sudo ndiswrapper -l but that doesn't work either.

Anything else I can do? I really need the internet.

---

### Post by jamesbrooks101 on 2007-06-07
Anyone? The internet is really important to me at the moment, because I am doing my GCSE's. I can always go back to WinXP but that is in a real emergancy.

I could use Wine, but I do not know how to compile it. I downloaded off of the website, and read the README but when I try and compile nothing works.

---

### Post by Fidelio on 2007-06-07
Have you set up your wireless connection? System>admin>newtorking.
You'll need to enable your wireless card and set all the options there, including the password for connecting to your router.

---

### Post by jamesbrooks101 on 2007-06-08
I installed the .deb package, restarted went to networking and all I had was:

Wired Connection
Modem

No wireless? My wireless card is Netgear wg311

---

### Post by jamesbrooks101 on 2007-06-09
Anyone? I cannot get the internet working. So unfortunatley I have had to go back to Windows :(

---

