---
title: "[SOLVED] A bit nervous about &amp;quot;Diving In&amp;quot; to Ubuntu"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Andavane on 2007-07-07
Greetings.
I am about to install Ubuntu for  the first time.
I have an IBM machine with a 40 Gb hard drive which contains Windows XP-Pro.
In the Computer management section this is called “Disc 0”, containing 6 partitions.
In the drive which used to be the CD bay I have another hard drive which contains 112 Gb, it has been initialized, but that is all—not partitioned or anything. It is referred to as “Disc 1”.

I have two books. One is “Beginning Ubuntu Linux, from Novice to Professional” by Keir Thomas, (2006) which has an Ubuntu CD in the back. I understand that this CD goes with the book; it seems a good idea to install from this.

However I also have the latest DVD “Ubuntu 7.04 Feisty Fawn”, and also feel that perhaps it would be best to install from this, as being the most user friendly. There is a DVD/CD drive on my machine.

I am not really sure how to proceed, or whether one could install both.. I am a bit nervous about going ahead with an installation, as my main work is on  Windows XP. However it is backed up, and I do have a laptop on which I can work with Windows. I do not really understand terms like “Grub”, and would be quite lost if something happened during installation which I don’t understand.

And yet I feel that it is not good to carry on dithering, and that I should do something.

As an absolute beginner I would much appreciate any sound advice as to how to proceed. perhaps Someone was once in my position.

i have read through help files as far as I can understand and have the  section

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

however as there is another fresh unpartitioned hard drive for Ubuntu I feel that other procedures may apply; so if there is a link to an article which outlines this, I’d be happy to know.

Kind regards

John

NB: For word processing etc I have been using Open Office for about 2 years now, and have just gone over to an accounting program called “Personal Accountz” which works on Windows, Mac, and Linux: particularly well on Ubuntu as I understand. So I have been making preparations for the “Move”.

---

### Post by buuntuu! on 2007-07-07
welcome!
as you have clearly done your homework there should be nothing to worry about!
just defrag your windows-partition several times, pop in your feisty disc (i wouldn't go for a triple install, so choose the newer distribution) and when given the option where to install,  select "resize existing partition".
by default this would give you a neat 50/50 split (with windows being the first and ubuntu the second part - change the settings to your liking)
i would install both OS on your 40gig partition and set up the big one as a data-partition, but if you want your windows-hd untouched it is also possible to install ubuntu on the second harddrive.

if you havent already, read [this,]("http://psychocats.net/ubuntu/index.php") easy to understand and all the info you should need!
have fun

---

### Post by sab0403 on 2007-07-07
Yes, you *could* install both. However this would be as efficient as installing XP twice because you had two different install disks. ;)

I'd recommend you used the Feisty LiveCD. It provides a simple way to see whether your hardware will work with Linux or not, plus you get to see and experience the environment, programs, etc. When you're ready to install, it's simple - just click on the "Install" icon on the desktop, and it will guide you through it.

As to your HD... the Feisty CD can be told which specific HD or partition it will use as the Ubuntu install (as well as which will be the swap). If you know which partitions holds what, you can simply avoid making changes to those partitions and the install won't touch them. Also, you can specify on which physical HD you're going to install - so, for instance, you can install on your bigger HD and leave the Windows install alone (which is highly recommended around here, for cleanliness if nothing else).

So boot from the LiveCD, try it out, and when you're ready to install, we'll be here.

---

### Post by Andavane on 2007-07-08
07/08/07
Thank you very much, gentlemen.
Will go ahead to install Feisty on the second hd (I have seen the live cd working); the scanner is ancient and due to be replaced, so will choose Linux compatible when the time comes for that ;)

Is there anything I should heed about this “GRUB” thing ? I have read that it may not go in the right place, and that it may not boot into Windows; something to do with the MBR which I don’t fully understand.

Kind regards

John

---

### Post by neoguy2012 on 2007-07-08
Don't worry too much about GRUB.  Usually, your Ubuntu installation will automatically detect Windows XP.  Just make sure that you know exactly which partitions you are installing it to and make sure that you do not mess with the windows partition(s).  Remember that you may need to make a small swap partition during installation, so always make sure you double-check everything to make sure you aren't changing the windows partition(s) at all!!  If you run into any problems with GRUB after installation, we will be happy to help.  Good luck!

