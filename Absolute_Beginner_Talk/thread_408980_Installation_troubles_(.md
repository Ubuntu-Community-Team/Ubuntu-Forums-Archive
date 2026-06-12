---
title: "Installation troubles :("
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by dmpolska on 2007-04-14
Hey guys. I am totally new with linux and know very, very little about it. However, I downloaded version 6.10, put it on a CD etc. and as I type this I am running off Linux live CD. Okay, so here is my problem. 

First, everything goes fine at start up except when I select the option in the begining to scan for errors. 

When I do that I receive around 15 of these errors: 

ubuntu buffer i/o error on device hda   ###some numbers###

This error though doesn't seem to have any effect on the installation though, and it all goes through and loads to desktop. When from the beginning of the disk I select install etc. that error does not show up and i go to desktop too. 

Now, at installation.. first I had some problems partitioning the drive, but it seems that through extensive trial and error I got that to work. 

But now during installation it seems to freeze at 43% each time. 

At 43% it seems like the disk stops spinning. After this happens i can still move the mouse, but, if i select something like firefox the whole screen freezes. 

I am not sure what to do I really want to run Linux! 

thanks for reading this and any responses to this

---

### Post by dmpolska on 2007-04-14
additional details: 

I have a 4.88 GB size set for linux-swap and a 4.89 GB set for ext3, before installation.

---

### Post by mikewhatever on 2007-04-14
Try burning another CD following this how-to [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29)
It's a good idea to md5sum check the downloaded iso file too, because that could be the problem, rather then the CD.
[https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29](https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28md5sum%29)

You swap partition is way too large. Resize it before the installation. The max size should be double you RAM size.

---

### Post by dmpolska on 2007-04-14
mikewhatever, I followed all of those steps listed and ran the msdsum check. 

Can you please explain by what you mean my partition drive size is too big and that it should be double my ram? 

Originally I had partitioned a drive L: for 10gb, then in Ubuntu Live I partitioned it to 5 and 5. 

My ram is .99gb. So your saying I should have it as 8 ("/") and 2 gb swap?

Thanks again

---

### Post by mikewhatever on 2007-04-14
> **dmpolska said:**
> mikewhatever, I followed all of those steps listed and ran the msdsum check. 

Can you please explain by what you mean my partition drive size is too big and that it should be double my ram? 

Originally I had partitioned a drive L: for 10gb, then in Ubuntu Live I partitioned it to 5 and 5. 

My ram is .99gb. So your saying I should have it as 8 ("/") and 2 gb swap?

Thanks again
Ubuntu swap partition is similar to the page file in Windows. It is used to extend RAM and hold RAM content on hibernation. I am sure you can find better definitions on the web. The size of swap can vary depending on the size of RAM and the nature of tasks the PC is used for. Users with only 256 - 512 MB of RAM will definitely need a swap of 1.5-2 times of RAM, but users with more then 1GB may not need swap at all (unless want to hibernate).
I also have 1GB of RAM and 0.94 BG swap. It never got used until I started to use Beryl, but even then, not more then 50 MB. In your case, even 2 BG is too much. I'd go for 1-1.5 BG if planning to hibernate or run heavy tasks and numerous programs. Either 8 GB root, 2 GB swap, or 9BG root, 1-1 BG swap is better then 5 & 5.

---

### Post by dmpolska on 2007-04-14
Thanks mikewhatever. It still did not work though :( 

Can there be a problem because I have a PheonixBIOS?

---

### Post by dmpolska on 2007-04-14
Still doesnt work, keeps freezing at 43%, so i will provide some more details. 

When running InfraRecorder and selecting the iso etc, these were the options at which i recorded. 

Write method - Session-at-once (SAO)

Eject the disk after writing - CHECK 
Simulation - NOT CHECK 
Buffer underrun protection - CHECK 
Pad data tracks - CHECK 
Fixate the disk after writing - CHECK 


Okay, now here is the image of my partition in Ubuntu, taken from my camera. 

[http://img.photobucket.com/albums/v415/dmpolska/V12001.jpg](http://img.photobucket.com/albums/v415/dmpolska/V12001.jpg)

In that picture, the reiserfs filesystem is selected, but I have tried both ext2 and ext3 (usually working with ext3) 

Any help on why it freezes at 43% is welcome.

---

### Post by Loki-uk on 2007-04-14
Hi this might not be whay your looking for but I've been wanting to try to learn Linux for ages but I only have 1 PC and need windows. So I have installed Virtual PC 2007 which is free and then ubuntu 6.06.11 LTS into that. I've made an install guide at [www.aotk50.dsl.piepx.com/default.htm](www.aotk50.dsl.piepx.com/default.htm). This is still a work in progess but the Ubuntu section is mostly finished but since Ubuntu is running as a VM you don't need to worry what hardware your PC is. I'm still working on the VM Additions section ask we speak.

Thanks

Loki

---

### Post by randell6564 on 2007-04-14
Hi!
In my opinion, you have a corrupted download of 6.10.  try downloading the OS again, and this time burn it to cd as slow as possible.
Next, try just letting Ubuntu setup your drive space. (in other words, don't mess with manual partitioning).

---

### Post by dmpolska on 2007-04-14
Thanks for your help guys. I now have Ubuntu running! (with one probleg m) 

I got it running by: 

Reinstalling the ISO onto a DVD-RW writing at 1X speed. Simple, just, good thing it worked. 

However this is my current problem. 

Whenever I try to download anything, Flash (for using youtube) or the Updates (140 of them or something around that), my internet totally shuts down and I have to restart in order for it to work again. 

I have plugged in an ethernet cable which is running at eth0, but I have wireless which I would like to use (need to use) name: lo, which doesnt work alltogether. 

The main problem is whenever I try to download ANYTHING, including the mos important thing (updates, firefox pluggins), internet shuts down and I cant turn it back on. 

Any ideas?

---

### Post by Sabar on 2007-04-14
> The main problem is whenever I try to download ANYTHING, including the mos important thing (updates, firefox pluggins), internet shuts down and I cant turn it back on.

Have you tried to go to other web sites? If you do, do they time out? 

You may need to go to My "Slow Internet Fix" link at the bottom of this post

I don't know if this is the problem or not but it may be

Sabar

---

### Post by randell6564 on 2007-04-14
> I have plugged in an ethernet cable which is running at eth0, but I have wireless which I would like to use (need to use) name: lo, which doesnt work alltogether.
'lo' is NOT your wireless.  go to 'System>Administration>Networking and DEactivate ethernet connection.
THEN, highlite 'Wireless Connection' and click 'Activate'.
THEN click 'OK'.  If you still can't access the net, then go back to 'System>Administration>Networking, and highlite 'Wireless Connection', and click on 'Properties'. Enter your 'Essid', Wep/Wap key (if you need one), and try again.

If this does not work then open a terminal and type:```
iwlist wlan0 scan
```and post the results.
Also post the output of:```
sudo gedit /etc/network/interfaces
```

---

### Post by dmpolska on 2007-04-14
Sabar, 

Yes, all other sites work. However, say I go onto Youtube, and I go to select to download the Flash, that does not work. Instead, it pretends to start downloading and the internet gets disconnected (dont know how if as of right now I am connected through cable.). Then I cant reconnect and must restart. 

Thanks for your reply though.

---

### Post by dmpolska on 2007-04-14
> **randell6564 said:**
> 'lo' is NOT your wireless.  go to 'System>Administration>Networking and DEactivate ethernet connection.
THEN, highlite 'Wireless Connection' and click 'Activate'.
THEN click 'OK'.  If you still can't access the net, then go back to 'System>Administration>Networking, and highlite 'Wireless Connection', and click on 'Properties'. Enter your 'Essid', Wep/Wap key (if you need one), and try again.

If this does not work then open a terminal and type:```
iwlist wlan0 scan
```and post the results.
Also post the output of:```
sudo gedit /etc/network/interfaces
```


Wow, randell, thank you so much. It worked after I activated wireless and typed in Linksys as my Essid. 

However, I have wondered what is the terminal? I read people here typing things in and getting outputs and I have no idea where that is.

 I will also try downloading updates and other things again, and I will tell you how it goes. 

Thanks again :)

---

### Post by dmpolska on 2007-04-14
Well, Updates are downloading! :)! I don't know why it's working with wireless and not with the wired connection. But that's okay for now :) 

Still not sure what a terminal is though, could you help explain that randell? 

Thanks again

---

### Post by randell6564 on 2007-04-14
> **dmpolska said:**
> Well, Updates are downloading! :)! I don't know why it's working with wireless and not with the wired connection. But that's okay for now :) 

Still not sure what a terminal is though, could you help explain that randell? 

Thanks again
Well..,it's not working with "wired connection" because you DISabled 'eth0'.
As far as "terminal", go to Applications>Accessories. Do you see the application 'Terminal'?  That is a [command line]("http://en.wikipedia.org/wiki/Command_line_interface") application.  Most Linux users like to use it to oversee and control their OS's.

You can update, install, and control every aspect of your computer using the terminal.
Anyway..,Glad that you got your updates!   Cheers!

---

### Post by dmpolska on 2007-04-14
Thank you again for your help randell. What I meant before is that even when the cable was plugged in and enabled and then i would go to update it would disconnect itself. That is unimportant for now though. But thanks anyway :) 

