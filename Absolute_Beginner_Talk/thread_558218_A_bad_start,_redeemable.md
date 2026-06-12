---
title: "A bad start, redeemable?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Godsgimp on 2007-09-23
Hi all.

**Synopsis:** Need help with Ubuntu basics, particularly wireless internet access.

I'm an absolute beginner to Ubuntu/linux having been a windows user for years. After using as much open source software as my windows installation allowed I decided it was time i try out Ubuntu having heard good things. Unfortunately things went bad at the start. I read as much about installation as i could then followed the instructions. I needed to dual boot my system because I couldn't afford to have my work interrupted. Unfortunately the installation crashed and left my hard disk corrupted, and me up @#$% creek without a paddle. A windows bootable cd reported the hard drive missing and I was forced to go whole hog and format and install Ubuntu. Now I must get it working properly for work in a days time. And I know I need help.

I am sure with the right advice I can help my Ubuntu installation redeem itself! I am hoping to be pleasantly surprised and converted. My needs are fairly straightforward.

-It is imperative that I get my **wireless** working as quickly as possible. At this time I am using another pc to access the internet.
-the system start up takes a heavy 7minutes. Is this normal, are their ways to improve this (drastically)?

My laptop is a-
[B]HP Compaq nx6310
Intel Centrino Duo
1Gig RAM
40Gig HDD[/B]

The Ubuntu version is **6.10 Edgy Eft.**

I really want to make full use of my Ubuntu experience! Can anyone help me, help Ubuntu redeem itself. I will continue reading the forums for help meanwhile.

Thank you.

---

### Post by Daveth on 2007-09-23
Hallo. Welcome to the Ubuntu forum. 
Sorry to hear about your installation woes. 

It would be useful for us to know what stage the installation failed, whether this was an "official" live cd, or one you made yourself, and if you ran the live cd beforehand and whether it picked up your hardware. Lots of folk dual boot and wireless support seems much better, though I am old-fashioned and place greater faith in cables!
I'm sure we can help you out.

---

### Post by the.phantom on 2007-09-23
this kink might help a bunch?