---

### Post by BL00dFox on 2007-07-08
Hello and welcome to Ubuntu.

GRUB is the utility that handles boot loading. It is automatically implemented after you install Ubuntu. It automatically detects your partition table, reads the different operating systems, and asks you which one you want to load.

Please do not hesitate to ask any further questions.

---

### Post by Andavane on 2007-07-08
Thank you again.
Indeed,  I do not want to touch anything at all on the existing windows drive. The second drive is fresh and clean waiting there for Ubuntu.
Thanks for explaining what GRUB is. After all, everyone started not knowing this! ;) Do the letters stand for anything?
Will get everything checked and copies taken before proceeding.
The nightmare is that during the install, something will happen which I don’t understand.
Very fortunately I also have a Windows laptop I can get out on, so I may well take up your offer on help and will _Holler_ if things get sticky. 
Kind regards
John

---

### Post by Hallvor on 2007-07-08
I did the excact same thing a few months ago - made a dual boot and installed Ubuntu on a second hard drive. I was a little worried about GRUB, and thought I maybe would have to edit files in order to make the dual boot work, but Ubuntu just installed GRUB and everything worked - including Windows.

Of course, there is always a learning curve. But these forums are great if you need help, and the online wikis are very good. And if you need a break from it all, you can always boot into Windows again.

---

### Post by BL00dFox on 2007-07-08
> **Andavane said:**
> Thank you again.
Indeed,  I do not want to touch anything at all on the existing windows drive. The second drive is fresh and clean waiting there for Ubuntu.
Thanks for explaining what GRUB is. After all, everyone started not knowing this! ;) Do the letters stand for anything?
Will get everything checked and copies taken before proceeding.
The nightmare is that during the install, something will happen which I don’t understand.
Very fortunately I also have a Windows laptop I can get out on, so I may well take up your offer on help and will _Holler_ if things get sticky. 
Kind regards
John

A pleasure to help you. GRUB stands for: GRand Unified Bootloader. Be assured: the Ubuntu installation process is a dream. It is extremely user friendly, fast and the probability of something crazy happening is next to zero. However, PLEASE PLEASE make sure all your data is backed up (<---- Cant stress that enough).

Go ahead and call for any further help if needed :guitar:

---

### Post by davidjmayo on 2007-07-08
> Thanks for explaining what GRUB is. After all, everyone started not knowing this!  Do the letters stand for anything?

FYI
GRUB (GRand Unified Bootloader).

---

### Post by xlr8 on 2007-07-08
Andavane,

Your making the right choice by trying out feisty. I just set mine up for the first time a few days ago.

I had an absolutely flawless install with everything I've done. (including getting beryl up and running) and I know NOTHING about linux.

Anyways there's an article in the newest maximum pc magazine on installing ubuntu. They even tell you how to get it set up to dual boot windows. (this is the article that got me started with things) If i can find it online ill try to post it, if not you may want to pick up the august maximum pc. It not only outlines the install but it also walks you through what to do after you get it all setup. propietary drivers (think nvidia and ati), and java and flash, how to set up your wireless network, the list goes on and on.

---

### Post by dfreer on 2007-07-08
> **Andavane said:**
> Thank you again.
Indeed,  I do not want to touch anything at all on the existing windows drive. The second drive is fresh and clean waiting there for Ubuntu.


So "disc 0" is the windows drive, and
"Disc 1" is going to be the ubuntu drive, correct?

You might want to consider installing GRUB to the MBR of the blank drive "disc 1", if you truly do not wish ubuntu to touch the windows drive. By default it will install it to "disc 0" if I understand your drive scheme correctly. Either remove the windows drive, install ubuntu, and then pop it back in when done installing, OR you can change the boot order in BIOS to boot "disc 1" first instead of "disc 0", OR you can change the option manually within the installer itself.

Note: it will not destroy your windows drive to install GRUB to the MBR of disc 0; you will still be able to boot windows through GRUB, and if you ever get rid of ubuntu you can restore the windows MBR by using a Windows XP Disc. I thought I would bring this up since you specifically said you don't want it touching your windows drive at all.

---

### Post by BL00dFox on 2007-07-08
> **dfreer said:**
> So "disc 0" is the windows drive, and
"Disc 1" is going to be the ubuntu drive, correct?