Time for Mplayer and Beryl!

---

### Post by randell6564 on 2007-04-14
> **dmpolska said:**
> Thank you again for your help randell. What I meant before is that even when the cable was plugged in and enabled and then i would go to update it would disconnect itself. That is unimportant for now though. But thanks anyway :) 

Time for Mplayer and Beryl!
The only way that I could decipher this is if you reverted back to DEactivating your wireless and REactivating your 'eth0'.
THEN I would ask you if you could access the internet BEFORE attempting to Update.  If you CAN, then it would not make sense! (Not being able to update).

When you say, "and then I would go to update", what exactly do you mean?  How did you aniciate the update?

---

### Post by dmpolska on 2007-04-14
Yes! It made no sense to me at all... but this is Linux and not anything like Windows so I thought maybe it was just some other weird error. 

Basically online would work with eth0. The message on the top bar would pop up saying "There are 164 Updates to Download." I would click on it... it would load for a little bit then bam the internet stops working, nothing downloads, and I was forced with restarting in order to get eth to work again.

---

### Post by randell6564 on 2007-04-14
> **dmpolska said:**
> Yes! It made no sense to me at all... but this is Linux and not anything like Windows so I thought maybe it was just some other weird error. 

Basically online would work with eth0. The message on the top bar would pop up saying "There are 164 Updates to Download." I would click on it... it would load for a little bit then bam the internet stops working, nothing downloads, and I was forced with restarting in order to get eth to work again.
Sounds like a connection Time-Out.  Try downloading and installing 5 to 10 updates at a time. (if that doesn't work, try less)
Update the kernel image first.  That is a big one!
IN FACT..,instead of clicking on the update icon, just go to System>Administration>Update Manager.  There, you can check and UN-check updates.  That way you can decide how many updates get downloaded at a time.  This will lessen the chance of a connection time-out!

---

### Post by dmpolska on 2007-04-14
Well right now they are all downloading fine using the wireless connection. And it was weird because the connection (multiple times/restarts) would time out during any kind of download (including Flash to Firefox). 

Quick question for you because you seem to actually read what I write :), for the Mplayer: 

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

