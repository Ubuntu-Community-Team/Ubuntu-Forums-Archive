---
title: "i think i want to upgrade to 8.04"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by divindavid on 2008-02-21
i want to upgrade to ubuntu 8.04 because i have herd good things about it for old computers (correct me if i am wrong). i have a IBM t22 with a P3 processor at 996MHz and 256mb of ram.but i dont want to format my drive to install it so is there a way to upgrade like i did when i upgraded to 7.10 i just hit a few buttons and let it sit for a while. or if i use the alter. version of the ubuntu 8.04 CD is there a upgrade option there..


thank you

david.

---

### Post by spiderbatdad on 2008-02-21
I don't believe 8.04 is designed to run on 256MB of RAM. 1GB+ would be great.

---

### Post by icechen1 on 2008-02-21
It might work but maybe not compiz,anyway
in a terminal do
sudo update-manager -d

---

### Post by Iowan on 2008-02-21
I didn't see 8.04 as a download option, but [here]("http://ubuntuforums.org/showthread.php?t=600644") is some useful information.

---

### Post by oilchangeguy on 2008-02-21
> **divindavid said:**
> i want to upgrade to ubuntu 8.04 because i have herd good things about it for old computers (correct me if i am wrong). i have a IBM t22 with a P3 processor at 996MHz and 256mb of ram.but i dont want to format my drive to install it so is there a way to upgrade like i did when i upgraded to 7.10 i just hit a few buttons and let it sit for a while. or if i use the alter. version of the ubuntu 8.04 CD is there a upgrade option there..


thank you

david.

8.04 is still in beta, so if nothing else, there will be problems that go along with using beta software. and as the previous poster stated, your machine probably does not have the power to properly run 8.04. even if you have "herd" good things about it.(i hear the mooing of cows). i've not HEARD anything yet. but stay away from any beta software.

---

### Post by sports fan Matt on 2008-02-21
I agree--plus even though its getting closer..it "aint ready for primetime just yet".  I certainly do not think it going to run atm with 256 MB, the release is still more then a month away and hopefully by then it will run..(lest we forget, 256 is the BARE minimum) for even Ubuntu to run on.

Another thing to consider: If it ain't broke, why in the world risk it?  I wouldn't and plan on waiting maybe even after the update to install

---

### Post by divindavid on 2008-02-21
ok.......
i am running 7.10 verry fast for only 256mb of ram.
well i guess i will not install. 
i will when i get my asus Eee PC boy will that be great.

---

### Post by divindavid on 2008-02-21
and oilchangeguy stfu when you were 13 could you do all of this plus spell things right (ok maby the spelling) i just bought a huge cheese roll.

---

### Post by dcstar on 2008-02-21
> **divindavid said:**
> i want to upgrade to ubuntu 8.04 because i have herd good things about it for old computers (correct me if i am wrong).
.........

Since most new releases have more and more "features" that require higher specced hardware to adequately perform on, I seriously doubt that premise.

8.04 currently uses the 2.6.24 kernel, and I don't see that as any slimmer that the current 2.6.22 kernel (the generic image package is 80.8GB versus 74.4 for 7.10) - some of this has to load into the memory of your system, and it ain't less in the newer version.

If you want a more suitable Ubuntu for old hardware, the 6.06 LTS release may well be a better option.

---

### Post by BLTicklemonster on 2008-02-21
> **divindavid said:**
> and oilchangeguy stfu when you were 13 could you do all of this plus spell things right (ok maby the spelling) i just bought a huge cheese roll.

lmao


:popcorn:

---

### Post by bodhi.zazen on 2008-02-22
go for it, but be prepared for bugs and it would be nice if you are willing to file bug reports as well.

IMO 8.04 is fine for testing / development but not yet ready for prime time.

---

### Post by divindavid on 2008-02-22
thank you for all of your help

---

