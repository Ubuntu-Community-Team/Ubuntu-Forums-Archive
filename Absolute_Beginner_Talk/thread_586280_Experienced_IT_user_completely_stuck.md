---
title: "Experienced IT user completely stuck"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by puzzled-in-penzance on 2007-10-22
Hi All 
Having just spent £300 upgrading my:
[LIST]
[*]motherboard (Foxcomm K8M980M2MB-RS2H),
[*]CPU (AMD Athlon(tm) 64 X2 Dual Core), 
[*]Graphics card (ATI Radeon HD 2400 PRO)
[*]DDR2-SDRAM PC2-6400 (2 Gigs!)
[/LIST]
Followed by three frustrating weeks unable to get the card to load the right driver under Windows 2K, and then using a 120 day free trial of XP Pro 64 bit which wouldn't run some of my essential software and a couple of minor peripherals, I decided it was time to try Linux again and downloaded Ubuntu I've been hearing so much about.

When I experimented last with Linux it was early days and no drivers for my graphics etc so I went for Windows 2000 instead.

I've 15 years professional experience DTP and graphic design and website basics and teaching that too . . . with both Microsoft and Mac platforms, so I'm above average when it comes to software. The impression I got from the Ubuntu site was "installation is simple."

I have now downloaded 3 versions of it, burnt them onto CD (verified too). I insert in the drive and boot from CD . . . and NOTHING HAPPENS.

Well, a message asking me to insert a System Disk and try again. What's going on guys? I have two SATA drives I usually set up in a RAID 1 array with an external USB for backup. 

But new hardware, new O/S it seems prudent to leave them separate and basic. I've failed to get Win 2K to run on one, and Linux on the other. 

Now I am thinking I should have coughed up the extra and gone for that super duper Intel Core Duo tower running OS X Leopard.

I need a solid, reliable, fast computer, capable of producing print quality pdfs. I've heard Gimp can do most of what Photoshop can, but even if I need to run Windows apps from a Linux core . . . I need to get the BIOS to do something with the ubuntu iso.

Any ideas?

---

### Post by Greg Knight on 2007-10-22
Quick question.....

When you burnt the discs; did you just copy the .iso file to the disks, or did you use them to burn an image to the disk?

---

### Post by buzzmandt on 2007-10-22
> I have now downloaded 3 versions of it, burnt them onto CD (verified too). I insert in the drive and boot from CD . . . and NOTHING HAPPENS.nothing happens?  does it not even try to access the cd rom?

---

### Post by Scruffynerf on 2007-10-22
It sounds like you need to configure your BIOS first. That comes before the OS, be it windows or linux or whatever. This includes setting up the hardware RAID array.

When setting the BIOS, enable the function to boot from a CD.

The "system disk" it's asking for could well be the Bios CD that comes with the hardware supplier.

---

### Post by csabimeta on 2007-10-22
Have you configured boot sequence in your BIOS correctly?

---

### Post by kellemes on 2007-10-22
Will any other bootable rom boot?

---

### Post by Sef on 2007-10-22
Do not burn the iso at more than 4x.  If faster, it can corrupt the burn.

---

### Post by Cheat King on 2007-10-22
I'm 12 and I installed it easily. ;) Just saying... :P

---

### Post by hyper_ch on 2007-10-22
I'd also say either you did not burn it as ISO or you do not have booting from cd rom enabled.

---

### Post by puzzled-in-penzance on 2007-10-23
> **Greg Knight said:**
> Quick question.....

When you burnt the discs; did you just copy the .iso file to the disks, or did you use them to burn an image to the disk?

Thanks for your reply. I think you hit on the problem. I don't really understand what 'iso' is so I just copied it to disk. When I downloaded the demo version of XP Pro 64 bit from Microsoft last week, it too was an iso and it said copy it to disk and it worked no problem. 

If Microsoft can make this process idiot proof can't Ubuntu? I am an experienced user and got stuck - god help others! I burn CD's all the time, even written basic autorun.inf files but never used the iso function before.

I have had a partially set up Windows pc but have NOW installed Nero rather than XP 'copy to CD' function. I then used the 'burn image to disk function' . . .  once . . . and I got a result. Unfortunately it was the text version and in German . . . my fault . . . the UK sites were so slow downloading I went further afield and got a quicker download. 

Please advise . . . is the 'alternative' version the text one? I think I'd prefer graphics but either way English would be handy. This seems so crucial . . . and all the online support offered is directed toward people who can read their disk.

Anyway . . . thanks for being the only person to reply to my post who gave me a truly useful answer.

