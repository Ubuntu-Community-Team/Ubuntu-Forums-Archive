---
title: "Can't get rid of Fedora!"
date: 2006-11-04
forum: Absolute Beginner Talk
---

### Post by storybookscribe on 2006-11-04
I'm helping a friend who let someone uninstall Windows XP completely and install Fedora (without giving him any disks).  I have an Ubuntu Disk but it stalls and won't install over Fedora.  So, I'm trying to boot his pc with his Windows XP disk but When the first screen comes up, the keyboard freezes and won't let him type/select *anything* to continue.

Is there something in the boot menu doing this or is it Fedora?  We need to get Fedora DELETED (without any disks) and then install Windows XP again so I can provide him with a dual boot.  If nothing else, to get Ubuntu installed.

I tried the Ubuntu disk on my computer and it runs perfectly.  For some reason, when I put it in his computer, it take *forever* to go from screen to screen, freezing completely after selecting English as the language.

Very desperate for help here!!

---

### Post by taurus on 2006-11-04
Try using the alternate CD because you have more control when it gets to the partitioning...

---

### Post by storybookscribe on 2006-11-04
What's the alternate CD?  I'm brand new to Linux myself.  The only disk I have is the one that came with *The Official Ubuntu Book.*  The only other disk I have is his Windows XP disk.  I tried both of them and can't get anywhere with either of them.

---

### Post by d3v1ant_0n3 on 2006-11-04
If the computer is freezing at GRUB, that shouldn't be a problem for the XP disk- You need to ensure that you change the settings in BIOS so that the cd drive is the first device- so you can install windows.

If it's freezing at POST ( the initial startup of the computer (where it displays the processor/memory, etc) then that is more serious, and probably not the fault of Fedora- since it hasn't got close to trying to load an OS yet.

What kind of keyboard is your friend using? and have you got a spare you can use.

More info on the computer in question might be useful too- specs, or at least the age of the computer- if it runs XP, it should be able to manage Ubuntu in one flavour or another.

---

### Post by storybookscribe on 2006-11-04
The computer is 2 years old.  AMD 64bit.  

It's not freezing at POST (thank you for describing what that is).  When the Windows XP disk starts, it wants me to press F1 to accept terms.  But at that point, no keys on the keyboard work.  I have one spare keyboard and that's doing the same thing.  

The Ubuntu disk is freezing after selecting ENGLISH as the language, if it even gets to that screen.

The BIOS is set up so the CD Drive is the first choice to boot from.

I'm really stumped on this one....

---

### Post by storybookscribe on 2006-11-04
Here are the computer specs based on his invoice:

H2100 Computer System
16x Combo CD-RW DVD-ROM 
AMD Duron 1600 Socket A CPU Type 8
256MB Elixir/Infineon OEM PC2700 333mhz DDR Memory
Seagate 40GB Barracuda 7200.7 ATA 100

He's an older gentlemen who got the pc from a place that builds them.  He uses it for the most basic of services.

---

### Post by storybookscribe on 2006-11-04
:::BUMP:::  Desperate for help, here.  ](*,)

---

### Post by taurus on 2006-11-04
If you have a fast network connection, you can download a copy of alternate CD for Edgy from here...

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

---

### Post by storybookscribe on 2006-11-04
Thanks, Taurus, but this guy is going to need to use Dapper Drake.

---

### Post by taurus on 2006-11-04
Well, Dapper Drake it is then...

[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

---

### Post by d3v1ant_0n3 on 2006-11-04
Just a thought, but USB keyboard or ps/2( the old style). I've had some problems installing windows before using a USB keyboard- although the keyboard WAS kinda flaky if i remember correctly.

The Live CD is being slow because of the amount of RAM in that comp, I believe 256 is the minimum recommended for the live cd, and by all accounts it's a bit of a slide show (as you've experienced!). If ubuntu itself is slow when installed, you might want to install the xubuntu-desktop package after install- it uses XCFE rather than GNOME, and is that bit less memory hungry.

---

### Post by storybookscribe on 2006-11-04
Thanks for the link, **Taurus**.

**d3v1ant_0n3**, It's a USB keyboard.  As far as installing xubuntu, I'll have to make sure my friend is able to learn how to use the basics in Linux.  I just wish he never learned about Linux.  For what he does on his pc, he really doesn't need it.  He heard this guy tell him that Linux doesn't need virus protection and that got him all excited and he let the guy goof around with his pc and now it's a mess.  I've always been the one to help him with Windows and I'm brand new to Linux, so I'm doing the best I can.

He paid the guy $70 for the pleasure, too.  ](*,) #-o

---

### Post by taurus on 2006-11-04
Your friend got one thing right.  You don't need an antivirus for Linux because I have never had one for all those years...  ;)

