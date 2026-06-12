---
title: "Anyone get DVD Shrink to work in Ubuntu Feisty 7.04?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-06-05
I can't get shrink to open up when installed under wine. I have followed mrbass.org tutorial & also the dvd shrink wiki, & I am still not having any luck.

It is installed under wine, & shows up there, as well as DVDD, which does work okay. It is just shrink that won't open when I try to use it...

Any help?

---

### Post by bishop1073 on 2007-06-05
I ran into similar issues. Sometimes I could get it to work and sometimes not. Most of the time, if I did get it to work, it wouldn't be able to bypass the copy protection to backup the disk. Because of that, I have unfortunately gone the route of dual booting my system with XP. Not I use Ripit4me, DVD Decrypter and DVD Shrink and have never had a bad burn. 

I would love to find an open source / GPL app for linux that would be able to do exactly what Ripit4me, DVD Decrypter and DVD Shrink can do. No luck so far.

---

### Post by discmaster on 2007-06-05
Hi bishop1073,

Thanks for the info. I have used the same as you successfully with xp. After hitting wall after wall with issues like this & also with audio editing issues (I have other threads on that subject), it looks like I may be heading back in the direction of windows again.

I need a stable, workable system, windows seems to provide that, unfortunately linux doesn't seem to be there yet...at least not for me.

I would like to stay with ubuntu, but it's all broken... :(

---

### Post by aeiah on 2007-06-05
is there any reason why you must stick with dvdshrink?

---

### Post by discmaster on 2007-06-05
Not really, I guess; I know there is k9copy, but I don't know if that provides the same flexibility as shrink does. I really only need it for compression, adding still pics., removing audio streams, etc.

Does k9copy do that, or what would you suggest?

---

### Post by Eddie Wilson on 2007-06-05
The bad thing about this problem is that there are no native linux apps. that will that will decode the latest movies so that you can make backup copies of what you own. K9copy may do everything that you need tho.
Eddie

---

### Post by jaw1959 on 2007-06-05
Try using xDVDShrink.  You can install it with Automatix if you feel ok about using Automatix.  I'm not sure how you would use it for inserting still pics, but it seems to backup DVDs just as well as DVDshrink did for me when I ran windows.

---

### Post by kelvin spratt on 2007-06-05
xdvd shrink is a clone of dvd shink the interface is near idendical if thats any help.

---

### Post by bishop1073 on 2007-06-05
I tried xDVDShrink and it worked some of the time but I still ran into issues with decoding.  DVDShrink (Linux and  Windows based)  is not able to handle the latest and greatest movies. The only one that I have found reliable is  Ripit4me, DVD decrypter and DVD Shrink together on Windows. With all 3 doing their part in one process (Ripit4me merges into DVD Decrypter which in turn merges into DVDShrink) with minimal interaction (a total of 3-4 clicks) I never get a bad burn or a an unburnable disk. 

Hopefully, someone will be able to come up with the Linux equivilant to Ripit4me, DVD decrypter and DVD Shrink. with that and working out the bug I have with MythTV, I will be able to drop Windows completely

---

### Post by discmaster on 2007-06-05
> Try using xDVDShrink. You can install it with Automatix if you feel ok about using Automatix. Thanks, but I think I'll pass on that...  I've read enough threads in regards to Automatix, I don't want any new issues to work out...

> Hopefully, someone will be able to come up with the Linux equivilant to Ripit4me, DVD decrypter and DVD Shrink.  Wishful thinking...I would like that as well...but unfortunately, I may be forced back to windows in the end anyway, due to this issue & also can't get audio editors to work properly either... :(

---

### Post by Kuoi on 2007-06-05
I should look in the options if you missed a setting in Wine .
type in terminal "winecfg" ( without quotes )

Other from that , I should reinstall DvdShrink , because I've installed it using the same guide , and it works like a charm here.

And imo you can't compare XdvdShrink and DVDShrink , but just my opinion.
There are just some settings in DVDShrink that makes it "most wanted" .

Kuoi

---

### Post by discmaster on 2007-06-05
Hi Kuoi,

