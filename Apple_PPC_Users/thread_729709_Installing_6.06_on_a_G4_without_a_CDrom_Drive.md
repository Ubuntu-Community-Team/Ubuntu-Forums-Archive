---
title: "Installing 6.06 on a G4 without a CDrom Drive"
date: 2008-03-20
forum: Apple PPC Users
---

### Post by Kasa on 2008-03-20
Hello
I have used Ubuntu before, tho I h8 mac xD.

Basic problem, I have a Live CD of 6.06 and I am wishing to install (totally) on my G4 mac powrbook which has no CD ROM drive (broken)
I have tried with a External USB dvd writer, which will read but not boot the CD ( holding down c to boot)

anyideas would be help full

---

### Post by stream303 on 2008-03-20
As far as I know, you cannot boot from a usb cdrom, but I could be wrong.  Anyone?

If you can get your hands on a firewire cd/dvd this might help:

[http://ubuntuforums.org/showthread.php?t=698290](http://ubuntuforums.org/showthread.php?t=698290)

---

### Post by Kasa on 2008-03-20
I am wondering, I have a PC that dual boots with Gusty and I read a thread about puting this mac into target mode and using it as a harddrive.
problem is my computer wont read the PPC cd, I am thinking if I use a Normal CD on the PC when this mac is acting as a "HD" would that effect it in anyway ?
Because I am thinking the only difference is the Yaboot, and Grub.

BEcause I am hopeing to fulling wipe mac from this and have it as a Ubuntu laptop. (seeing dual booting isnt that much fun)



So, if I install a NORMAL 7.10 (no ppc anything) by using the target mode and connecting it to my Ubuntu on my PC, would it work ?

I will also try now with my firewire, I have a firewire cable here for this DVD wirter, I will try firstly with holding down c then holding down the other one and inserting the code if i can.

---

### Post by Kasa on 2008-03-20
I did both the "hold c" and "command+option+o+f" it just booted like normal.
I am really starting to hate mac.

Can anyone think of a way to get this to work ?

---

### Post by Kasa on 2008-03-20
ok,
I read somewhere els that holding Option on start up brings it into a boot menu.
Which for the first time was right.
I then worked out that the USB connection wont work, but the Firewire does.
it showed the the DVD with Ubuntu wass there.
WHOEVER
when i click on it the then hit the enter, or any button to say yes that is the selection's i want.
the screen flashes, then comes back that screen only in inverted colors.
anyone have any idea why the DVD FAILS TO LOAD???

---

### Post by Kasa on 2008-03-21
Can anyone help me PLZ!!!!!!!!!!!!
I have been thinking about it for HOURS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
and I am wanting to kill ALL MACS!!!!!!!!!

---

### Post by stream303 on 2008-03-21
You are just being tested by your mac for worthiness :)

Are you burning the CD / DVD at a slow enough speed?  What are you using to burn the ubuntu iso image with, and are you burning it as an iso and not just copying it over?

When you boot by holding down the cmd(cloverleaf)-Option(alt)-O-F keys while powering on, (I always need about 6 more fingers to do this...) and you reach the open firmware prompt, and with the ubuntu disk already in the firewire drive, are you typing this at the prompt:

```
boot fw/node/sbp-2/disk:,\install\yaboot
```

Don't sweat it - somewhere something's getting overlooked.

---

### Post by Kasa on 2008-03-21
I have trypes opening the Openfrimware prompt, using that method I never get a response :>.

I burned the CD on my Ubuntu system, (Its the ppc-livecd). the speed might have something to do with it, But I am using a really old reads (made in 2003 :?).
as I said before When holding option key on startup it loads a location where I can select the mac HD or the CD, If i select the CD it will just go black then invert the colours.
Is there any reason why the open firmware wont boot ?

and I think i burned the cd at x75 I THINk :/.

---

### Post by stream303 on 2008-03-21
Hmm..  Can you try again with the "alternate" install image, and then burn with a speed of something ridiculous like 2x or 4x?

How are you burning the iso with Ubuntu?  Are you right-clicking the downloaded image, and selecting write image to disk, or are you copying the image to the cd manually?

---

### Post by Kasa on 2008-03-21
I got into it xD (seems having my hand on the mouse dosnt help.)
now how can i fix " load to low or something like that"
(openfireware prompt that is)

---

### Post by Kasa on 2008-03-21
I now know wat it says 
```
LOAD-SIZE too small
```
how can I fix that :?

