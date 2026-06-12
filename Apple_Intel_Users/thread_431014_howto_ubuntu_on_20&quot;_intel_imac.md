---
title: "howto? ubuntu on 20&quot; intel imac"
date: 2007-05-02
forum: Apple Intel Users
---

### Post by nebhead on 2007-05-02
hi people.

just to set the scene, my friend has Intel imac 20-inch 2.16GHz Intel core 2 duo, and wishes to install ubuntu feisty. first of all, as i am helping him installing it and i have never installed Linux on a mac ever, how do you do it?
i have heard people say that you create a partition with boot-camp, and then reformat the partition and install ubuntu. is this true?
my friend tried the feisty live disc and it froze on boot and the keyboard wouldn't respond. the dapper live disc works, just not the feisty one. so all i really want is a little howto for the install and how to get drivers for the graphics card etc set up for beryl and games, is all this easy?

thanks, all help appreciated.

---

### Post by Slackpacker on 2007-05-02
I lumped all the posts & howtos I used for my dual-boot installation into [this post]("http://ubuntuforums.org/showthread.php?t=429330") (maybe I should have posted it here, oh well).  The most important one being the Macbook howto on the wiki.  Obviously things will be a bit easier Flash and codec-wise if you use the i386 version.

---

### Post by ronocdh on 2007-05-02
> **Slackpacker said:**
> I lumped all the posts & howtos I used for my dual-boot installation into [this post]("http://ubuntuforums.org/showthread.php?t=429330") (maybe I should have posted it here, oh well).  The most important one being the Macbook howto on the wiki.  Obviously things will be a bit easier Flash and codec-wise if you use the i386 version.
First of all, I don't think it's at all obvious to someone "who's never installed Linux on a Mac" that choosing the i386 build will result in fewer Flash problems. But that's a different discussion.

I suspect the Live CD you guys burned was bad. Depending on your hardware, you might not have to obtain the restricted drivers, but if you're not even getting past the boot screen, well that's tricky. I recommend grabbing the OS X (open source) app **Burn**, which you can find [here]("http://www.opensourcemac.org"). It automatically verifies the integrity of the disc after burning.

Good luck, please post back with any further issues.

---

### Post by Gen2ly on 2007-05-02
Yeah, I like Burn too.  I always used it for data, wasn't aware it could do ISOs.

---

### Post by ronocdh on 2007-05-02
> **Dirk.R.Gently said:**
> Yeah, I like Burn too.  I always used it for data, wasn't aware it could do ISOs.
First time I burned an ISO it just added the image onto the CD as a file. =) Now I just use cmd-O once Burn starts and then I select the image file. Works like a charm.

---

### Post by ZeldaFreak on 2007-05-05
Thank you for your help but I know for a fact that the Feisty disc I burned works as I tried it on my PC (AMD64 processor).

I have ordered some Feisty discs from Ubuntu so I will try them and see if they work.
(I'm nebheads friend btw..)

---

### Post by ronocdh on 2007-05-05
> **ZeldaFreak said:**
> Thank you for your help but I know for a fact that the Feisty disc I burned works as I tried it on my PC (AMD64 processor).

I have ordered some Feisty discs from Ubuntu so I will try them and see if they work.
(I'm nebheads friend btw..)
Not to be belligerent, but it is very possible you're experiencing decay of recordable media; prices are so low on CD-Rs for a reason! I reiterate that I think one should always use a program like **Burn** when writing ISOs and also make sure to verify the checksum on the main screen of the Live CD menu. (That is, is you get that far! ;))

---

### Post by nebhead on 2007-05-09
Thanks for help people, we will attempt to install with your tips and help this weekend.

---

