---
title: "can't install ubuntu7.10"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by 3076 on 2008-02-13
[SIZE="4"][FONT="Arial Black"]Having  downloaded ubuntu7.10 , having burned it on the cd , once having started all is regular , chooses the first entry(start or install ubuntu) , enters a interface: And then  course retinue swing, later the course strip  are filled .a small "X"-like thing has appeared, it changed to a loading circle , then entered the interface (do not have a wallpaper ) in yellowish brown.the mouse appears on [COLOR="Red"]BUT[/COLOR], it has been 20 minutes but there is not reaction. can you help me.[/FONT][/SIZE]

---

### Post by emarkd on 2008-02-13
Are you saying that there's nothing on the screen?  It's just a solid color with a mouse pointer?  If so:

1.  Did you verify the .iso file after you downloaded it?  You can get the md5 hash from Ubuntu.com if you didn't.

2. Did you burn the disk at a very low speed?  Most CD burners allow a bit of error when they're burning in order to achieve high speeds.  That may be fine for audio but it's bad news for a Live CD.

If you'd like to read more on this, see [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by overdrank on 2008-02-13
> **3076 said:**
> [SIZE="4"][FONT="Arial Black"]Having  downloaded ubuntu7.10 , having burned it on the cd , once having started all is regular , chooses the first entry(start or install ubuntu) , enters a interface: And then  course retinue swing, later the course strip  are filled .a small "X"-like thing has appeared, it changed to a loading circle , then entered the interface (do not have a wallpaper ) in yellowish brown.the mouse appears on [COLOR="Red"]BUT[/COLOR], it has been 20 minutes but there is not reaction. can you help me.[/FONT][/SIZE]

HI and welcome, thanks for the big print ( my eyes are bad ) but it is not needed. Could you tell us some specs on the system? and did you check the cd for errors and you may look at this a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by 3076 on 2008-02-13
sorry i am forigner and i don't quite understand" *some specs*"you said do you mean this
dell pentium 4, 40GB ,256M memory?

---

### Post by emarkd on 2008-02-13
Did you check out our previous posts about verifying your disk?

If this is a hardware issue, it's usually related to video, so what type of video card do you have?

---

### Post by overdrank on 2008-02-13
> **3076 said:**
> sorry i am forigner and i don't quite understand" *some specs*"you said do you mean this
dell pentium 4, 40GB ,256M memory?

HI and yes, forgive my abbreviations and the graphics card?
**Edit and emarkd has beaten me to it lol but also if the graphics is onboard it will be sharing that memory that is at the minimum requirements. **

---

### Post by 3076 on 2008-02-13
one thing i did is that i use alcohol120% to burn the cd image to the dvd ,is there some bad effect?

---

### Post by 3076 on 2008-02-13
it is Intel(R) 82865G Graphics Controller

---

### Post by overdrank on 2008-02-13
> **3076 said:**
> it is Intel(R) 82865G Graphics Controller

HI and I would suggest checking the cd for errors on the start or install screen. And also see my edit to my previous post on the onboard graphics sharing the memory.

---

### Post by 3076 on 2008-02-13
sorry i don't know what is to "verify my disk"

---

### Post by 3076 on 2008-02-13
it is *iso absolutely

---

### Post by emarkd on 2008-02-13
> **3076 said:**
> sorry i don't know what is to "verify my disk"

See [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso).  That will walk you through it.

---

### Post by overdrank on 2008-02-13
> **3076 said:**
> it is *iso absolutely

When you boot the cd and see the screen with start and install there should be a option with check cd for errors.

---

### Post by 3076 on 2008-02-13
i check ed but there is nothing wrong

---

### Post by overdrank on 2008-02-13
> **3076 said:**
> i check ed but there is nothing wrong

Ok if the cd checks out then I believe it is not running do to the low memory being shared with the graphics.
**If you are just wanting to install then you can use the alternate cd found here**
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

---

### Post by emarkd on 2008-02-13
> **overdrank said:**
> Ok if the cd checks out then I believe it is not running do to the low memory being shared with the graphics.
**If you are just wanting to install then you can use the alternate cd found here**
[http://releases.ubuntu.com/releases/7.10/](http://releases.ubuntu.com/releases/7.10/)

I agree.  I searched that video card and there's no reason why it won't work, except that it shares main memory, reducing the amount actually available.  If you really want to try Ubuntu, either install it from the alternate CD as mentioned above, and be prepared to fight a few fights to get your system lean enough to run properly, or maybe try one of the lighter-weight variants, like Xubuntu for FluxBuntu.

Or [buy more RAM]("http://www.newegg.com").  It's gotten quite cheap...

---

### Post by 3076 on 2008-02-13
ok i will try

---

### Post by 3076 on 2008-02-13
thank you overdrank and emarkd

---

### Post by asmoore82 on 2008-02-13
> **emarkd said:**
> 2. Did you burn the disk at a very low speed?  **Most CD burners allow a bit of error when they're burning in order to achieve high speeds.**  That may be fine for audio but it's bad news for a Live CD.
this ``emphasis added'' part here is nonsense. I switched to Linux quite some years ago and have
since burned a lot of CD's at *full speed and verified them* afterwards with no problems whatsoever.

That having been said, though, I do recommend burning at slow speed *on Windows*.

---

### Post by emarkd on 2008-02-13
Maybe "allow" was a bad choice of words, but it's true that errors are more likely to occur at higher speed, else there would be no benefit to burning at lower speeds.

---

### Post by jcitguy78 on 2008-02-13
Is your machine running Ubuntu only or are you trying to dual boot it?

---

### Post by northern lights on 2008-02-14
> **jcitguy78 said:**
> Is your machine running Ubuntu only or are you trying to dual boot it?

What difference would that make? He could be runnin' OS X or Samba for all I care - the Live CD should work no matter what...

@3076: 256 megs of memory really don't cost the world nowadays, but if u're not sure whether that'd fix anything and don't wanna waste cash, can't u borrow a ram stick from some buddy for a few hours to try?! Further, if that's not an option for ya, check out the following two links, those are two rather lean and less hardware demanding distros:

Fluxbuntu (stripped Ubuntu, own window manager - neither K or GNOME Desktop Environments): [http://fluxbuntu.org/js.html#]("http://fluxbuntu.org/js.html#")
Puppy Linux (recently created by this retired Aussie professor, very small, very resource efficient): [http://www.puppylinux.org/user/viewpage.php?page_id=3]("http://www.puppylinux.org/user/viewpage.php?page_id=3")

---

### Post by tjwoosta on 2008-02-14
I am having the same problem trying to install ubuntu on a dell  with 256 mb ram and the same intel graphics controler I currently have xp and it is a little sluggish i thought ubuntu would be better but it does the same thing as mentioned above.

---

### Post by 3076 on 2008-02-14
i also running winXP pro indeed

---

