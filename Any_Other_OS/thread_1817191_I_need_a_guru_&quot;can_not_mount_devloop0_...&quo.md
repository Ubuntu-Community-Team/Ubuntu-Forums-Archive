---
title: "I need a guru: &quot;can not mount /dev/loop0 ...&quot; same on CD &amp; USB, md5 is ok"
date: 2011-08-03
forum: Any Other OS
---

### Post by aburgess on 2011-08-03
So I'm trying to put Mint 11 LXDE (based on Ubuntu 11.04) on my brother's Dell Inspiron 1525. Every time I try to boot up from the installation media I get "Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs."

The md5sum is good. The problem is replicated using a CD, a DVD, and USB key, all of which boot up fine on my Asus netbook.

He currently has Ubuntu 7.04 installed, so I know this worked on his machine once. Any guesses, anybody?

---

### Post by Kromgol on 2011-08-03
The problem is most likely a corrupt ISO that you've burned/extracted. Try downloading another one and then check the md5sum of both.

---

### Post by aburgess on 2011-08-03
As I've said, the md5sum is good, it's replicated on multiple formats, and the media boots on other machines. But I guess my next step is to try maybe a 10.04 iso or something.

---

### Post by 23dornot23d on 2011-08-03
I have already done this once and there were a couple of problems - but they were soon resolved ......

where did you download the ISO for 11 from ....... if you give a link to it ..... 

I will see tonight if I can get the same problems to re-occur and hopefully give a fix to them.

Check my link I keep a record of what I do as I go along in my messages in _*[[COLOR=Red]**my home page here at Ubuntu Forums**[/COLOR]]("http://ubuntuforums.org/member.php?u=953253")*_ ......

but I used the Mint Lxde 10 to start from ....... ( guru mmmmm not me - but I will try to help if I can )

---

### Post by aburgess on 2011-08-03
[http://mirror.csclub.uwaterloo.ca/linuxmint/testing/linuxmint-11-lxde-32bit-rc2.iso](http://mirror.csclub.uwaterloo.ca/linuxmint/testing/linuxmint-11-lxde-32bit-rc2.iso)

It's one of the mirrors on this page: [http://blog.linuxmint.com/?p=1793](http://blog.linuxmint.com/?p=1793)

---

### Post by 23dornot23d on 2011-08-03
Ok well it should be the same ISO ..... as the France one .... so 

I have decided to load the one from France as its going to be twice as fast
a download for me to the other link ...... France: [linuxmint-fr.org]("http://mirror.linuxmint-fr.net/linuxmint.com/testing/linuxmint-11-lxde-32bit-rc2.iso")
Md5 sum: f1c310e709c3236a84a7afa4a44f696d

Ok I will let you know how it goes ...... downloading now .... 1mb/sec 7 mins to go ... ;)

Got to make room for it on a hard drive now .....so might as well put it in my main one .

First things first .... How did you burn your CD .... what application did you use .... ?

I always burn my disks with K3b ..... 
( just my choice ... may not make any difference but its a variable )

doing  this at 10x default settings ....

Ok booted up and in the desktop ,,,,, no problems yet ....


Well there is nothing I can see wrong with the French one ....... but just to check that there is not a difference
on the downloads ...... 

I will download from the same place you did .... 20 mins remaining
and as you say the Md5 sum: f1c310e709c3236a84a7afa4a44f696d    - is correct ....

Did you use [Brasero]("http://www.google.com/search?client=ubuntu&channel=fs&q=Brasero&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&hs=foo&channel=fs&source=hp&q=Brasero+problems&pbx=1&oq=Brasero+problems&aq=f&aqi=g1g-v4&aql=&gs_sm=e&gs_upl=4497l7575l0l7813l9l9l0l4l4l0l325l1256l0.1.3.1l5l0&bav=on.2,or.r_gc.r_pw.&fp=7caaed5eb0414d97&biw=1157&bih=534")

But as you say it works on yours ok ...... so it could be the CD/DVD reader in your brothers machine that
is not picking up the data ..... ( but you say its not working from flash either ) .....

I am at the moment using the French download and am in the process of installing it ....... so that one is definitely ok ...

I would be looking at two things ..... incompatibility between swapping a CD burnt on your machine to his .....
( as tolerances could mean they do not work together ,,,, I have had this only once before though )
but with the Flash not working also ..... it points to a problem on your brothers machine maybe

> 
He currently has Ubuntu 7.04 installed, so I know this worked on his machine once. Any guesses, anybody?
So your brothers machine and are the [URL="http://en.wikipedia.org/wiki/Dell_Inspiron_1525"]specifications good enough
to run the distro[/URL]

I am thinking more that the CD drive may be worn out or a different tolerance on how
well it reads the burnt disks from another machine 
( and possibly with the older technology is not reading the disc as well as it should - who knows ) ....

But my bets are on something to do with the hardware or the burning of the CD ,,,,, 

The Flash drive can you  use it at all to see the files on it ...... when its inserted in the machine
from a desktop environment ...... 


But if it fails on your brothers machine again ..... then it may be the CD/DVD drive ......
(has his CD/DVD player burner had problems before with other disks)
and possibly the flash reader would only read the smaller 1 to 2 Gig .... flash cards back then .



Best I can say is try it one more time from the French download ..... site ..... 
Try slower speeds at burning ,,,,,, if you believe his machine is ok 
Also use K3B to burn the CD 

Because the actual ISO is good from there and the MD5 is the same for both downloads
so I doubt very much there is a difference between the sites ...

This is it installed and running from that site - using the France download point ....

[IMG]http://img820.imageshack.us/img820/6606/firstly.jpg[/IMG]

Upgraded it to Gnome-Shell

[IMG]http://img171.imageshack.us/img171/2509/lxdes.jpg[/IMG]

---

### Post by aburgess on 2011-08-04
Thanks for your thoughts. I think the CD drive and USB ports have been working normally for most purposes. I was able to get to a minty-looking page with options for "LiveCD," "Compatibility Mode," etc, it was after I chose to any of those options that it failed. 

I'm going to try some other iso's (10.04, 8.04, alternate CD), just to see if anything works.

Great screenshots, I love the LXDE desktop and I love what the Mint guys do with it:)

---

### Post by 23dornot23d on 2011-08-04
Ok well I hope you have success - if his still runs ok download and burn the disk on his machine ......

Just makes compatibility 100% then for the CD .....

Ok all for now ..... and I agree Mint themes are good ..... 

They even made them match the Nvidia Logo colors  .... ok all for now have fun ... ;)

---