---

### Post by storybookscribe on 2006-11-04
> **taurus said:**
> Well, Dapper Drake it is then...

[http://ubuntu-releases.cs.umn.edu//6.06/](http://ubuntu-releases.cs.umn.edu//6.06/)

Downloading the Alternate CD for AMD now.  WOW does it take a long time.  The time remaining continually climbs higher.  Up to 2 hours.

To be honest, I wish I could just uninstall Fedora and get Windows XP back up for him.  I will be using a dual boot with ubuntu for myself, but my friend needs to stick with what he's familiar with.  I just wish I could figure out why the keyboard freezes and won't let me continue to install XP.

---

### Post by blendmaster on 2006-11-04
If you're really intent on getting Windows back, why not take the computer to a local shop?

Or better yet, have the friend who told him about Linux install Ubuntu, if he really does know what he's talking about.

That is, if you never get Ubuntu working, but I think once you put the alternate cd in, you won't have that problem (the alt cd tends to have a lot less problems when it comes to installing Ubuntu...).

---

### Post by storybookscribe on 2006-11-04
Thanks.  I'm downloading the Alternate CD right now.  It's slooooow.  24% done, but that seems to be my best option right now.  Just wish I knew why the keyboard sticks when it comes to reinstalling Windows.  Grrr...

Taking the pc to a shop to reinstall Windows would be a last resort.  This guy is on a fixed income.

---

### Post by heliumcyanide on 2006-11-04
Once I installed Fedora, over XP.  And XP Install would lock up because it had no windows partition type to dump its install files to, I fixed this by getting an old boot disk, and reformated to fat.  This was after deleteing the linux partitions, into freespace

---

### Post by storybookscribe on 2006-11-05
Still downloading the Alternate CD for AMD.  Zzzzzz.....  

I'm hoping this will do the trick. [-o<

---

### Post by taurus on 2006-11-05
> **storybookscribe said:**
> Still downloading the Alternate CD for AMD.  Zzzzzz.....  

I'm hoping this will do the trick. [-o<
Do you have a DSL or a dial-up?  That thing has been running, downloading, for a while, eh!

---

### Post by storybookscribe on 2006-11-05
LOL  DSL.  If this were on Dial-Up, I'd just have taken a sledgehammer to it hours ago!

To see if it would go any faster, I'm downloading it on my pc at home (across the hall) at the same time.  I have a fast laptop with a fast connection.  It's a barely faster download than my friend's pc.

---

### Post by taurus on 2006-11-05
What's the speed of your DSL then?  It usually takes me less than an hour on my 3mb line at home and at work, it would take about 20 minutes or less since we have T3!!!

---

### Post by storybookscribe on 2006-11-05
To be honest, I don't know.  I've had it for so long...

It just finished downloading.  1hr 56min!  And you know what?  I would have been EXTREMELY ticked off right now if I hadn't downloaded this to disk on my computer at the same time because I just realized that my friend's pc doesn't have a program on it now to burn disks!  My laptop does so it wasn't time wasted, but if I hadn't had mine going at the same time, I'd have been close to tears at this point!  I'd like to get my hands on the guy that did this to my friend's computer and introduce him to Jesus...........

Going to try installing from the Alternate CD now...  [-o<

---

### Post by Mimsy on 2006-11-05
> **blendmaster said:**
> 
Or better yet, have the friend who told him about Linux install Ubuntu, if he really does know what he's talking about.

Personally, I wouldn't trust any "friend" who charged me $70 to install a Linux distribution near my computer (even if it's not a free distro). It's supposed to be free for those who want or need it, and even more for those who fall in both categories.

I know it's completely off topic, but that just irks me.

/Mimsy

---

### Post by taurus on 2006-11-05
Okay, your friend needs to install this free burning program on his machine so he can burn whenever and whatever he wants...

[http://www.cdburnerxp.se/download.php](http://www.cdburnerxp.se/download.php)

---

### Post by storybookscribe on 2006-11-05
**Taurus**,

I can't thank you enough for sticking this out with me.  It's helped to know that I have a go-to person to help keep my sanity in check.  I'm going back to my apartment to get the Alt CD now.  Should be done burning by now...

---

### Post by taurus on 2006-11-05
You're welcome.  I am started to see double now so either I need to go to bed soon or I will crash right on top of the keyboard!!!

---

### Post by storybookscribe on 2006-11-05
The pc would not boot from the Alternate CD.  ](*,) 

I can open the CD but can't tell what files to click to install it.  No files with a .exe, like I'm used to with Windows.  There's an install folder, but just a lot of smaller files.  Nothing to indicate how to install it.  :icon_frown:

---

### Post by taurus on 2006-11-05
It doesn't even boot or does it give you some kind of error message?

---

### Post by storybookscribe on 2006-11-05
It just won't boot.  When I tell it to boot from disk, it goes straight to Fedora like normal.

---

### Post by taurus on 2006-11-05
Are you sure you've changed the order of boot sequence in the BIOS?  I would check it again to be sure...  And do you have another computer that you can test to see if you can boot from the CD?  You don't have to install it, just see if you can boot from it.

---

### Post by storybookscribe on 2006-11-05
I can try it on my pc.  Won't take but a moment.  I'm sure the boot sequence is correct.  I can boot from any other CD I put in the drive.

---

### Post by storybookscribe on 2006-11-05
It wouldn't boot on my pc either.  On both pc's, as the pc was starting, I hit F11 for the boot menu and scrolled down to the CD/DVD Drive.  It worked for other CD's, just not this one.

---

### Post by taurus on 2006-11-05
Argh!  It means that you've burned it wrong!  How did you burn it anyway?  Did you burn it as an image file with whatever burning software that you've used?

---

### Post by storybookscribe on 2006-11-05
It said it burned it as an ISO.  I don't get it.  I think it's just too late.  I'll try again tomorrow.  Too late to worry about it anymore tonight.  I'll continue posting in this thread tomorrow to let you know how it's going.

Thanks again, **taurus**, for *everything*!  I think it's time to go to bed and have a good cry!  :lol: 

Sleep well!

---

### Post by taurus on 2006-11-05
> **storybookscribe said:**
> It said it burned it as an ISO.  I don't get it.  I think it's just too late.  I'll try again tomorrow.  Too late to worry about it anymore tonight.  I'll continue posting in this thread tomorrow to let you know how it's going.

What program do you use to burn the ISO in Windows anyway?

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

> Thanks again, **taurus**, for *everything*!  I think it's time to go to bed and have a good cry!  :lol: 

Sleep well!

I am going to take a quick shower and go to bed and have a good dream!!!

---

### Post by Mimsy on 2006-11-05
I know, you're already in bed, having good dreams about a computer that actually works,but for when you wake up, try this: Burn the ISO as an image (as the guide says) and as slowly s is possible. I wasted three CDs before I realised that burning at the speed of a geriatric snail was the only thing that would give me a working live CD.

/Mimsy

---

### Post by storybookscribe on 2006-11-05
Thanks **Mimsy**...

I got some sleep.  Oddly enough, my dreams had nothing to do with computers or sledgehammers.  (I was braced for them, though!)

Once the Alternate CD downloaded, my computer automatically asked if I wanted to burn it to disk.  I just clicked OK and it did it itself, in about 10 minutes.  I don't think it gave me an option for burning speed. 

Since I have to do it again, I'll pay attention to see.  Thanks for your help.  I'm just baffled here...

I had other plans for the weekend that were really kind of important.  But I know that if I don't get my friend's pc fixed, he'll have someone else over to mess around with it some more.  [-(

---

### Post by taurus on 2006-11-05
Save it to your harddrive but don't burn it yet.  Then, use a regular burning software to do the burning.  Again, you can use the free one that I sent you (the link) and just follow the instructions from [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso) on how to burn it.

---

### Post by caravel on 2006-11-05
I had the same problem.  I had to boot from the livecd and use fdisk to remove the old fedora partitions.  Then I booted to the windows XP recovery console and did, fixboot and fixmbr.  You should then be able create new partitions to install XP.

---

### Post by storybookscribe on 2006-11-05
Taurus, will the link to the burning software that you gave (ubuntu) work on his pc if he has Fedora on it?  (Again, new to Linux)  

I tried to burn a Live CD from Fedora so I could use that to uninstall Fedora but their page won't open.

---

### Post by taurus on 2006-11-05
Actually, the link that I posted that contains a program is for XP only.  If you want to use Fedora Core to burn it, you can use k3b.  Look in Applications -> Sound & Video and you will see a burning program for it.  Again, make sure you burn it as an image file, not a data file.

---

### Post by storybookscribe on 2006-11-05
Taurus,

I just called the company my friend had his computer built at.  I explained everything to them and this is what they said...

1)  There's a hardware problem if the pc won't boot from a Windows XP disk (and we've tried three of them).

2)  The reason the keyboard freezes when trying to install one of the XP disks is because it didn't boot from the CD.  The CD was just opened up.  Since there's only a Linux OS on the computer right now, and Windows isn't Linux, the keyboard wouldn't work with it.