---

### Post by Kasa on 2008-03-21
Reading about on the internet, it seems I am doomed, doesnt it.
I havent yet found one Distro, or person that has had this error and solved it :/.
This is making me depressed as I would of enjoyed ubuntu on a laptop which is portable, instead of having it share my PC tower with vista.
U know, if Ubuntu ever goes out and make towers/laptops/ect. like apple have.
I would buy Ubuntu and to think maybe Apple would be doomed seeing the cost of production of a BASIC ubuntu tower would be much smaller to say and normal apple tower.
Ubuntu would win in my vote xD

ANy way.
IF someone knows how to fix this 
```
LOAD-SIZE to small
```

Please do tell me , I am really wanting to get this computer "fixed" xD

---

### Post by Kasa on 2008-03-22
Ok,
I fix the problem by removing a space between (disk:, and \install)
now when i boot into the Live CD of Gusty, (I used live-nosplash-powerpc video=ofonly)
I can't see the MAC INTERNAL HD :/.
I clicked install and got up to the Partitioner and still no HD found AT ALL!!!!!!.
I will try 6.06 and see if it can see it, if it can then I should be ok.
Anyidea why Gusty wouldnt beable to see the HD :?.
(i am thinking the fact that its a mac HD xD might be wrong tho)

---

### Post by stream303 on 2008-03-22
> **Kasa said:**
> 
IF someone knows how to fix this 
```
LOAD-SIZE to small
```

Please do tell me , I am really wanting to get this computer "fixed" xD

I found something interesting here, look at Rudelota's response about resetting the pram and nvram with the load-size problem:

[http://www.backports.ubuntuforums.org/showthread.php?t=445111](http://www.backports.ubuntuforums.org/showthread.php?t=445111)

I don't have this issue, so I'm not sure how it will affect your mac.  But now that we're comfortable getting into openfirmare, maybe this will help.

[http://docs.info.apple.com/article.html?artnum=42642](http://docs.info.apple.com/article.html?artnum=42642)

---

### Post by Kasa on 2008-03-22
Ok, Might I say you have been a massive help.
Now would u know anything about seting up a bcm3418 wireless card  with WEP Plain encryption ?

I have it set up with my wifi moden with no Encryption atm which isnt what i really want.
I am not sure how to set up the encryption on a PLain system which is current ly inplace.
any ideas  ?
or should i just upgrade to gusty and see if thats easyer xD.
(which I am going to do anyway.)

---

### Post by Kasa on 2008-03-23
ok, 
when i boot into gusty on the liveCD and hit install it gets to the partitioner and well no HD is shown.
I was thinking this was a MAc format problem, but I think it cant be now 6.06 is installed.
I am hoping to install 7.10 as my wifi on 6.06 isnt working (well I works now and then if I do massive amounts of terminal use).

Does anyone know why a HD wouldnt show up on install of 7.10 ?

---

### Post by Kasa on 2008-03-23
Ok, I am going to see is installing festy (if it will read my hd) then gusty might work.
is there anyone that knows why my HD wont be read on the Gusty live cd!!!!!

---

### Post by slacka-vt on 2008-03-25
You ever try the dapper live-cd on your machine ?

~s

---

### Post by Kasa on 2008-03-26
I firstly installed Dapper (LiveCD) then Feisty (liveCD) gusty wont read the HD.
BUt I will try the install with a Ethernet cable for internet, Some reports say haveing working internet might help.

---

### Post by slacka-vt on 2008-03-26
well,

          I guess my next question would be
- if those prior installs worked, then why did you upgrade ?

Dapper and Hardy are supported on the PPC platform and Edgy - Gutsy are not.
Newer does not always constitute better.
It's all about stability.
I actually completely gave up on Ubuntu for 3 years.
This Hardy release has got me reevaluating my stature.

~s

---

### Post by Kasa on 2008-03-26
Dapper might be stable, but trying to get that inbuilt wireless card to work was crazy.
feisty is working atm, But seeing hardy is no the stable PPc might try and give that a go, when its out.
atm I will stick with feisty it seems to be working fine.

---

### Post by Kasa on 2008-03-26
A recommendation to all  Bcm4318 card users 
Feisty Works best.
is was extremely easy compared to 6.06 .

A must for all PPC users with a wireless BCM43xx and mainly for the troublesome 18 cards.

---

