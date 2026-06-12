---
title: "Problem with new Computer"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by tazmanmn on 2008-03-02
Hi all I am sorta new to the linux world I used Ark Linux for sometime on my old computer and recently bought a new one with a Dual Core AMD nice little machine it came with no OS and I loaded ubuntu on it as the main OS. It was working great for almost two weeks I love this OS and now today something went wrong when I turn the computer it won't load a thing it just goes past the Ubuntu loading screen and then gives me a cursor in the corner and it won't even load the live cd that I am using right now on my clunker computer. Any help would be great...if need be I don't have a whole lot of nothing on there to loose so if I need to I can format the HDD which is a Serial ATA instead of the old kind. 
Thanks to all 
D

---

### Post by glennric on 2008-03-02
Can you boot the live cd on the new computer?

---

### Post by justleen on 2008-03-02
can you get into a terminal by pressing ctrl-alt-f2 (or just alt-f2) whe you have the cursos?

if you see the "ubuntu loading screen" you can already press ctrl-alt-f1. this will disable the splash screen, and give the output of the booting. Try and see if you can find what is giving errors this way

---

### Post by tazmanmn on 2008-03-02
No it like stops and gives like a terminal screen that I can offically say I don't know how to use yet...I'm still reading...what I don't get is I haven't messed in the terminal at all when it was working great and then this morning it went online for awhile and frooze up and no won't load nothing...

thoughts?

---

### Post by justleen on 2008-03-02
no to the live cd, or no to the ctrl-alt to get into a terminal?

you schould be able to see the ooutput during boot any way (you do see the splah right?)

as to why is stopped working.. bits and bytes are delicate thing... every now and then one falls over.. if you unluvky, its a vital one :)

---

### Post by tazmanmn on 2008-03-02
Well I don't know about the crtl alt yet I gotta hook the good one back up some way here
and if memory servs me correctly the kernal won't load was one of the problems...as far as the live cd goes it just won't go for some reason basiclly does the same thing that the HDD does.

---

### Post by glennric on 2008-03-02
Have you changed anything with the hardware?  Like added or removed some hardware component or physically reconfigured something?  Or did you make modifications to the bios?  If the live cd booted before and won't now then there must have been something like that.

---

### Post by justleen on 2008-03-02
obviously the CD should boot.. SHOULD, offcourse..
ehm.. did you power down the system when you tried booting of the live cd, instead of resetting?

Did you build this new system your self? as in, might there be a cable loose? 
On the lice CD you ca press ctrl-alt-f1 as well, while booting. See where that fails...

---

### Post by tazmanmn on 2008-03-02
Ok got the new one plugged in but this is going to take me a minute to play with cause I short a keyboard lol but I'll have some fun with it...I will try the disk boot crtl alt f1 
As far as the computer goes I ordered with the M-board in case w/ PS and added a video card and a gig ethernet card, and dvd burner and cd rom that is all I have done to it 
So let us see what the problem is.

---

### Post by tazmanmn on 2008-03-02
Hit ctrl alt f1 at the loading screen got ok's all done the line till it hit starting common unix printing system cupsd and now it is stuck there with cursor

ideas?

---

### Post by tazmanmn on 2008-03-02
Got the error I think we are looking for when I tried to boot from CD I ctrl alt f1 and get an buffer I/O error on device fd0 logical block 0

---

### Post by tazmanmn on 2008-03-02
still stuck on this cupsd section on the load I am thinking that is where the problem may lie

help anyone?

---

### Post by glennric on 2008-03-02
Do you have a floppy disk in the floppy drive?  Or is it possible that the floppy drive cable is loose?  /dev/fd0 is the device name of the floppy drive.

---

### Post by tazmanmn on 2008-03-02
there is no floppy drive in the computer at all not even a cable...

What about this Starting common unix printing system: cupsd

this is where the system keeps locking up at

---

### Post by glennric on 2008-03-02
Ok, did you make any changes in your bios at any point?  You should go to the bios and make sure that it is not seeing a floppy drive, and that all options related to floppy drives are disabled.

---

### Post by tazmanmn on 2008-03-02
How about I do this the easy way and someone tell me how to dump the HDD and I will reload from scratch...that seems to be the easiest solution before my wife makes me go buy icky vista :(

---

### Post by tazmanmn on 2008-03-02
Ok floppy drive stuff off in Bios (not really sure why it was on) but we are still stalling out at the load screen after hitting ctrl alt f1 it says ok almost all the way down the line until it gets to Common Unix Printing System: cupsd  and stalls out with a cursor on the left bottom next to the phrase....

Ideas anyone  thoughts???  
And thanks all that have said something
I may not be super smart at this os yet just gimme some time

---

### Post by glennric on 2008-03-02
Are you trying to boot from the live cd again?

---

### Post by tazmanmn on 2008-03-02
That same thing happens from either CD or HDD I don't know what I am looking at when it comes to that...

---

### Post by tazmanmn on 2008-03-02
This is really starting to drive me nuts...would some one please tell me what Common Unix Printing System:Cupsd is and how do I make it work or shut it off cause that seems to be the stalling point for my PC...

---

### Post by glennric on 2008-03-02
cups is the print system in linux.  It controls print jobs and sends them to your printer.  I don't know why this would stop your computer from booting.  It is most likely not the actual cause of the lockup.  What your screen shows you may not be the actual job that is causing the lock.  Now that bootup asynchronous there are more than one task running at a time during boot up, although the splash screen is just showing a sequential list.  I am not sure how to diagnose your problem as you can't actually get to a console.

---

### Post by tazmanmn on 2008-03-02
Ok now that I got back online again would it make any difference if I can get into the grub screen would that help solve my problem or is there any way to erase the HDD from the area I am in?

---