I've used about as much sanity as I can afford on this problem.  I'm taking the pc in to them and have them fix it.  Unfortunately, it will be about four or five days until it's fixed.  

They said he could use more memory though.  He has 256mb but they said Windows needs 512mb to run properly.  

Now, I have a question for you **FOR ME!**

Since I'm there, I want to see what they would charge for a system I could use strictly for Linux.  If I'm having a pc built, what should I make sure to have in it?  How much memory, what speed cd rom, etc.  I haven't bought a new computer in three years and I have no idea what's basic, etc., anymore.  Any programs I should be sure to get or should it be totally blank so I can load Ubuntu?  Just let me know what I should make sure it has and I'll be sure to get it.

---

### Post by storybookscribe on 2006-11-05
Hoping to hear from you soon so we can head out.  Can't blame you if you're busy or offline though!  You had a late night!

---

### Post by Tarvok on 2006-11-05
Well, to run Ubuntu, you need a minimum of 256 MB RAM and 3 GB hard disk space, though more is always better. Other than that, it comes down to what you want to do with the computer; the considerations are pretty much the same as with Windows. Slightly older hardware is more likely to "Just Work," since its more likely the drivers are already there. Believe it or not, I actually had an easier time getting my folks' Dell Dimension 2400 working under Ubuntu than I did getting it to work under Windows. With Windows, I had to do the CD Shuffle to get all the special drivers Windows doesn't have on there. With Ubuntu, once I changed the video cache from 1 MB to 8 MB in the BIOS, everything Just Worked.

