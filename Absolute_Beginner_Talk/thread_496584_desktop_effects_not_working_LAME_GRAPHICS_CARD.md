---
title: "desktop effects not working LAME GRAPHICS CARD"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Church.Cameron on 2007-07-09
Ok so i have a ATI RADEON Xpress 200 and its not working, i will go on ahead to try to use the desktop effects and POOF everything goes white. with little icons spinning around i tried to Prnt Screen it but it didn't show up. so now have i have looked around at other post with no help, so i am posting my own agian. i really don't know what to do still kinda new but catching on very quickly.

give me some help

---

### Post by Cypher on 2007-07-09
What are the specs of your machine especially the graphics card?

---

### Post by Church.Cameron on 2007-07-09
i have a HP Pavilion zv6233 nr with a AMD Athalon 64 3400+ (2.2 Ghz) 1024 RAM, ATI RADEON Xpress 200 256 MB, umm anything else you want to know? the machine is about a year old

---

### Post by Cypher on 2007-07-09
Hmmm..OK, that looks like it's enough, how about this. Open a terminal and see what you get for
```

glxinfo | grep direct

```

---

### Post by evny on 2007-07-09
I also have an HP laptop with the same graphics card and I get the same thing when I try to use desktop effects.  I searched around these forums a bit and I don't think desktop effects can work with this card.

---

### Post by Church.Cameron on 2007-07-09
Well how can that be that lame it should saying tha tits part of the ATi fam i mean it just needs a driver languge right?

---

