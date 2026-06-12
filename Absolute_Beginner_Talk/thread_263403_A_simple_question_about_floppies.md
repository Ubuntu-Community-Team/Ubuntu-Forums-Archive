---
title: "A simple question about floppies"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-09-23
Hello everyone,
I'm not very familiar with floppies and I want to install one of the GNU/Linux distros on an old Dell box (64 RAM - 4.1G HD) which is totally empty because I accidently deleted the Windows 98 SE that was in it.

I can't change the boot order and it is set on Boot Floppy. I would like to know what the maximum capacity in MB on one floppy is? I was thinking of DamnSmallLinux or Puppy which I'd download/burn to CD using another computer. From there, I'd create a floppy.

Thanks for reading.

---

### Post by MWAAAHAAA on 2006-09-23
Wikipedia is a great source of information. Hope this helps. [http://en.wikipedia.org/wiki/Floppy_disk](http://en.wikipedia.org/wiki/Floppy_disk)

---

### Post by ron999 on 2006-09-23
Hi xyz

They're usually 1.44MB capacity.

---

### Post by xyz on 2006-09-23
Thanks for the help, MWAAAHAAA  and ron999!
Judging from what I've been reading, I'm not going to be able to do it that way! Too bad!

---

### Post by junglepeanut on 2006-09-23
Create boot floppy, create boot cd from DSL or others (DSL will get many hits in google for boot floppy with how to make one.) 

Before you do that though, as I went through the whole process, and it seemed after about thirty floppies I had laying around I finally found one that would burn fully. I then was doing a search and found the way to change my pc's boot order. I.e I was under the impression it was unchangeable and trust me I really tried. But in the end it turned out there was a special key sequence that had to be entered before the option would be allowed. Something like ctrl then hold delete for along time.

Just look online for your motherboard and hopefully...it may not have the option so otherwise hope you have more than one floppy at least. I may have the floppy laying around still if you can't find any of the files. I can send em to you, but you will still have to make it bootable.

Jp

---

### Post by bri_06 on 2006-09-23
Floppies are like... so 90s. :rolleyes:

---

### Post by xyz on 2006-09-23
> **junglepeanut said:**
> Create boot floppy, create boot cd from DSL or others (DSL will get many hits in google for boot floppy with how to make one.) 

Before you do that though, as I went through the whole process, and it seemed after about thirty floppies I had laying around I finally found one that would burn fully. I then was doing a search and found the way to change my pc's boot order. I.e I was under the impression it was unchangeable and trust me I really tried. But in the end it turned out there was a special key sequence that had to be entered before the option would be allowed. Something like ctrl then hold delete for along time.

Just look online for your motherboard and hopefully...it may not have the option so otherwise hope you have more than one floppy at least. I may have the floppy laying around still if you can't find any of the files. I can send em to you, but you will still have to make it bootable.


Thanks junglepeanut...also for suggesting to send them to me. I'll let you know. That would be great! Where do you live...if I'm being indiscrete,forget it.

I will go and search the way you advised and we'll see!

bri_06...I really don't understand why you couldn't refrain from making that comment. It is just so...I won't say it. Good day to you anyways!

---

### Post by ron999 on 2006-09-23
Hi xyz
On my previous pc I had difficulties making it boot from CD so I used a Smart Boot Manager on a floppy disk.
When you boot from this floppy it displays a menu of your hard drive(s) and CD Rom and asks you which you would like to boot from.
It may have been this one that I used, or something very similar:-
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)
This might solve your problem though I'm pretty sure you should be able to alter the boot up sequence by altering settings in the BIOS if you can find information about your motherboard.

---

### Post by haxer on 2006-09-23
No not 90s try 80s :)

---

### Post by xyz on 2006-09-23
A couple of people on this thread have nothing better to do than not help!
It seems we've been harassed by too many useless threads/posts these past few days.
Note that I didn't start this thread to find out when floppies started. Thank you for your understanding.

---

### Post by bri_06 on 2006-09-23
It was only a joke. :rolleyes: 

 I hope you figured out whatever you are doing with the floppies. ;)

---

### Post by xyz on 2006-09-23
;)  ;) 

I'm looking into it...so far not so good!

---

### Post by xyz on 2006-09-23
> **junglepeanut said:**
> Create boot floppy, create boot cd from DSL or others (DSL will get many hits in google for boot floppy with how to make one.) 

Before you do that though, as I went through the whole process, and it seemed after about thirty floppies I had laying around I finally found one that would burn fully. I then was doing a search and found the way to change my pc's boot order. I.e I was under the impression it was unchangeable and trust me I really tried. But in the end it turned out there was a special key sequence that had to be entered before the option would be allowed. Something like ctrl then hold delete for along time.

Just look online for your motherboard and hopefully...it may not have the option so otherwise hope you have more than one floppy at least. I may have the floppy laying around still if you can't find any of the files. I can send em to you, but you will still have to make it bootable.

I went to a friend's and downloaded SmartBootManager and wrote it to a floppy. Just 2 things before I go on: 