For linux do I always download the one that says "source?" Thanks again :)

---

### Post by randell6564 on 2007-04-14
> **dmpolska said:**
> Well right now they are all downloading fine using the wireless connection. And it was weird because the connection (multiple times/restarts) would time out during any kind of download (including Flash to Firefox). 

Quick question for you because you seem to actually read what I write :), for the Mplayer: 

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

For linux do I always download the one that says "source?" Thanks again :)
NO,NO,NO!  That requires you to BUILD the application.  Since you are obveously new to the Linux world (me too), this would be a HUGE headache!!
Mplayer is available through System>Administration>Synaptic Package Manager.  As long as you have enabled the multiverse repo's in your /etc/apt/sources.list

open your terminal and type:```
sudo gedit /etc/apt/sources.list
```
post this here ok?  So that i can see it.  Then we will go from there.

---

### Post by dmpolska on 2007-05-26
Thanks for everyone help that helped me last time... including randell6564... I managed to download what I wanted to download with the help of a linux friend. 

I did not want to create a new thread for the  new issue, so I searched for this thread. 

Anyway, a short while after using linux, probably 4 days after, i abandoned it because of school work. Now, I want to try it again. I downloaded Feisty Fawn and since I am running on Vista, i can no longer use partition magic to partition my drive :( 

On the liveCD, i have two drives. 

7gig recovery
100gig or so drive which is 60 gig full. 

I want to create a new partition of about 22 gigs for Ubuntu, but on the liveCD i am not sure how to do that, and the guides that I found were only brief.. I do not want to erase the drive by accident. 

Any help would again be appreciated.

---