### Post by seventhc on 2008-02-22
check here.
[http://www.ubuntu.com/testing/](http://www.ubuntu.com/testing/)

---

### Post by spacefreak86 on 2008-02-22
Quick Question. When the time does come for everyone to upgrade to 8.04, is there an option to transfer over files and configurations without having to wipe the partition (or hard drive, depending on how you set it up), or do you have to do a clean install and just back everything up on CD?

---

### Post by Pandemic187 on 2008-02-22
> **spacefreak86 said:**
> Quick Question. When the time does come for everyone to upgrade to 8.04, is there an option to transfer over files and configurations without having to wipe the partition (or hard drive, depending on how you set it up), or do you have to do a clean install and just back everything up on CD?
Yep. I know that one way of doing it would be to edit your /etc/apt/sources.list file so that every instance of whichever release of Ubuntu you're currently using would be changed to Hardy. So if you're running Gusty, for example, you would change every instance of *Gusty* to *Hardy*. I'm not sure if that's the best way to do it, but it certainly can be done.

---

### Post by seventhc on 2008-02-22
I think you can just click on the *Upgrade* button. It will show up at the top of the box that opens for *Updates*.
I'm pretty sure if you do it that way, your settings remain, but I can't make any guarantees. In any system change a good backup is desirable and a good habit to be in.

---

### Post by bodhi.zazen on 2008-02-22
The plan is to enable the option to upgrade, both 7.10 -> 8.04 as well as LTS -> LTS (direct LTS upgrade).

We will see how it goes.

---

### Post by Paqman on 2008-02-22
> **oilchangeguy said:**
> 8.04 is still in beta

It's not even that far along, actually. The beta is scheduled for release 22 March.

Once the final version is released (24 April) you'll be able to do an in-place upgrade if you so desire. A good tip to make this go smoothly is to disable any extra repos while upgrading. I've upgraded Ubuntu a couple of times without any problems at all. Some people have ended up with borken systems though, so back up anything precious beforehand.

---

### Post by kooolrock on 2008-02-22
> **spiderbatdad said:**
> I don't believe 8.04 is designed to run on 256MB of RAM. 1GB+ would be great.
+1

---

### Post by kooolrock on 2008-02-22
> **divindavid said:**
> i want to upgrade to ubuntu 8.04 because i have herd good things about it for old computers (correct me if i am wrong). i have a IBM t22 with a P3 processor at 996MHz and 256mb of ram.but i dont want to format my drive to install it so is there a way to upgrade like i did when i upgraded to 7.10 i just hit a few buttons and let it sit for a while. or if i use the alter. version of the ubuntu 8.04 CD is there a upgrade option there..


thank you

david.
dear buddy,
u mentioned that u [COLOR="Red"]dont want to format ur drive to install 8.04 [/COLOR]. if that is the case, DON'T SHIFT TO 8.04. the reason is because it is meant for developers/ those are ready to take a "risk". since u don't wanna take a risk by having to foramt in case of an error, stay away from it for a while.

---

### Post by bodhi.zazen on 2008-02-22
I do not know about 8.04, but 7.10 :

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

> Minimum requirements

      300 MHz x86 processor

      64 MB of system memory (RAM)

      At least 2 GB of disk space (for full installation and swap space)

      VGA graphics card capable of 640x480 resolution

      CD-ROM drive

If your system has less than 192 MB of system memory, use the Alternate Installation CD. 

This is likely with no X (gui)

And :

> Recommended minimum requirements

      500 MHz x86 processor

      192 MB of system memory (RAM)

      8 GB of disk space

      Graphics card capable of 1024x768 resolution

      Sound card

      A network or Internet connection

Of course you can optimize for low RAM:

	[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

But 1 Gb sounds high for the "minimum" RAM requirements ;)

---

### Post by spacefreak86 on 2008-02-22
I know in windows one can simply go to regedit and then click on backup registry, and then just copy the files you want on some removable media (or another hard drive if you have one). Is there an equivalent to regedit (registry editor) in Ubuntu to back things up?

Also is there a way to back up the repositories, or will we have to d/l all of them again?

---

### Post by ronmarley1 on 2008-02-22
> **oilchangeguy said:**
> 8.04 is still in beta, so if nothing else, there will be problems that go along with using beta software. and as the previous poster stated, your machine probably does not have the power to properly run 8.04. even if you have "herd" good things about it.(i hear the mooing of cows). i've not HEARD anything yet. but stay away from any beta software.

Actually, still Alpha.  In any event, as the poster suggests, it's not ready for production machines.  On the flip side, I've loaded the Beta versions of Ubuntu going back to Dapper and things ran fine for me.  I may be an exception, but not the rule.

Lastly, oilchangeguy, if you are going to correct someone's spelling, try applying a few grammar rules to yourself.  Most sentences begin with a capital letter.

---

### Post by Paqman on 2008-02-23
> **spacefreak86 said:**
> 
Also is there a way to back up the repositories, or will we have to d/l all of them again?

If you reinstall, you'll have to download all your packages again. However, you can [do it automatically](http://ubuntuforums.org/showthread.php?t=261366).

---