### Post by Church.Cameron on 2007-07-09
[http://albertomilone.com/nvidia_scripts1.htm](http://albertomilone.com/nvidia_scripts1.htm) you might wanna go here post above me rumor has it that its good and can fix the graphical issue or might fix it.

---

### Post by Lunatrix on 2007-07-09
i have a ATI Radeon 9550 and my screen just goes white. and my internet isnt working!

---

### Post by Church.Cameron on 2007-07-09
Same here with the internet i am not sure whats going on but i think if we can look around and fill each other in on what we find we might be able to fix this [http://albertomilone.com/nvidia_scripts1.htm](http://albertomilone.com/nvidia_scripts1.htm) seems to be solid i am told so check it out,

keep searching will make this work.

the internet issue might be bigger than i know of though whats exactly wrong with the internet?

---

### Post by evny on 2007-07-09
I'm on my way out, so I can't look it up right now.  Someone who knows better will probably come along and comment.  But I think it's something like this: even though we have the restricted driver for the card, it doesn't work with "compositing" (I think).  The driver has to be disabled and compositing has to be enabled, but since it doesn't work with this particular card, we don't get desktop effects, we get a white screen.  I recall seeing a list of video cards and unfortunately, the ATI Xpress 200 was listed as "not supported."

But of course, if there's a way to get it working, that would be great.

---

### Post by Church.Cameron on 2007-07-09
Well then if they want to keep me as a supporter i would like them to support the RADEON Xpress cus that card is very popular in laptops, i gonna check into it more i look and see what might be up.

---

### Post by evny on 2007-07-09
I just quickly logged in again to say it's not Linux or Ubuntu's fault.  It's ATI's fault for not using open source drivers.

---

### Post by Church.Cameron on 2007-07-09
Hmm well then they has to be way to take the Languge files and make them communicate with Ubuntus demands, there needs to be away for the ( i believe its the INF files ) to coexsist with Ubuntu's desktop effects.

---

### Post by randytuggle on 2007-07-09
I have an Acer with a Radeon Express 1100 and mine takes a crap if I install restricted drivers and attempt to use desktop effects. You may want to install the driver for your card directly from the ATI website and THEN try desktop effects.

---

### Post by Church.Cameron on 2007-07-09
That would be the sound solution, buut ati dosen't control this graphics card HP does they are in full support for this graphics card, i have the drivers for it on a hp drivers disk, but i am not sure if that gets me any closer to achiving my goals. but yea that was a good idea but you goto ATi they send you to HP or who ever controls the graphics card.

Thank you for helping though

---

### Post by Church.Cameron on 2007-07-09
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) i don't think this post relates to many of the laptop Graphics cards by ATi,

---

### Post by into_311 on 2007-07-09
> **Cypher said:**
> Hmmm..OK, that looks like it's enough, how about this. Open a terminal and see what you get for
```

glxinfo | grep direct

```

I liked Cypher's comment. What does that output of that command tell you. If you go to a shell/command prompt and type that in? If direct direct rendering isn't enabled. Then the 3d Desktop Effects won't work.

DId you install the ATI driver via the restricted drivers manager?

What does it say in the "Device Section" of your /etc/X11/xorg.conf file? It should read "fglrx". If it has ati or radeon that it is still using the open source driver for some reason (which will not work with 3d desktop effects on your graphics card).

---

### Post by Church.Cameron on 2007-07-09
> **into_311 said:**
> I liked Cypher's comment. What does that output of that command tell you. If you go to a shell/command prompt and type that in? If direct direct rendering isn't enabled. Then the 3d Desktop Effects won't work.

DId you install the ATI driver via the restricted drivers manager?

What does it say in the "Device Section" of your /etc/X11/xorg.conf file? It should read "fglrx". If it has ati or radeon that it is still using the open source driver for some reason (which will not work with 3d desktop effects on your graphics card).

I am not sure how to install a driver in the resrticted drivers area i will play with it tonight.

i am at work so its not around me but tonight i will check it out.

---

### Post by swoll1980 on 2007-07-09
> **Church.Cameron said:**
> i have a HP Pavilion zv6233 nr with a AMD Athalon 64 3400+ (2.2 Ghz) 1024 RAM, ATI RADEON Xpress 200 256 MB, umm anything else you want to know? the machine is about a year old

My brother has same cpu as you same thing happens to him  :(

---

### Post by Church.Cameron on 2007-07-09
> **swoll1980 said:**
> My brother has same cpu as you same thing happens to him  :(

Yea i have been told there is a fix but i haven't seen much i haven't had a change to fool around with it and see what i can accomplish, i  have a few things i am gonna try. but yea its a great computer just not very compatable with Ubuntu :( LAME

---

### Post by Church.Cameron on 2007-07-09
ok i would like to know if anybody know is that envy system works on most all ati graphics cards, i look in other places on the web and the forums are 50/50 on Envy but i can't rely soley on that opinion cuz they were not very discriptive on the basis of why they didn't like it.

So Envy does it work, is it worth it, and will or might solve my graphical issue.


WHY DO THE UBUNTU GODS MOCK ME IN WAYS I CANNOT UNDERSTAND WHYYYYY!!!!!!!!!!!!!!!!!

a glass of water is what i need

thnx

---

### Post by Church.Cameron on 2007-07-09
[http://ubuntuforums.org/showthread.php?t=427464&highlight=ATi](http://ubuntuforums.org/showthread.php?t=427464&highlight=ATi)


P / HP-Compaq Laptops available = 6 | Current Rating = **


-[HP] [dv1000] [1.6GHz] [512Mb] [80Gb] (REQUIRES NDISWRAPPER FOR WIFI)

-[HP-Compaq] [nx9020]

-[HP] [nx6110]

-[HP] [NX7000]

[COLOR="Red"]-[HP] [Pavilion zv6000] [ATI Radeon Xpress 200m] [Broadcom wireless] [Sempron 3200+] [512MB RAM] [40gb HD] (Perhaps needs Ndiswrapper for WiFi)[/COLOR]

-[HP] [Compaq Evo n610c]


so its a compatable, system  dv6000 series can work with ubuntu, so threre is hope, i have check other places and this isn't a new problem for hp laptops that are 1 or more old, the drivers installed in the newer hp systems are alot better and have been transfered to ubuntu without a hitch. so there is hope, its possible to get this thing up and going. and if you can get past the installation on a dv6000 series so far from all i have been reading theres hope for the dv6000 laptops.

---

### Post by snwbord2456 on 2007-07-09
I know this isnt'that helpful, here at least is a guide for installing beryl which you need to do in order to get the cool desktop effects like the cube and the wiggle and all that stuff (at least I think? from what ive read, though I could easily be wrong, I´m new also) 

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

but I always get stuck on 

> sudo modprobe -r fglrx

But when i enter the glex command, my rendering is enabled, but I cant remove the fglrx module because I get:

FATAL: Module fglrx module in use. Do I need to start in a different graphics (I dont know the correct term) and if so, how?

P.S. I have a different system as well, but on that Ubuntu supported thread my computer (Dell Inspiron e1505) was compatible. My graphics card is a Radion Mobility X1400, which on the guide I gave, I couldnt find the X1400.

---

### Post by Church.Cameron on 2007-07-09
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)


so this in lamest terms is telling me....i am owned, and i am not ging to be able to perform the desktop effects.... LAME

2D Acceleration Only
Xpress 200M Northbridge integrated GPUs 

man this isn't a good day for me and ubuntu

so should i give up hope for my graphics card to preform what i wish for it to do?

---

### Post by snwbord2456 on 2007-07-10
Your guess is as good as mine, im debating buying another vide card though cause I really want those effect, but im wondering if its worth.

---

### Post by snwbord2456 on 2007-07-10
[QUOTE=snwbord2456;2994428]Your guess is as good as mine, I really want those effects.

---

### Post by bren on 2007-07-10
> 
Ok so i have a ATI RADEON Xpress 200 and its not working, i will go on ahead to try to use the desktop effects and POOF everything goes white. with little icons spinning around i tried to Prnt Screen it but it didn't show up. so now have i have looked around at other post with no help, so i am posting my own agian. i really don't know what to do still kinda new but catching on very quickly.

give me some help

i have the same graphics card and you are right that desktop effects does not work.

however, do not fear

follow this link and you will have faster graphics and the old version of beryl (fancy windows effects)

works for me

make sure to read to the bottom about inhibiting beryl updates (later version will break it for you again)

bren

[http://ubuntuforums.org/showthread.php?t=399643&page=6&highlight=x200m](http://ubuntuforums.org/showthread.php?t=399643&page=6&highlight=x200m)

---

### Post by Vague on 2007-07-10
> **Church.Cameron said:**
> [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)


so this in lamest terms is telling me....i am owned, and i am not ging to be able to perform the desktop effects.... LAME

2D Acceleration Only
Xpress 200M Northbridge integrated GPUs 

man this isn't a good day for me and ubuntu

so should i give up hope for my graphics card to preform what i wish for it to do?

That guide is for the open source radeon driver, which does not offer 3D support for your card.  You need to be using the proprietary fglrx driver.  If you don't have that running, check this guide for more information: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-796aa4d6d0477c8ed722acef1878cc5626855ae3)

The guide you linked says that using the fglrx driver with XGL for Beryl isn't stable, and that might be true, but that's exactly what I'm doing for Compiz Fusion on this machine, and it's working fine for me (granted, it's a totally different card, so your mileage may vary, but the radeon driver is definitely not going to work for you).

edit: didn't see yours before I posted this, bren.

---

### Post by snwbord2456 on 2007-07-11
Bren and Vague, when using the guide you provided it says to download the drivers installer. I have an X1400 graphics card (ATI Radeon) yet when I goto Driver & Software ->Radeom -> it jumps from the X1300 series to the X1600 series, which one should I use?

---

### Post by Vague on 2007-07-11
> **snwbord2456 said:**
> Bren and Vague, when using the guide you provided it says to download the drivers installer. I have an X1400 graphics card (ATI Radeon) yet when I goto Driver & Software ->Radeom -> it jumps from the X1300 series to the X1600 series, which one should I use?

Well, to answer your question one way, they probably don't bother listing your card because the X1300-X1550 cards are all based on the same core.  To answer it another way, you should be fine installing it from the repositories, rather than directly from ATI's web site.  I actually linked to the anchor in the guide for installing using the Restricted Drivers Manager in Feisty, which should work for you.

edit:  Sorry, it's been a while since I read this thread, and I had to re-read it.  Probably should have done that before posting.  Anyway.

It appears from what you've said that you're already running the fglrx driver, right?  If so, then you don't need to use the guide I linked to, as you already have it installed.  Likewise, using the radeon driver, as suggested in the guide you linked to, won't work, because RV515-based cards aren't supported by that driver.

You should probably check out this How-To: [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

It's a guide for using Beryl or Compiz Fusion with the fglrx driver.  Basically, just follow the instructions up until it says Beryl, and then follow the instructions for either Beryl or Compiz Fusion.

---

