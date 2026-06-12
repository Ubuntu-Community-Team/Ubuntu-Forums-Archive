---
title: "Can I use Ubuntu ?!"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by fomscu on 2007-06-08
Hi there, 

I'm new to the LINUX world ... searching for a good distribution to begin with, friends told me about ubuntu !
but I'm still afraid about beginning.

I'm a medical student and my Pc contains many important files ( exceeding 100 gb ) 

my computer is :
pentium 4
1.7ghz intel processor
128 mb of RAM
AVI RAGE 128 PRo ULtra AGP
Creative Audio 128 vebra
D-link Ethernet Adapter 
ASUS CD 52x
HD 2 x 80gb = 160 gb

FIRST: Are these parts completely supported ?

Second: I can have a free 20 gb partition, So can I use it to install Ubuntu on without affecting the remaining partitions? and how, plz?

Thanks a lot In advance !

sorry for interruption

---

### Post by Bachstelze on 2007-06-08
128 MiB of RAM is a bit low. You will be better off with Xubuntu if you want an Ubuntu based system. Also, that ATi card could cause problems...

---

### Post by RichPicker on 2007-06-08
You can use it from the partition to see if you like it, with dual boot. Or use it directly from the live cd.

---

### Post by Nekiruhs on 2007-06-08
> **RichPicker said:**
> You can use it from the partition to see if you like it, with dual boot. Or use it directly from the live cd.
No, he can't unfortunately. The Live CD requires at least 256 MB ram

---

### Post by ccfjeff on 2007-06-08
> **Nekiruhs said:**
> No, he can't unfortunately. The Live CD requires at least 256 MB ram

I believe s/he could run [the Xubuntu version]("http://www.ubuntu.com/products/whatisubuntu/xubuntu") on LiveCD.  S/He might have to use the Alternate CD to install, though.

---

### Post by fomscu on 2007-06-08
So, If I raised my RAM to 256 mb ... what will be the case?

by  the way ccfjeff , It is HE !

---

### Post by Nekiruhs on 2007-06-08
If you upgraded your ram to 256, the normal install would work and Ubuntu would be happy. If not, you might have to go with the alternate install CD (text only, but its easy and we can walk you through it) and  use Xubuntu (Uses XFCE instead of GNOME, different apps and user interface).

---

### Post by fomscu on 2007-06-08
You mean I still can use Ubuntu with my 128mb RAM ?

if so, when using this ( alternate install CD ) .. will my Ubuntu version after installation be the same as others ?

---

### Post by Nekiruhs on 2007-06-08
Yes, you can still use Ubuntu, but you may get better performance if you use Xubuntu. And your install will be identical to a live CD install.

---

### Post by kittyhawk63 on 2007-06-08
Just to rouse you. Who's paying for your medical schooling? That cost some dollars. I would suggest that you spend a few more dollars and, if possible, have at least 512 MB of RAM. You won't be sorry. Memory is so much cheaper these days. Just make sure that your cards are completely compatible. I kicked out my 128 MB card in my computer and kicked in two identical 256 MB cards and have never regretted it. I have one slot to go and just may fill it one day. The more memory you can afford, the faster and smoother your computer works, and it avoids all that caching back and forth except in heaviest demands.
Dr. kh

---

### Post by fomscu on 2007-06-08
Nekiruhs, thanks a lot....

Dr.Kh , I got your advice. Thanks.

but I still have a question !

the docs say that ( free space is that still RAW Not just with no files ) or something like that....


**[COLOR="Red"]So will I be able to install Ubuntu with my win-xp side by side ?[/COLOR]**

---

### Post by Nekiruhs on 2007-06-08
You should be able to. Just shrink your windows partition using the gParted live cd, and use the alternate install CD to install it.

---

### Post by jonom on 2007-06-08
How the heck do you run Windows in 128mb of ram? That must be painful. :eek:

---

### Post by Nekiruhs on 2007-06-08
You should be able to. Just shrink your windows partition using the gParted live cd, and use the alternate install CD to install it.

---

### Post by fomscu on 2007-06-08
> **Nekiruhs said:**
> You should be able to. Just shrink your windows partition using the gParted live cd, and use the alternate install CD to install it.