As to programs, buy nothing; that is the whole point with Ubuntu. Just pop that disk in there and let it do its magic. There are probably thousands of apps available in the online repositories. It's truly amazing; my next computer (moving out of my folks' place and getting a comp to take with me) is shipping with no software whatsoever; Dapper Drake will do everything I need it to (even if I do have to wrestle with Wine from time to time for the few Windows games I'll want to play).

---

### Post by taurus on 2006-11-05
Yes, let them handle it since they already got paid for it.

Now, if you want to build a new system for Ubuntu (and don't care about Windows), I would go with at least 512MB of RAM or 1GB if you can afford it.  For harddrive, try to get as large as you can afford and I highly recommand you go for an nVidia graphic card.  I have eVGA GeForce 5700FX 256MB on my two computers and they both run great with nvidia driver.  For a CD, may as well go with DVD burner and 8x is plenty fast...  Now, the question is whether you would go with AMD64 or the new Intel Dual 2 Core!  If I were you, I would go for a 19" LCD monitor.  You can check out the components at [http://www.newegg.com](http://www.newegg.com) to see how much each piece would cost so you can get a good idea how much a whole system will set you back.

Good luck and don't let them sell you some crap or talk you into getting some crap!  ;)

p.s.  The power went out here for about half an hour so just got back on again!!!

---

### Post by annda on 2006-11-05
sorry to hear that the problem still persists.

as to your other question, i'd recommend starting a new thread with a more appropriate title so that people will know you're asking about hardware, not fedora anymore.

check out the ubuntu wiki here:
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

from my experience, suse and mandriva also have extensive databases (i know, it's specific to the distribution, but mostly what counts is whether there are open source drivers available for the linux world).

also, it's always a good idea to go for solid brand name components, even if they are not the latest technology. i am very happy with my laptop - Centrino 1,4 with 512 MB RAM and 128 MB ATI video. even Beryl runs smoothly on that.

good luck!

---

### Post by Mimsy on 2006-11-05
Ouch. That sledgehammer looks really tempting right now, doesn't it...?  ](*,) 

I'm using Ubuntu on an old laptop with 256 MB memory, and it flies across the web. It boots faster than my SOs gaming PC with WinXP. It's awesome. :) I installed Ubuntu on it because although it could run XP, it did it very slowly. Once I had installed the extra stuff you have to have on a Windows machine to avoid being killed by malware, such as a good AV, firewall, spywareblaster, et cetera, it was just too bogged down by background processes to be able to keep up.

So yes, your friend does need more memory. See if the shop has a deal on it right now, and have them install it while fixing the PC. You can probably get some sort of deal and get it done a bit cheaper that way. Unless you prefer to buy a generic module on Newegg and install it yourself of course. That's always the cheapest way.

As for a new PC, personally I would leave it compeltely blank, regardless of what OS I was going to put on it, just because I want absolute control over what is installed. It's a matter of preference. If you buy it with Windows installed you can set Ubuntyu up to double boot, if you want to be able to use applications that are not supported in Ubuntu yet.

What you need to put in your new PC depends almost entirely on what you plan to use it for. The one thing I would worry about, and research thoroughly beforehand, is to make sure that all components are compatible with Linux and known to Just Work(TM) with Ubuntu. There are good webpages for that information, but embarrassingly enough I'm not quite sure where they are. I know others here know though. *(Edit: QED... others do know.)*

Good Luck!

/Mimsy

---

