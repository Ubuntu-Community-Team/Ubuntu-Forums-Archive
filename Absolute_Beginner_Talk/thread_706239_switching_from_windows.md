---
title: "switching from windows ?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by yarger897 on 2008-02-24
i have used window and thats the only operating system that i have ever used. so i have a few questions ? can i play world of warcraft with clicking an icon or is all the commands ran off / comands? also doest it read 64 bit processers and how many gig of ram will it  read . how well does wine work with windows applications? is this system easy to operate for noobs like myself ? plz give me some answer because micro soft is putting holes in my pocket :(

---

### Post by PmDematagoda on 2008-02-24
You can play World of Warcraft on Linux by using it through [Wine]("http://www.winehq.org/"), Wine can be installed using:-
```
sudo apt-get install wine
```
or by going to the Synaptic Package Manager in System>Administration>Synaptic Package Manager, searching for wine and installing it. The other Windows programs will also have to be run using Wine but if you could provide the list of Windows applications you wish to use then we could tell you if you can use it using Wine, if there are Linux versions of them or if there are good open source alternatives for it.

About 64-bit processing, yes, Ubuntu does support it, just download the AMD64 version of Ubuntu and install it. How much RAM do you have in the first place?

Ubuntu has gone a long way to make sure that beginners to Linux from Windows find the switch to be as easy as possible, so you should find it easy:).

---

### Post by szymon_g on 2008-02-24
can i play world of warcraft with clicking an icon or is all the commands ran off / comands? 
you can play WoW using wine. the fastest and easiest way is to invoke it from konsole

wine wow.exe (i'm not sure about name of this exe, sorry ;p).

of course you can put it as an icon on desktop

also doest it read 64 bit processers and how many gig of ram will it read
1. yes, it does
2. i'm not sure about situation in 64bits (i use 32bit)- in 32bit system ubuntu can read up to 3.2(3.5?) gram- on default kernel. of course you can install kernel that supports >4g ram

how well does wine work with windows applications?
hm... some programs work, some doesnt, some work partially... in overall: [www.winehq.org](www.winehq.org)

is this system easy to operate for noobs like myself ?
yes

 plz give me some answer because micro soft is putting holes in my pocket

hehe, thats what microsoft do ;p

---

### Post by Mad_Gouki on 2008-02-24
I switched to Ubuntu a few weeks ago from Vista, and I must say, after a week or so of confusion, you start to figure out how it all works, and it is really not much different from windows, you just use the command prompt a LOT ;)
gaming on linux does sometimes require a bit of messing to get it to work, if you have an NVIDIA card, you will probably have little to no problem, if your card is ATI, it will be a lot of trouble.

Some of the 64 bit stuff doesn't work as easily in Ubuntu as the x86 stuff does, so for a beginner, I would say get the x86 distro, and once you have a good handle on how it all works, upgrade to the 64 bit kernel, or do a fresh install of the 64 bit distro if you want that new os feeling.

I have 2 gigs of ram and it uses that, I would imagine it supports over 3 or 4 gigs of ram, just like windows would.

world of warcraft is VERY popular, so there will be tutorials on how to get it working if you run into any problems, and the forums are always here if you need help.  All in all, I am of the opinion that windows just isn't all that great, not after seeing ubuntu and how easy it is to get stuff working with just a few steps.

The major difference is that it will either work, it will require a restricted driver to be enabled, or it will take some configuration or installation of other things and maybe even some compiling to get some things to work, but all in all it is not too bad, and there are tutorials for EVERYTHING you could ever think of.

---

### Post by (((X))) on 2008-02-24
If I just copy all my WINDOWS from my windows computer into ubuntu/c:Windows(wine), 
would I be able to do more, because I coudn´t even get cdrom I need to use for school to work in wine, Is there a site I can download additional things for wine?

---

### Post by yarger897 on 2008-02-24
very helpful thanks very much . but one more question can i go ahead and down load ubuntu to my old computer and pick witch os that i want to boot up so i can learn linux before i try this on my newly built computer with no os yet .if so how or will it automatically ask me since i have window already installed ?

---

### Post by PmDematagoda on 2008-02-24
> **yarger897 said:**
> very helpful thanks very much . but one more question can i go ahead and down load ubuntu to my old computer and pick witch os that i want to boot up so i can learn linux before i try this on my newly built computer with no os yet .if so how or will it automatically ask me since i have window already installed ?

When you install Ubuntu it will automatically setup the dual-boot which would allow you to access both Windows and Ubuntu, you can choose which OS to boot at start-up.

Also, could you post the specifications of the old PC you are going to test Ubuntu on?

---

### Post by yarger897 on 2008-02-24
old computer has = 

                                  motherboard= asus with ati chipset 
                                  hard drive = 160g wd sata
                                  video card = his 256mb 128bit 
                                  memory =1g cosair xms ddr400
                                  cpu= 1.8g amd athlon 64 3000+

new computer =


                                motherboard = asus nvida chipset 
                                hard drive =320g wd sata
                               video card =evga 8800 320mb 320bit gddr3 gforce
                               memory =4g cosair xms2 ddr800
                               cpu = 3.2 amd athlon 64 duel core 6400 + am2

---

### Post by PmDematagoda on 2008-02-24
Ubuntu should work out-of-the-box with your old PC, but you may have to use the Alternate CD or different parameters for the Live CD on the new PC since the 8800 is not really well supported by the vesa driver which is used by the Live CD.

---

### Post by jocheem67 on 2008-02-24
As a rather advanced windows-user a cuople of years ago, it took me 'bout 2-3 months to figure out the architecture of linux/ubuntu....
It's certainly a matter of motivation: does one just want to click some icons and use the graphical part of the ubuntu OS, that's certainly possible..However when one runs into problems, a crashcourse linux troubleshooting is certainly needed....and that takes time and effort and idd an open mind...

If you wanna make the "big step" I would recommend to dual-boot for quite a while. First learn to navigate your new OS, read the docs, mess up once in a while, and just after that try to make ubuntu your production-OS...

It is quite a change, and though some linux-users can be productive while not knowing a lot about what's under the hood, I do think that that is a rather tricky way...

Now I just love to do the command-line, it's more rewarding to me....

---