You might want to consider installing GRUB to the MBR of the blank drive "disc 1", if you truly do not wish ubuntu to touch the windows drive. By default it will install it to "disc 0" if I understand your drive scheme correctly. Either remove the windows drive, install ubuntu, and then pop it back in when done installing, OR you can change the boot order in BIOS to boot "disc 1" first instead of "disc 0", OR you can change the option manually within the installer itself.

Note: it will not destroy your windows drive to install GRUB to the MBR of disc 0; you will still be able to boot windows through GRUB, and if you ever get rid of ubuntu you can restore the windows MBR by using a Windows XP Disc. I thought I would bring this up since you specifically said you don't want it touching your windows drive at all.

Although that information is accurate, I strongly urge you to ignore it at the moment. Just install Ubuntu on your seperate partition and it should handle the rest for you fine. As you learn more and more about linux, you can do what dfreer says.

>  I thought I would bring this up since you specifically said you don't want it touching your windows drive at all.

I think he meant that he doesnt want to alter his windows partition in any way.

I dont mean to offend the person who posted that info but I feel it may confuse John as it is obviously the first time hes installing ubuntu.

---

### Post by xlr8 on 2007-07-08
I just found the link to the article in maximum pc with a step by step guide on how to install ubuntu and get some of the other goodies working after the install is done.

It's a few pages long so instead of trying to copy and paste the article I'll just post the link.

[http://www.maximumpc.com/linux]("http://www.maximumpc.com/linux")

This should have you up and running in about 20 minutes, thats how long it took me believe it or not :-D

Oh and even if you dont use the article to do your install.. you REALLY should read it and print it, it tells you how to do alot of things that us windows users would have no idea about.

Hope this helps you as much as it did for me,
Tim

---

### Post by Andavane on 2007-07-09
Gentlemen, thank you one and all for your further advice on my situation.
It’s good to know that others have been in the same boat.

> So "disc 0" is the windows drive, and
"Disc 1" is going to be the Ubuntu drive, correct? 
Yes, dfreer, this is the case

> You might want to consider installing GRUB to the MBR of the blank drive "disc 1", if you truly do not wish ubuntu to touch the windows drive. By default it will install it to "disc 0" if I understand your drive scheme correctly. Either remove the windows drive, install ubuntu, and then pop it back in when done installing, OR you can change the boot order in BIOS to boot "disc 1" first instead of "disc 0", OR you can change the option manually within the installer itself.
....I thought I would bring this up since you specifically said you don't want it touching your windows drive at all.
Yes, I see: however I was unaware about the little file which would be written to disc “0” where windows sits. As BL00dFox has written, > I think he meant that he doesn't want to alter his windows partition in any way.  Indeed, I will just stick to the default procedure for now, particularly as the Drive “0” has the windows installed in a hidden partition in there, and you don’t get a windows CD. Useful advice to bear in mind for a future date, though.

And thanks to xlr8, Tim, for suggesting this article which I’ve pasted into a document to read.

I shall soon be working on the laptop with windows, where all the files and documents are, testing the Ubunutu out on this one. Hoping to be able to boot between the two on this one PC.

I’d like to add that a friend came round to install “Suse Linux” on my system, on another hard drive, in 2002, and the entire thing was a wall-to-wall nightmare; so I shleppt off to lick my wounds. Hence part of the reason to being so tentative about trying Linux again... ;)

Kind regards,

John
__________________________________
IBM Think-Centre
One 40 Gb hard drive housing windows xp
One 120 Gb hard drive in the CD-drive bay.

---

### Post by Andavane on 2007-07-12
Thanks chaps, one and all
Ubuntu 7.04 "Feisty Fawn" is now installed and up and running.
Apart from a few doubts (which were resolved by clicking "back" untill I could 'see' the destination for the OS), it did indeed all run like a dream.
Very smooth, and most impressive.

I trust that others who may exercise the doubt I had, will feel inspired to proceed.

The moral backing and goodwill from the forum has been a huge plus factor.

Will continue with a further point for clarification in another thread.

Regards

John

---

### Post by Andavane on 2007-07-12
Thank you everybody.
The installation has gone very well.
Trust that this will encourage other to move to Ubuntu Linux who have harboured doubts.
Now to knuckle down to the learning curve.   
Regards
John

---

