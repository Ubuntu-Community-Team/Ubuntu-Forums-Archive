---
title: "My Initial Ubuntu Experience (Be kind please)"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by carlolovearianne on 2008-03-10
In preparation in buying my first laptop which will be either a Compaq Presario C733TU or V3017 which will be an Ubuntu exclusive laptop,  I installed Ubuntu on my brother's old beat-up PC (unbranded) with Intel Celeron 1.70 Ghz, 512mb RAM and 40GB HDD. 

I have an original iMac (333mhz) running OS X Panther. I bought it dirt cheap more than a year ago and upgraded it myself. Though still slow and quite painful to use, honestly, it still is a reliable machine. I was just looking forward to replacing it with a more modern (faster)  but affordable machine which I can use for my mp3 collection,  rip my entire dvd and vcd collection, surf the net and scan and edit old family pictures.  

The pc used to run Windows XP and  I knew it was a pretty beat up machine because my brother had the hardrive reformatted at least a couple of times, mainly because of severe virus infection. My experience with the particular pc wasn't very good as well. Susceptible to numerous hanging and kernel panics and also painfully slow, even when doing some mundane task such as typing with MS Word (but it still got me through college, though scathed). I had to add  a PCI LAN card ( a D-Link) and replace the optical drive as well (a real cheap Asus CD-ROM drive) before the installation. Both original parts were already dead. 

Installed Ubuntu using the 7.10 Live CD. The Live desktop took quite a bit of time showing up and for almost three minutes I was staring at a peach colored screen with a white cursor. When the live desktop did appear, I clicked on the install option and that also took a while to respond. Once the options for installation appeared it was straightforward all the way until 22% of the installing package screen showed up a message  "Encountered an error. Possible cause may be a defective optical drive..." (not verbatim but something along those lines). So I reboot, ejected the cd, wiped it clean and started all over again and this time it went by without a hitch. (Note: I disconnected the ethernet cable while the initial installation went thru). After about 45 minutes I was given the message that the installation is finished and I need to reboot. I reconnected the ethernet cable, rebooted and after around 30 seconds the log in screen came up. I entered the user name and password,  hit enter, peach screen again for a minute and then the  Ubuntu desktop finally showed up.

I first enabled All Repositories and Restricted Drivers. Unchecked unneeded services. I immediately downloaded the restricted drivers for the pc's Nvidia GeForce video card. Afterwards I ignored the need to restart and went ahead to the Add/Remove software and installed Advanced Desktop Settings. Only afterwards did i restarted. Once the desktop was ready, updates were made available by the Update Manager. Ignoring that for the meantime, I added the Medibuntu repository in the terminal. All of the following was installed in the terminal and went well smoothly; flash plug-in,  msttcorefonts, mpg123 and extra multimedia codecs. I also updated the entire system from the terminal afterwards. Using sudo apt-get update and sudo apt-get upgrade (175 updates in all according to Update Manager). 


After rebooting I transferred my mp3  collection (very integral that it work in Ubuntu) and played them using Rhythmbox. My only reservation is that Rhythmbox is not displaying the album covers. So I made a mental note to download and try out Banshee, Amarok and whatever else is there until I find the right one for me. Though still no iTunes contender, Banshee is ok. It shows the album covers, but no visualization and browse? I know Rhythmbox have those features but I guess you can't win them all, can you? I also tried Amarok but I didn't like it. I settled for Banshee instead.

Totem movie player didn't worked for me as well. It won't read my VCD's so I had to install Mplayer. 

I didn't need two sets of audio and video players so I removed Rhythmbox and Totem in Synaptic Package Manager.

I then  opened my AppleWorks files (saved as msword documents) in Open Office. That also went well, including my AppleWorks database (saved as .csv)  that Calc managed to translate.

I also opened my favorites websites in Firefox just to see if any additional plug-ins will be required (say for apple.com). 

Lastly was the email client. I tried Evolution but I prefer Thunderbird (with Lightning extension installed). Again I didn't need two sets of email clients so I removed Evolution in Synaptic as well. 

I also tried the following applications: Scribus (kept), Comix (kept), Gimp (kept), Wine (removed, more on that later), Avidemux (kept) and Elisa (removed).