Cheers

---

### Post by puzzled-in-penzance on 2007-10-23
> **hyper_ch said:**
> I'd also say either you did not burn it as ISO or you do not have booting from cd rom enabled.

The downloaded file was an iso  . . . copying it to CD seemed the obvious thing to do

I downloaded a demo version of XP Pro 64 bit from Microsoft last week . . . it too was an iso and I copied it to disk . . . and it worked first time. I do know how to configure my BIOS boot sequence settings!

---

### Post by justinmiller87 on 2007-10-23
> **Cheat King said:**
> I'm 12 and I installed it easily. ;) Just saying... :P
Two things:
1. How did your comment help the conversation?
2. Isn't it illegal for anyone under the age of 13 to be on the Internet?

And to answer your question, the alternate CD is the text-based install. You're probably going to be better off installing from the Live CD, as it guides you through the process.

---

### Post by hyper_ch on 2007-10-24
> **justinmiller87 said:**
> Two things:
1. How did your comment help the conversation?
2. Isn't it illegal for anyone under the age of 13 to be on the Internet?


1. It shows that even youngsters as him can understand this perfectly well and that the OP shouldn't give ;)
2. ???


--> [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Greg Knight on 2007-10-24
Yes the alternate installer is text based, but it's really not that scary.

However try the live cd first; that way you will be able to get a feel for the system without actually having to install anything.

They both do the same thing...  ask like 7 quetions and then off they go.

Let us know how you go!

Cheers!

---

### Post by akiratheoni on 2007-10-24
> **justinmiller87 said:**
> Two things:
1. How did your comment help the conversation?
2. Isn't it illegal for anyone under the age of 13 to be on the Internet?

And to answer your question, the alternate CD is the text-based install. You're probably going to be better off installing from the Live CD, as it guides you through the process.

Well, not on the Internet, but most forums do not allow children under 13. But, anyway...

The text-based installer isn't as scary as it seems. I too wanted to install by Live CD, but when my resolution was so different I couldn't even hit the 'next' button on the install, I went ahead and used the alternate CD.

But during the installation, isn't there an option to choose English for the installation (and default language of the computer)? So it might have not mattered, if you could go through one or two screens to find the language choose. But I might be wrong.

---

### Post by linuxlizard on 2007-10-25
> If Microsoft can make this process idiot proof can't Ubuntu? I am an experienced user and got stuck - god help others! I burn CD's all the time, even written basic autorun.inf files but never used the iso function before.

Uh first off, if you downloaded the iso on a microsoft desktop, and microsoft's desktop didn't know what to do with an iso, then it's microsoft that didn't make the process idiot proof, not ubuntu. If you had clicked on an iso in ubuntu, it would have asked you if you wanted to burn it.

Secondly, an iso is a disk image, not a function.

Thirdly, thanks for giving me a laugh. The "experienced IT user" comes on with an attitude about his disk not booting and he doesn't even know what an iso is. I know,  it is very frustrating from where you stand, but if you step back and consider the experienced IT user says he needs something "idiot" proof I find that quite funny...

BEWARE linux, because if your patience is tried before you even manage to boot the live cd, you are in for a bumpy ride. I know because I rode it myself for several months back in the day, so part of the laugh is a look back at myself. Of course back (redhat 8 days) then linux really was confusing compared to today, and unlike today, that seemed to be what its users wanted (made them really cool and they could talk down to everyone) so don't be totally put off by your first trial. Ubuntu has brought linux a long way forward really fast the past few years.

Fourthly, cd burning instructions  are right on the page with the link to the iso. Just pointing that out in fairness to ubuntu.

> I'm 12 and I installed it easily.  Just saying... :P
:lolflag:

> 2. Isn't it illegal for anyone under the age of 13 to be on the Internet?
:popcorn: This thread just cracks me up over and over again! 
Cheers!

---

### Post by jusmurph on 2007-10-25
> **puzzled-in-penzance said:**
> Thanks for your reply. I think you hit on the problem. I don't really understand what 'iso' is so I just copied it to disk. When I downloaded the demo version of XP Pro 64 bit from Microsoft last week, it too was an iso and it said copy it to disk and it worked no problem. 

If Microsoft can make this process idiot proof can't Ubuntu? I am an experienced user and got stuck - god help others!

Please advise . . . is the 'alternative' version the text one?
Cheers

Iso is the stanadrd Image format, plenty of others exist but when in doubt don't rely on your experience as a graphic artist to help your IT work. If i were you i would have googled ".ISO" to work out what i was dealing with. Sticking with what you know is detrimental to the ability to learn, anyway

The alternative one is definitely a text version, which is you will only need, if you know you need it.

---

### Post by -grubby on 2007-10-25
Did burn you burn it as an ISO file and not a data CD?The CD burner program that comes with windows won't due. I wasted about 6 CDs before I knew I was doing something wrong so I picked up [infrarecorder]("http://infrarecorder.sourceforge.net/")

---

### Post by LaRoza on 2007-10-25
> **puzzled-in-penzance said:**
> 
If Microsoft can make this process idiot proof can't Ubuntu? I am an experienced user and got stuck - god help others! I burn CD's all the time, even written basic autorun.inf files but never used the iso function before.


How can you be experienced, but not know what an iso image is? An iso image is a very common way to distribute disks.

There is no such thing as idiot proof, if you doubt your ability, it is recommended you ask for assistance.

---

### Post by ~chinook~ on 2007-10-25
Not to make fun of the guy or anything, but how the heck can you have 15 years of IT experience and not know how to burn an iso image.

---

### Post by AMDBuntu on 2007-10-25
Infrarecoder is a good, easy to use, free Windows based disc burning tool that will put the iso (disk image) on the CD so that it boots.

It takes about 24 hours of patience, working with Linux, to begin getting comfortable with it. 

No worries about the learning curve... :lolflag:

---

### Post by mmmfottrell on 2007-10-25
> **LaRoza said:**
> How can you be experienced, but not know what an iso image is? An iso image is a very common way to distribute disks.

There is no such thing as idiot proof, if you doubt your ability, it is recommended you ask for assistance.

QFT

also, like it was said before, the lack of "idiot-proof" burning is microsoft's fault, not Ubuntu's. 




P.S. Don't let us jerks discourage you from using Ubuntu. It really is great, even if the userbase is a bit condescending. :)

---

### Post by magicman5421 on 2007-10-25
If on your computer, though, if the live cd doesn't work/you get graphics errors, you will need to use the alternative cd. It's really not that scary. All it requires is a little bit of patience.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-10-25
I don't like breaking my one rules but

everyone try not to insult people even in the defense of some one else, and "Experienced IT _user_ completely stuck" dose not mean Experienced IT **Professional** 
or experienced IT** know it all ** saying this mostly for the thread poster because you have X year's experience blabla i would i have been an experienced it user scene i was like 3 

parten my flaming maybe some other ppl can say it better then me 

some links you should all read and maybe me again
[http://ubuntuforums.org/showthread.php?t=65842](http://ubuntuforums.org/showthread.php?t=65842)
this ones really good   [http://ubuntuforums.org/showpost.php?p=1488521&postcount=1](http://ubuntuforums.org/showpost.php?p=1488521&postcount=1)
[http://www.ubuntuforums.org/showpost...13&postcount=2](http://www.ubuntuforums.org/showpost...13&postcount=2)

---

### Post by Buried:. on 2007-10-25
I was able to burn at fastest speed and it working fine, try another Ubuntu download, check the others.

---

### Post by bigmonmulgrew on 2007-10-25
Can I just say 2 things. There is no such thing as an experienced IT user. there may be in certain areas, its like saying a carpenter will be a good plasterer because they are both in the building trades. IT is not on category it is many sub categories.

secondly to the thread poster. I get very annoyed at IT guys who think they know it all when it comes to computers. I work in a factory. I am an IT hobbyist. I write unattended windows disks, I can program, make web pages, I'm what PC world would consider a network expert, I build PCs in my spare time, I teach all kinds of basic computer use to folks who know almost nothing about computers. I may one day follow up my IT skills and get a job in the field but currently I'm happy where I am. Recently one of our IT guys came round, he couldn't log on to the computer near my line as the password had been changed. I mentioned it keeps getting changed randomly  and told him the new one. I asked him if he could remove it, a password is not needed on this computer, it is even written on the monitor by policy. He told me it is impossibly to setup this computer without a password, he also told me that the password had been changed because someone keeps turning the PC off during an update. This made me think 1 the next line over there is an identical PC with identical software which does not require a password. and 2 After all his talking down to me assuming im "just a factory worker" it was me and not the "expert" that realised that no amount of password changing will affect someones ability to press the power button, duh.

rant over.

My point is do not assume that you know lots about computers because you have been using them for years and do not assume that a high qualification makes you proficcient I've know degree students that know very little about their subject.
I'm not saying you don't know your stuff I'm just saying be a little more humble about what you know

---