Thanks for the reply - I have went thru the settings quite a few times, & also reinstalled a few times...

Believe me, I have done everything to get this thing going...I just don't know what else to try with it. If I can't get it working by following the guides, I just don't know how to fix it any other way...

---

### Post by scott_evil on 2007-06-05
I had the same problem and I finally fixed it. This worked for me, so no guarantees.

I went to [How To Wine](http://doc.gwos.org/index.php/HowToWine) and followed the instructions to Downgrade Wine.

First I downloaded the Edgy wine package for [build 0.9.34](http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb)

sudo aptitude remove wine

cd /where/downloaded/package/lives

sudo dpkg -i wine_0.9.34~winehq0~ubuntu~6.10-1_i386.deb

That's It! It works!

---

### Post by ramjet_1953 on 2007-06-05
k9 copy is fully featured and best of all, its' compression algorithms provide a DVD5 copy that is indistinguishable from the DVD9.

I have tried other packages, but they have noticible pixelisation.

ps. It is best to just get k9copy to make the iso and burn it using k3b, or GnomeBaker.

Regards,
Roger :cool:

---

### Post by mgmiller on 2007-06-06
I was also having problems running DVD Shrink in Feisty and found it is a known bug and major regression in wine starting at version 0.9.35.  I fixed it by disabling the wine repos in synaptic and unistalling wine.  I then reinstalled wine version 0.9.33 from the Ubuntu repositories and it works fine again.  Make sure that you are telling wine to run DVD Shrink as windows NT4.  I have good luck using a combination of DVD Decrypter and DVD shrink in wine.  I have also tried dvd95, k9copy and xdvd and they all work as well as DVD Shrink, but often produce a finished movie that will only play on my newer DVD player, not my older one.  DVD shrink always produces movies I can play anywhere.

---

### Post by lazerous on 2007-06-06
I've been running both dvd shrink and dvd decrypter under wine.  I followed Mr. Bass' directions and got it to work.  

I typically just make sure that if I'm backing up anything, I rip it first with decrypter before throwing it into dvd shrink.  That should get rid of some of the encrypted disc problems.

[Laz]

---

### Post by wild77 on 2007-06-08
I have been testing this guide on Ubuntu Feisty 7.04 and it seems to work with only a couple of small issues. Now that Ripit4Me is no longer being updated, I have also been working on getting DVDfab HDDecrypter working with this set-up. No luck so far the program installs and opens ok, but will not detect the drive. I am always looking for testers or input from others who have gotten this to work.

[http://forum.doom9.org/showthread.php?p=948220#post948220](http://forum.doom9.org/showthread.php?p=948220#post948220)

Programs running under Wine

DVD Decrypter
Ripit4Me
FixVTS
DVD Shrink
ImgBurn
VobBlanker
PgcEdit
DVD Rebuilder & Cinema Craft Encoder

I am going back to Edgy 6.10 until they can fix Feisty, There are several problems on my system including freezing at start-up and DVD drive not being seen or auto mounted. Feisty seems very BUGGY where as Edgy just WORKS!

My latest desktop with Edgy 6.10
[IMG]http://www.geocities.com/tyedye776967/Ripit4Me.png[/IMG]

---

### Post by discmaster on 2007-06-08
Hi wild77,

Thanks for the info. Fiesty is my first attempt at linux, & after 3 mo. or so of fighting it, I am pretty much ready to go back to windows where everything works. Your list of programs running under wine is impressive, however, my experiences have been very poor.

So far, I have only gotten DVDD to work properly; on the audio editing end of things, not much works there either...have you tried Goldwave under wine, by any chance?

---

### Post by Drakkor on 2007-06-08
nevermind,lol

---

### Post by mc4man on 2007-06-11
I've found that if you  copy Quartz.dll ver. 6.3.1.881 to sys.32 and setting to native shrink will start working again in the latest ver. of wine that comes with 7.04 (available from ms site)

---

### Post by marpstar on 2007-06-15
I too had this problem and fixed it by downgrading to 0.9.33.  No problems since.  I know that 0.9.39 came out today, but I haven't tried it yet.  I'll try it out later...

---