I know that there are several DVD rippers in Ubuntu but I was quite frustrated with the lack of a straightforward VCD ripper. I found a workaround in the forums and came across a terminal command that rips a .dat file and saves it automatically as .mpg in the home folder. It worked fine but if you are familiar with VCD's you know that a single movie consist of 2 to 4 discs. With the terminal command, you'll end up with very large .mpg files that you need to join to watch seamlessly and convert to a smaller format (I prefer mp4). I tried the accompanying cat command but I didn't manage to get it to work (maybe it's just me). 

I also connected my HP D2360 printer and it worked immediately.  

One thing though is when I decided to get some real work done (rip a few audio cd's) and edit a few comic books I downloaded (pdf to jpeg in GIMP) so I could view them in Comix, the pc (I hope and not the OS itself) failed me. The Ubuntu loading screen showed up fine but what should  be the log-in screen is a black and white static mess that kept flashing in and out. Still heard the "beep", though. Tried rebooting and accessing the GRUB menu but it wont respond.  

I guess that's it for the pc. I'm convinced that it's a hardware problem. As I stated, the pc was never a reliable machine anyway. All in all, the experience was good and I'm looking forward in buying a brand new Compaq Presario (the Ubuntu colors will beautifully match the laptop's exterior).

However if you guys think I did something wrong which caused the log-in to foul-up please let me know.
 
Cheers. :)

---

### Post by neurostu on 2008-03-10
Having read your post I would agree that it sounds like a hardware issue. My one piece of advise though, when you do get your laptop is to customize it SLOWLY.  Take time and really decide what things to add and what to remove.  If you do it step by step instead of one fell swoop you can save yourself a lot of pain if something breaks.

---

### Post by crjackson on 2008-03-10
Try booting form the LiveCD again and that will tell your for sure if it's hardware or software.

---

### Post by libertas on 2008-03-11
I wouldn't throw out the computer just yet, i understand that it is a hardware problem and thats just fine but my question is, is it that ubuntu is just to big for it (takes up to much RAM/ROM) so that it doesn't work properly or is it truly fried. 

Did it work fine with 98 and the like cause if it did then the thing you should do is instead of putting ubuntu (which is the equvilant to XP) on it you should instead install puppy linux. 

Puppy Linux is a reliable, fast and efficient little OS that i have grown rather fond of. it is so lightweight that it made the old OLD computer that was having issues running 98 (not enough RAM and ROM for it to work properly) run like new, in fact it is more responsive and works faster than the newer computer that runs ubuntu.

So all in all what i am trying to say is that it does not seem like a good idea to me to throw out the computer just yet, i suggest that you try putting puppy linux on it and see how that works out, im not saying that you should not get a new computer, but instead i am saying that you should not throw it out. Im sure that some use could come of it, there are always people less fortunate or if you have need of something for internet use, Word processing, Video watching etc. (all of the base things that come with ubuntu) then just have it there.

puppy linux can be found at [http://www.puppylinux.com/](http://www.puppylinux.com/) if you are interested.

---

### Post by handydan918 on 2008-03-11
The live cd suggestion is a good one. Alternatively, you might try hitting ctrl+alt+F2 and see if you get a console login...if so, login and do ```
sudo dpkg-reconfigure
```

---

### Post by steveneddy on 2008-03-11
Did you Google to determine if your hardware was supported fully in Ubuntu or Linux?

---

### Post by linuxlizard on 2008-03-11
Just wanted to say that the hardware if working and set up properly should run ubuntu just fine. I've got Kubuntu (which probably needs a little more umph than ubuntu because of kde) fiesty fawn running on my folks computer which is the same processor and less memory. It's even got beryl running the cube and plays games like legends, urban terror, and open arena just fine. It doesn't feel sluggish at all even with beryl running.

I don't have gutsy on there, but surely the hardware requirements didn't jump that much in a single release...

---

### Post by carlolovearianne on 2008-03-11
Thanks for the replies.

I don't really care much about the old beat up pc. I would like to salvage some purpose out of it, of course, but at the end of the day its the new (unpurchased) laptop that I'm a bit worried about. Will the Compaq Presario work? Though cheap, it still is good money. And if Ubuntu doesn't work in that one, what should I do? Migrate to Windows? (perish the thought)


At this point I just want to know the absolute best laptop that is Ubuntu-friendly. I'm from the Philippines and new Dell laptops are not available here. But the market is flooded with Compaq, Asus, Acer and the likes.

I (like most people, I guess) just want to get some real work done with the OS. I wouldn't mind a bit of tweaking to get something to work but reading the forums I seem to get an impression that the price to pay for being free (OS) is too much for an average person to bear.

---

### Post by scramasax on 2008-03-11
> **carlolovearianne said:**
> Thanks for the replies.

I don't really care much about the old beat up pc. I would like to salvage some purpose out of it, of course, but at the end of the day its the new (unpurchased) laptop that I'm a bit worried about. Will the Compaq Presario work? Though cheap, it still is good money. And if Ubuntu doesn't work in that one, what should I do? Migrate to Windows? (perish the thought).

Dual-boot if need be.  There doesn't have to be an either/or.

You mention Compaq.  If I google "compaq linux", I find this:

[http://www.linux-on-laptops.com/compaq.html](http://www.linux-on-laptops.com/compaq.html)

---

### Post by neurostu on 2008-03-11
Although Dell is the only manufacterer (that I know of) that sells ubuntu on its machines, you will be able to get it to run well on 99.9% of the other machines out there. Older machines also tend to work a little bit better then newer ones too....

Just find a laptop that fits your budget then post the specs here and we'll help you out.

---

### Post by carlolovearianne on 2008-03-11
Thanks for the support everyone.

Though I'm having a bit of reservation as to purchasing a laptop for Ubuntu (with the possibility that it might/might not work  hanging on my mind), I'll see what happen by next week. I'll definitely be back (but I hope in an ecstatic mood not dumbfounded).

Going back to what happened to the  beat up pc. I haven't tried running the Live CD again but do you guys think that I possibly broke the system when I removed the default apps in synaptic manager? I opted for a complete removal, which as I understand completely removes everything.

---

### Post by sports fan Matt on 2008-03-11
Id love to commend you for your construstive and Fair review..When I migrated to Linux, I was like you, asking alot of questions (in fact I still ask alot of questions , (some may be stupid) but I learn every time.  The migration to Linux is not hard--but different.  It was the best choice for me and with ime and patience and an understanding that we are all here to help, you will feel right at home.  Take tiome, learn, play with diffrent programs..ITS JUST A computer..it can be fixed..

---

### Post by carlolovearianne on 2008-03-11
Will a Presario really  be good choice for Ubuntu? Are there any processors that you guys know of that does not play wel with Ubuntu? Like AMD Sempron? I can pick up 14.1" Presario with AMD Sempron for a very good price this week's end. I just forgot what the particular model number is (V3037 I think).

Any wireless card or graphics card I should watch out for? What do you guys think?

---

### Post by handydan918 on 2008-03-11
> **carlolovearianne said:**
> Will a Presario really  be good choice for Ubuntu? Are there any processors that you guys know of that does not play wel with Ubuntu? Like AMD Sempron? I can pick up 14.1" Presario with AMD Sempron for a very good price this week's end. I just forgot what the particular model number is (V3037 I think).

Any wireless card or graphics card I should watch out for? What do you guys think?

Wireless cards-watch out for anything using a broadcom chipset. They are always a major PITA! 
Graphics- depending on your needs, and provided that you don't mind using proprietary drivers, both ATI and nvidia have fairly broad support for Linux. Before buying, positively identify the video chip being used and start googling.

---

### Post by carlolovearianne on 2008-03-11
Just a quick update. Managed to reinstall 7.10 on the beat up pc. I'm going to let it simmer down and get comfy. No Synaptic Package madness. No Updating. No nothing. Not even internet (at least for a while). Just the bare bones OS and the pre-installed softwares from the Live CD.

:)


Safe to say I somehow broke the system then? Does that mean it's not safe to completely remove default apps like Evolution, Totem etc.?

---

### Post by neurostu on 2008-03-11
No if you do it right then removing evolution isn't a problem...

Now why are you wanting to remove it? if your doing it to free up space it really isn't worth the effort. If your removing it b/c the icon bugs you, in the menu editor (right click on the ubuntu icon) and just uncheck evolution.

---

