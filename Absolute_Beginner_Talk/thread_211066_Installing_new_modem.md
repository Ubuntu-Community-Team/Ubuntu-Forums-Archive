---
title: "Installing new modem"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by roxcyn on 2006-07-07
I installed Ubuntu on my older Sony computer because I don't like Windows ME (that's what came with the computer).  I am liking this operation system better because it seems faster.  However, I am having trouble with installing the modem.  I have the scanModem on there, but I am totally confused with all the jargon it includes in the text files after I ran the scan.  However, I know the exact model of my modems (I have two modems installed on the Sony computer):

[http://www.bestdata.com/index.php?file=c-allproddesc&iProductId=16162](http://www.bestdata.com/index.php?file=c-allproddesc&iProductId=16162)
Model: 56HP92-PCT
P/N: 35041

My other modem is a Lucent 1648/V.90 compatiable (that's the modem that came with the Sony computer, model number: PCV-J150)

So, I would appreciate the help.  :mrgreen:

---

### Post by Handyman's Special on 2006-07-07
Hello,

It has taken me a week to figure out that the WinModems do not work with Linux. At least, not without much, much work and trouble. We happened to have an old Hayes external modem laying around the house, so I hooked it up. Connected on the first try. It did take just a touch of trying until I got the correct setting for the com port. (Excuse me if I am still using Windows terms, I am a beginner here.)

With the weekend coming up, you will probably be able to pick one of those external modems at a flea market for just a little bit of money.

There was a very good link posted here yesterday, I suggest you read through it, too.
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)
This excellent page is what brought me to realize I was batting my head against a tree for nothing. If the modem software was written for Windows, that is where it works.

I tried the old Hayes modem in Windows and it flew, in Kanotix and it crept, but straight off the Ubuntu Live-CD it was as fast as it was in Windows.

I think I am going to love Linux.

Cheers,
Handyman's Special

---

### Post by roxcyn on 2006-07-07
Thanks Handyman's special.  Yea, that is where I went.  It appears complex at least to me.  I have never used Linux software, so I don't understand some of it.  

However, I don't have any flea markets around my city.  We used to have a few, but they closed down.  However, could you tell me if I could use those two modems?  I am attaching the scan from that software.  Or should I give up and buy a Linux compatible modem?  :-k

---

### Post by Handyman's Special on 2006-07-07
Hi roxcyn,

Good grief! Honest, I tried to read that but it looks like Greek to me.

I haven't searched the web net I bet an external modem can be found. Aren't there any computer shops around you. Some of them have odds and ends laying around that you can pick up for a decent price. Call around and see what you can come up with.

This is my first day being connected on Linux, so things are not to clear for me yet.

After that stuff M$ did with the Genuine Advantage I am happy to be seeing them in my rearview window.

Keep me posted on how you make out.
Cheers,
Handyman's Special

---

### Post by teyster2 on 2006-07-07
Ok, I know this will probably get me in trouble, but I have installed many internal modems, some easier than others.  I purchase USR hardware type from Ebay work well are not autodetected and you must put in the proper comport usually ttys4 or ttys14.
Also, I use conexant chipset modems.  The drivers may come with the modem out of the box or you can download from linuxant.org.  Their is an additional $20 charge for a key code to make the modem work at 56.6.
I have used the intel ham type 536ep, but not with Ubuntu and at some difficulty, but it can be done.  
Don't hate me if you have problems, I have installed these modems not only on my computer, but my friends are coming around to Ubuntu at my insistence and I've had to set theirs up many times.  No hi-speed available to us out here except Hughes or Wildblue satellite.  Anyway, hope this helped.

---

### Post by batholith on 2006-07-07
I purchased a lucent chipset modem from walmart for something like $15...it was a bit of a trick getting it set up but check out:

[http://linmodems.org/]("http://linmodems.org/")

They have a pretty good how-to there...I wasn't able to get the latest version of some the "drivers" to work, but the older more generic version (sorry I can't remember which) worked great.  I'm afraid with these types of modems it's a bit of trial and error...

---

### Post by djheadley on 2006-07-08
An alternative to flea-markets would be Goodwill or any type of thrift store.

---

### Post by editrix on 2006-07-08
> **djheadley said:**
> An alternative to flea-markets would be Goodwill or any type of thrift store.

Yes. And your nearest LUG (Linux Users Group). These are all over the world, and can be a goldmine of information (and cheap, used hardware). Just google your (nearest) city and "Linux Users Group."

---