[http://screencasts.ubuntu.com/MoS2007/Ogg_Medium](http://screencasts.ubuntu.com/MoS2007/Ogg_Medium)

you can watch how to do a normal install in flash or open source ( so you could watch in live cd)

just select installing ubuntu part 1
it is about 20 min long but sure makes it easier tio understand the install

installing ubuntu part 2 is a lot more advanced install

on the left side click what format and then click the image of install part 1
then next page click the download and it will stream it

---

### Post by Godsgimp on 2007-09-23
Hi Daveth

They are right when they say the Ubuntu community is responsive, it's nice to know!

I have an the official cd which my boss got from  Shuttleworth himself. I checked it for errors before going ahead with the install, as I am paranoid (and proved right to be,  it seems) On installing I choose the first partition option. The install failed on the repartitioning of Windows, after that the drive became unusable to windows and so i am thrown into the Ubuntu deep end, and I had to format completely. But my objective is not to get my windows back , I just want to forge forward with Ubuntu.

---

### Post by HereInOz on 2007-09-23
I notice you are using Edgy.  You will perhaps have more success if you use Feisty for the moment, as it has much better laptop support.  This may be difficult if you have no way to download the iso, but if you can get someone to get it for you, it could make your life easier.

Also, you may want to tread the bleeding edge and have a look at Gutsy, due for release in October.  It is still in alpha, but its wireless support is much better than either Edgy or Feisty.

7 minutes sounds a long time for a boot up.  Something is not right there, but I can't think what it might be.  Do you perhaps have a hard disk which is a bit suspect?  That could have been the source of your problems to start with.

---

### Post by EchoBeach on 2007-09-23
Hi godsgimp
I'm not an expert, but I do know that not all wireless hardware/configurations are supported.
Do you have any way of plugging the laptop into an ethernet connection?  Does it work without wireless?
Echo

---

### Post by Godsgimp on 2007-09-23
Hi Echobeach

According to this [page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel") my wireless card is supported. Although in network settings I can't seem to get it to work.
I haven't tried yet, but I may be able to connect using the cable this pc is using. Can that help me then with the wireless?

---

### Post by Godsgimp on 2007-09-23
HereinOZ

Yes Edgy is the latest release I could get my hands on. I could try fiesty download on this pc which is my home desktop. But what you have to know is that in South Africa our internet is supper slow. 700mb may well take me days to download. Is there a way of upgrading my current install?

I can't yet suspect the HDD as it was working fine before.. It is a relatively new laptop. Although I thought it was illegal to make them with such small HDD's these days... :0

---

### Post by tgalati4 on 2007-09-23
Keep the faith.  Despite the setbacks, you will get a clean install after a while.  Feisty is definitely the way to go for newer hardware.

What failed during the repartition?  Did Windows not boot properly or did you not select to resize the Windows partition and put Ubuntu on the second partition.  It's always worked for me and several others.

Sometimes the initial installation can be daunting, but after a while it becomes simple and easy on future machines.

---

### Post by Godsgimp on 2007-09-23
tgalati4

Ubuntu crashed and froze while repartitioning windows. Making space for itself. It froze, and I left it for an hour to be sure then had to restart the machine.

---

### Post by Godsgimp on 2007-09-23
As it stands now, I ma unable to access the internet on the laptop using wireless or lan cable. It is also already 2am in the morning I have been struggling with this for most of yesterday and the first part of today, it is time I went to bed. Maybe sleeping on it will help.

Appreciate being made to feel welcome. Even if I am still at a loss.
Speak soon.

Update: Mon 24th Sept 9am

Trying not to double post! 

I have today to fix all my woes. it's a public holiday, national barbecue/braai day. Then I return to work. I really need to get my internet working by then. All help is appreciated.

---

### Post by Godsgimp on 2007-09-24
I'm not getting anywhere. Without internet on the laptop it is extremely difficult to get anything fixed. And as much as I search I can't find the answers I am looking for. And unfortunately the high turn over rate at these forums is working against me, my post slipping down the lists into obscurity. :0

Time constraints, I need to have wireless by tomorrow morning 9am for work, mean that I am going to have to take drastic measures. It seems Ubuntu is fated to fail for me.. I am upset.

I am going to have to format my HDD in dos and reinstall Windows. A pity, but I can't afford to not have a functioning internet connection since all my work is online. 

Thanks to all who tried to help last night. The responsiveness of the Ubuntu forums really is amazing, I would wish to stick around. I will have to reinstall windows this evening, sad :(

---

### Post by Daveth on 2007-09-24
why not re-install windows, defrag the files, and partition from within windows, say 50:50 on your 40 gb, then try Ubuntu in the 2nd half? It will write grub into the windows boot partition and will give you the option of dipping in and out of windows, so you will always have a failsafe. Seems a shame to give up on a Shuttleworth -given cd- he hasn't autogrpahed it, has he?

With Ubuntu you would be best making a separate /home partition, so you can upgrade more tidily. So really quite redeemable I think. Anyway, hope you national holiday was not spoiled.

---

### Post by Godsgimp on 2007-09-24
Hi again Daveth

That is what I spent most of today trying to do. For some reason the windows CD still wouldn't recognize the HDD. Eventually I found that a file was corrupt on the Windows CD. So I once again reinstalled Ubuntu 6.10. But this didn't fix the wireless problems.. Fortunately a friend came to the rescue with a Mandriva Live CD, I installed that and it autodetected my wireless card and set my internet up in about 2min as opposed to not getting anywhere with Ubuntu. 

So with my internet working I think I will stay with this install until I can get a fresh working windows cd. Install that and format the drive with either a shared FAT32 or a /home partition. Im told thats the best but not the easiest? Then I will install either fiesty or if I wait a little.. Gutsy. That would be nice. And with any luck by then I will be a little more proficient then I am now. Expect to see more of me on these forums!

As for Shuttleworth given CD, our company was working with one of his here in Cape Town a while back, he handed over a couple o hundred CD's. Like candy!

---

### Post by EchoBeach on 2007-09-24
Do you have a (spare) HDD that you could connect to the laptop via USB - to retry installing Ubuntu.
A lot of people recommend using separate disks if at all possible.
If the laptop has a boot option to allow you to select a boot device at startup - before MBR and GRUB ...
Echo

---

### Post by tgalati4 on 2007-09-24
Sorry to hear of your troubles.  That's the first case that I have heard of Ubuntu freezing like that during a partition sqeeze.  Any you are correct that you need a network connection to search for answers.  I would stick with Mandriva for a while (since it's working) and spend some time with it.  Then get a Gutsy CD in October.  

It only gets better.

---

### Post by Godsgimp on 2007-09-25
Thanks guys

Thing is to me a working internet connection "IS" a computer. Without one.. it's pretty useless to me. So Ubuntu not being able to set up my wireless was a bad thing, although it did see my wireless card.. 

Eventually when I get all the problems sorted out what I want from my Ubuntu experience is to see if it furthers my internet experience. I wouldn't mind something like what dyna-bolic is for creatives but as an internet experience.. now that would be cool.

Heres looking forward to Gutsy!

---

### Post by Godsgimp on 2007-09-27
I figured out that installing Ubuntu.. or any Linux I guess. Changes a setting on SATA hard drives. Something about enabling "Native settings". This is what was preventing windows from seeing the hard drive after Ubuntu crashed during install. hectic

---

### Post by Godsgimp on 2007-11-06
Just thought I would let those who helped me know. I waited for Gutsy using Mandriva in the interim. Boy am I happy I waited.

Gutsy installation was a breeze, took less than thirty minutes! Been using it now for two weeks and basically I'm a convert. Burnt the .iso to several Cd's and have handed copies out to a bunch of people, hope they get the same enjoyment from it as I do.

Regards

---