- I have no running OS in this box (I deleted Win 98 SE)
- my BIOS set-up is:

  Boot first device:  Diskette Drive
  Boot second device: Internal HDD
  Boot third device:  NONE

From what I read here and there, I need to have my Floppy AND the CD-ROM to work simultaniously; that is, I need SBM floppy in the Diskette Drive and the distro CD that I want to install in the CD-ROM.
The problem is I can't run both at the same time; it's either or as there's only one slot for both.

So then I managed to install SBM and, that way, I can pull out the Floppy drawer and insert the CD-ROM with say Deli distro CD in it.

And nothing happens! Any thought on how to go on from here? Thanks.

---

### Post by ron999 on 2006-09-23
Hi xyz
I didn't realize that you didn't have floppy drive AND cd rom fitted.
You're running out of options.
Maybe you could take your hard drive round to your friend's house and disconnect their hard drive and hook up yours while you install Ubuntu from cd.
Once you have Ubuntu installed on that hard drive you will have no problem booting because GRUB will elbow it's way to the front every time.
I've not got any more bright ideas.:(

---

### Post by xyz on 2006-09-23
ron999 Thanks a lot for your time and help!
> Maybe you could take your hard drive round to your friend's house and disconnect their hard drive and hook up yours while you install Ubuntu from cd.

I thought about that and it would surely be the simplest best idea ever!
I just need compatibility, I guess, with my Dell Latitude CP Penthium-233/MMX
which must be about 10 years old.

I'm also looking for a distro small enough to fit in a floppy but...
I'd hate to have to give up!!!

---

### Post by xyz on 2006-09-23
I sent an email to Dell's Technical Support. I asked them why, despite following the procedure, I can't modify my boot order....we'll see!!

---

### Post by xyz on 2006-09-24
I also wrote to **Ben Gross**
[http://bengross.com/smallunix.html](http://bengross.com/smallunix.html)
who put up this interesting site!
My question:
> Hello Ben,
I don't mean to take too much of your time but if you have a minute to spare, I'd be immensely grateful. I read this:
[http://bengross.com/smallunix.html](http://bengross.com/smallunix.html)
This is what I need to figure out:
- I accidentely deleted Windows 98 SE from an old Dell Latitude CP - 64 RAM - 4.1G HD. So I've got a nice and totally empty drive.
- It boots from floppy and I can't change the boot order. It has "drawer-like" Floppy and CD-ROM which cannot be used simultaniously.
- what GNU/Linux distros could I download/write to a floppy and then proceed to install? Or any other OS which could allow me "to enter" this computer again?

Thanks for your help

His reply:
> Several of the distributions on the page allow your to boot from a floppy and then run a CD installer. Just search for floppy on the page. You could also boot from one of the CD distributions that will run in memory. Many devices will boot from a CD after it fails to boot from a floppy. Lots of distributions have a boot floppy to help you install. Just look around on the docs of various distributions. I have not tried this particular method of installation so I don't have a distribution to recommend.

Good luck,

---

### Post by junglepeanut on 2006-09-24
I am a little interested now and will continue to look into things. I was wondering if maybe you have access to a usb cdrom drive maybe we could make it work this way?

California, but I think you pretty much have the files already and it seems it must have been much easier for you to make a boot floppy. lol

Could you list all of the options you have for boot? (I think the easiest way would be to just scroll through them in your bios, writing them down.)

I have scoured the web and found that people have installed linux (seems to most often be slackware on this model), with out much complaint about set-up except for the initial sound issues most laptops seem to have. (One individual claimed pclinux was completely configured nicely out of the box for this model with all sound issues resolved, and he had run suse,knoppix, ...ubuntu etc the last I listed being the most important. :)

Maybe we can do boot floppy to usb flash drive?

---

### Post by xyz on 2006-09-24
> 1. I am a little interested now and will continue to look into things. I was wondering if maybe you have access to a usb cdrom drive maybe we could make it work this way?

Unfortunately no SCASI...
> 2. California, but
Say Hi to California for me...spent 12 years of my life in the Bay Area!
> 3. Could you list all of the options you have for boot?
Boot Speed 233 MHz
Boot first device: Diskette drive
Boot second device: Internall HDD
Boot third device: NONE

> 4. I have scoured the web and found that people have installed linux (seems to most often be slackware on this model), with out much complaint
Could you please direct me to where you found that?
> 5. Maybe we can do boot floppy to usb flash drive?
Can't boot from USB!
This Dell goes a long way back...1995.

Thanks a lot for your time.

---

### Post by chrisfay on 2006-09-24
> Can't boot from USB!
This Dell goes a long way back...1995.

I'm curious as to why you are even attempting this on such old hardware...an 11 year old computer?:shock: 

[friendly_sarcasm] Surley someone's giving away a pc built within the last decade... [/friendly_sarcasm]

---

### Post by xyz on 2006-09-24
Well I like to learn and since the beginning of this "venture", I did learn a lot. This could help me get this old beast on its feet or be used at a different time/place on another box, mine or someone else's.
Not every one is mucho $£$£$£$£...and I'm hoping to be able to use it at least for internet.

But if you have a spare box...say a bit of a younger lady...send it to me!
(friendly sarcasm)

---