will this affect my files? ( I'm really afraid !)

---

### Post by ugm6hr on 2007-06-08
> **fomscu said:**
> will this affect my files? ( I'm really afraid !)

If you have a spare 20GB partition, and haven't backed up your other files - I wouldn't bother.  20GB is plenty for Ubuntu to start with.

---

### Post by fomscu on 2007-06-08
> **jonom said:**
> How the heck do you run Windows in 128mb of ram? That must be painful. :eek:

I wonder what speed will I gain if I raised my RAM !;)

---

### Post by fomscu on 2007-06-08
> **HymnToLife said:**
>  Also, that ATi card could cause problems...

what are the expected problems regarding an ATI card?

---

### Post by steve.horsley on 2007-06-08
> **fomscu said:**
> 
the docs say that ( free space is that still RAW Not just with no files ) or something like that....


**[COLOR="Red"]So will I be able to install Ubuntu with my win-xp side by side ?[/COLOR]**

If you have free space - free as in not even allocaed to a partition, then you can just tell the installer to "use the biggest free space" and it will then create the two partitions that it needs in that space. 

You could create the two partitions by hand with a partitioning tool (the installer partitioner can do this) but probably easiest is to use a partitioning tool to delete the one partition that you don't want (you can probably do this from Windows), and  then let the Ubuntu installer use the free space and figure out the sizes and types of the new partitions that it will put in there for itself. If you don't already have an extended partition, the installer will probably create one and then put a couple of logical parttions inside that. The second of the two partitions it needs is a smallish partition used as swap space for paging virtual memory to.

---

### Post by fomscu on 2007-06-08
> **HymnToLife said:**
>  Also, that ATi card could cause problems...

what are the known problems that may happen with my ATI card?

---

### Post by jonom on 2007-06-08
> **fomscu said:**
> will this affect my files? ( I'm really afraid !)
Back them up! :!:

Seriously - if you have stuff you don't want to lose back it up. This goes for day-to-day operation as well as screwing with partitions. 

I don't know where you live, but I've seen 500G hard drives for as low as $120 Canadian recently. You can find used drives for very cheap.

---

### Post by jonom on 2007-06-08
> **fomscu said:**
> I wonder what speed will I gain if I raised my RAM !;)

Lots.

What version of Windows are you running? I can't imagine XP running in 128mb -- 512mb minimum.

If you are running 98 you will see a lot of speed increase.

---

### Post by AndyCooll on 2007-06-08
> **fomscu said:**
> what are the known problems that may happen with my ATI card?

It's an older card that's all. However I disagree with what he says, that card will work fine with a basic Ubuntu setup. You'll only start to have issues the card if you want to do graphics intensive stuff. It's the same as in Winderz, the more graphics intensive stuff you want to do the more powerful the graphics card you need, but for every day stuff a bog standard card will do fine.

:cool:

---

### Post by fomscu on 2007-06-08
> **jonom said:**
> Back them up! :!:

Seriously - if you have stuff you don't want to lose back it up. This goes for day-to-day operation as well as screwing with partitions. 

I don't know where you live, but I've seen 500G hard drives for as low as $120 Canadian recently. You can find used drives for very cheap.

I live in Egypt ! you know it ? ... the piece of land that connects Asia to Africa !

Any way ... the biggest HD size here is 200G !

I'll try to back my files up, actually after the end of my exams ;) ..

regarding windows, I use XP with no problems ( I don't know how !).

---

### Post by fomscu on 2007-06-08
> **AndyCooll said:**
> It's an older card that's all. However I disagree with what he says, that card will work fine with a basic Ubuntu setup. You'll only start to have issues the card if you want to do graphics intensive stuff. It's the same as in Winderz, the more graphics intensive stuff you want to do the more powerful the graphics card you need, but for every day stuff a bog standard card will do fine.

:cool:

thanks, I think it is fine now to begin !

but I'll still need your help, friends ! ;):D

---

### Post by fomscu on 2007-06-08
I forgot something,

After installing ubuntu, will the other partitions ( FAT Format ) be accessable through Ubuntu?

---

### Post by Enverex on 2007-06-08
> **fomscu said:**
> I wonder what speed will I gain if I raised my RAM !;)

Considerably, it means things will load faster and you'll find it thrashes your Hard Drive a lot less.

> **fomscu said:**
> what are the expected problems regarding an ATI card?

You shouldn't have any with this card, it's old enough to be well supported by the OpenSource ATi driver that comes with Ubuntu by default.

> **fomscu said:**
> I forgot something,

After installing ubuntu, will the other partitions ( FAT Format ) be accessable through Ubuntu?

Yes, you can read and write to them, even your NTFS drives.

---

### Post by kittyhawk63 on 2007-06-08
> **fomscu said:**
> I live in Egypt ! you know it ? ... the piece of land that connects Asia to Africa !

Yes, it seems that I have heard of that land before...let me see...oh yes, didn't someone named Moses once leave there with a few of his compadres after a nice vacation in the luxury of a nearby oasis?

Any way ... the biggest HD size here is 200G !
I'll try to back my files up, actually after the end of my exams ;) ..
regarding windows, I use XP with no problems ( I don't know how !).

I have a 160GB hard drive and Ubuntu uses very little of it.

A problem with ATI cards?
I have an ATI card and it was difficult, at least, in getting it to work. However, after trying a number of suggestions, I found that changing one word in xorg.conf made all the difference. If you have trouble with your card, and not all do, then keep me, and others, in mind and we can offer you some suggestions. Keep a positive mind though. It can be worked out.

---

### Post by xDaveManx on 2007-06-08
I can't tell what type of RAM you are using, but you can get a 512 MB stick of DDR400 at New Egg for [less than thirty bucks]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820145026").  Other types of memory should be priced similarly. That would put you at 640 MB, more than enough to handle the latest flavors of Ubuntu, I would think.

Before you go tinkering around with a major install, make sure all your files are safely backed up on removable media like DVD-Rs or CDRs, and use the Live CD to see if you can open all your necessary formats.  In lots of cases, there are workarounds or obscure open source programs that mimic the functionality of Windows, you just have to look.

Have fun, and I hope things work out!

---

### Post by a85lee on 2007-06-08
> **fomscu said:**
> what are the known problems that may happen with my ATI card?

Ubuntu is not automatically have driver support for ATI graphic card, but I think it wouldn't be a big problem, ATI just published the usage fro Linux, you can check out is your card in the list from ATI official website.

---

### Post by Enverex on 2007-06-09
> **a85lee said:**
> Ubuntu is not automatically have driver support for ATI graphic card, but I think it wouldn't be a big problem, ATI just published the usage fro Linux, you can check out is your card in the list from ATI official website.

Please people, stop giving wrong information.
Ubuntu DOES come with support out of the box for this card. It's the newer cards that need the fglrx driver that have issues.

---

### Post by ramjet_1953 on 2007-06-09
I agree that you should upgrade your RAM, if you really want to get the best out of your Linux experience. 

Both GNOME and KDE, being GUI's, need a bit of elbow room to do their thing.

As far as the install of Ubuntu goes, why not think outside the square and totally protect your valuable files that you have and just buy another HDD?

They are cheap these days and this way your files are secure and you can play with Linux to your heart's content.

Believe me, you won't be able to help yourself, you will tinker with the install, until you break it.

 We've all done it and it's all part of the learning curve and fun you can have.

I love the cliche "If you break it, you get to keep both pieces".

Regards,
Roger :cool:

---

### Post by fomscu on 2007-06-09
Thanks to all of you ,friends.

> **ramjet_1953 said:**
> 

Believe me, you won't be able to help yourself, you will tinker with the install, until you break it.

 We've all done it and it's all part of the learning curve and fun you can have.

I love the cliche "If you break it, you get to keep both pieces".

Regards,
Roger :cool:

Is there any step by step tutorial for installing Ubuntu with pictures ?

---

### Post by Enverex on 2007-06-09
> **fomscu said:**
> Thanks to all of you ,friends.



Is there any step by step tutorial for installing Ubuntu with pictures ?

When you run the install CD it takes you to a GUI to install it and it explains everything as you go along.

---

### Post by ugm6hr on 2007-06-09
> **fomscu said:**
> 
Is there any step by step tutorial for installing Ubuntu with pictures ?

But this will make sure there are no surprises:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Although - the partitioning section may be a bit different for you - since you have a spare 20GB partition.  I would recommend, for simplicity, that you delete the 20GB partition (and leave it as unallocated/unpartitioned) BEFORE starting the install process, and use the "Use largest continuous free space" option to install.

---

### Post by southernman on 2007-06-09
I can confirm you will have no problems with your video card. I have one in a backup pc that works just fine. Even my ATI Radeon X850 works *without *the restricted drivers.

I can understand your hesitation about loosing data. IF you are not accustomed to doing regular backups... one may wonder just how worried you could be. I mean, you are using windows... right? :P Kidding aside KEEP a backup regardless of what OS you choose to use.

As for your ram - you should be able to ebay or pricewatch.com some really reasonable.


Good luck and happy Ubunting, Xubunting

---

### Post by fomscu on 2007-06-09
How much time will the installation procedure take?

---

### Post by ugm6hr on 2007-06-09
> **fomscu said:**
> How much time will the installation procedure take?

On that hardware - I would guess 30-40 minutes... 

For a benchmark - I installed Xubuntu7.04 for a LiveCD on PIII 700MHz / 256MB RAM in 20 minutes.  Definitely infinitely faster than Windows XP (about 4 hours on the same machine).

---

### Post by Enverex on 2007-06-09
> **fomscu said:**
> How much time will the installation procedure take?

About 20 minutes depending on the speed of your PC.

---

### Post by Sweet Mercury on 2007-06-10
> **fomscu said:**
> Hi there, 

I'm new to the LINUX world ... searching for a good distribution to begin with, friends told me about ubuntu !
but I'm still afraid about beginning.

I'm a medical student and my Pc contains many important files ( exceeding 100 gb ) 

my computer is :
pentium 4
1.7ghz intel processor
128 mb of RAM
AVI RAGE 128 PRo ULtra AGP
Creative Audio 128 vebra
D-link Ethernet Adapter 
ASUS CD 52x
HD 2 x 80gb = 160 gb

FIRST: Are these parts completely supported ?

Second: I can have a free 20 gb partition, So can I use it to install Ubuntu on without affecting the remaining partitions? and how, plz?

Thanks a lot In advance !

sorry for interruption

I'm curious what your running now with only 128 MB of RAM?

RAM is generally very cheap. Unless you have a particularly expensive requirements you should be able to upgrade for under $100. Don't let that be what stops you from switching.

---

### Post by will_blix on 2007-06-10
Sir's,
Just to add up since I have the same question above, we have a spare PIII and my only option is to add aditional RAM. Will it be still possible to install to this rig? Thinking that PIII is much slower and runs only at 500 Mhz. Also is there a need to install video graphics adapter driver and how please? Thanks!

---

### Post by fomscu on 2007-06-11
> **ugm6hr said:**
> On that hardware - I would guess 30-40 minutes... 

For a benchmark - I installed Xubuntu7.04 for a LiveCD on PIII 700MHz / 256MB RAM in 20 minutes.  Definitely infinitely faster than Windows XP (about 4 hours on the same machine).

so 30-40 minutes for Ubuntu

and 20 minutes ( or less ) for Xubuntu !

I decided to upgrade my RAM to 512 ISA

so, wait for me to install it soon :D

---

### Post by bigboy_pdb on 2007-06-14
will_blix, I have a Pentium 2 with 250MB of RAM and a RIVA TNT graphics card with 16MB of RAM and I'm running Ubuntu on it. Sometimes it's a little slow in comparison to my computer that's a Pentium 4, but it works quite well. If your graphic card and other hardware are supported then I would think that it should work fine with a Pentium 3 chip and 250MB of RAM. Although, I wouldn't recommend using Kubuntu. I tried it on someone else's computer (which I think was a Pentium 3 with an onboard graphics card) and it was pretty slow because of the fading effects.

---

