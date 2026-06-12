---
title: "Unusual Installtion error message"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Torqumada286 on 2007-12-20
I finished building a new system for my wife and am trying to install Ubuntu on to it.  I though I might have had a bad copy, even though its the one I used for my system a few days ago, so I downloaded and burned a new copy to be sure.  Regardless of which disc I use, I get the same error message at the first menu screen.  I get a 3 part box with two veritical columns and one horizontal one.

The left vertical column is labeled data and from top to bottom reads
:
:
0: 157.0
1: 917c1a
2: 917c1a
3: 0.0
4:  64.1

The right vertical column is labeled prog and reads from top to bottom
:
:
:
:
:
:
:
0: ffffffff.5
1: 1386.5

The bottom horizontal box reads:
err 8
ip 21e5: 10.7

Anyone able to help me decipher the problem?

Torqumada

---

### Post by Bartender on 2007-12-20
In the absence of anyone who knows what they're talking about, I'd say you need to apply some basic trouble-shooting.
Can you get to the BIOS screen?
What I'm getting at is does the PC appear to act normally until you pop the CD in?

If not, I'd strip the thing down, set up the mb on a piece of cardboard, put in one stick of memory, plug in a monitor, keyboard and mouse, then start it up and poke around in BIOS.  See if it seems to be working OK.  Then start adding parts, swapping memory, etc.

If the PC seems to be acting OK right up until you put the CD in, I'd swap the optical drive out and plug in a spare.  See if that does it.  
I'd still try swapping out memory sticks, too.  Use one at a time and see if there's a difference.
If your power supply is faulty, the PC might run but not very well.  Try a different PSU also.

Of course, go back and check to make sure all connections are snug.  Do you have a spare cable for the optical drive?  Try swapping the cable.

---

### Post by Torqumada286 on 2007-12-20
Yes, I can get into the BIOS without a problem and everything there appears to be normal.  Its all new parts (yes I know that doesn't necessarily mean anything), except for the optical drive, so I guess I can check there next.  I have never seen any error message like this before.  I'll keep trying.  thank you for the help.

Torqumada

---

### Post by Torqumada286 on 2007-12-20
Hmmm, its not the optical drive or the CD.  Time to start pulling parts.  Before I get too far though, I wanted to be sure those error messages weren't CPU related.:(

Torqumada

---

### Post by rkd on 2007-12-20
Two things I would try, just to gather some more information:
1.  Try booting some other CDs -- do you have a memtest CD around?  Or a disk test CD?  Or a Windows installation CD?  The point is to see whether some other OS can boot.
2.  Do you have a floppy drive that you could connect and try to boot memtest or DOS from it?

---

### Post by Torqumada286 on 2007-12-20
Actually, my Windows CD is missing at the moment.  I have a one year old son and had placed the case on a low lying shelf.  It has gone missing and I have my suspicions of who moved it.;)  So, for the moment I am stuck with the Ubuntu discs.  I burned a new copy just to be sure.  Working on memory at the moment.

Torqumada

---

### Post by Torqumada286 on 2007-12-20
Same error message running with one stick of memory, regardless of which one of the four I used..  :confused:

Torqumada

---

### Post by Torqumada286 on 2007-12-20
Anyone have any ideas?

Torqumada

---

### Post by rkd on 2007-12-20
Find anything else to boot.  See what a different boot program does.  Maybe it will give an error message that points more clearly to the problem.

---

### Post by ayenack on 2007-12-20
If you've got any network cards installed pull them out and turn off any networking in BIOS this might solve the install problem.

Let me know if this works.

---

### Post by Torqumada286 on 2007-12-20
I don't know why I didn't remember this until now, but I still have a copy of the most basic version of Vista that I used when I built a system for a friend a few weeks ago.  He hadn't paid me for my work yet, so I am holding the disc until he does.  I'll see if that will load onto this computer and then report back.  I am also re-downloading Ubuntu and will burn another disc and try that too.  

Torqumada

---

### Post by Torqumada286 on 2007-12-20
OK, this is really strange:  Vista loaded with no problems at all.  I downloaded a new version of Ubuntu and burned it to disc and tried to load it.  I get the same error message as before.  What is going on here?

Torqumada

---

### Post by discoade on 2007-12-20
daft question but your not trying to load a 64 bit version to a 32 bit machine are you or vice versa? mind you that wouldnt stop the live cd loading would it!?  or maybe your optical drive is struggling with cdr's? ok i'll shut up now! :)

---

### Post by rkd on 2007-12-20
Clearly Vista knows something about how to run the hardware on that computer that Ubuntu doesn't.  Just what it is, I don't know.

I don't have a clear idea of how far Ubuntu gets into booting before the error occurs.  Do you get the chance to give it the various boot options, such as to ignore the apci stuff?  If so, try that.  Or try downloading and using the alternate CD image which doesn't use any graphics capabilities -- just text mode display.

No guarantee either of those will get past the problem, but they are things I can think of to try.

---

### Post by Torqumada286 on 2007-12-20
64bit Ubuntu onto a 64bit machine, specifically an AMD Athlon 64X2 5000+ Black Box edition.

Torqumada

---

### Post by Torqumada286 on 2007-12-20
> **rkd said:**
> Clearly Vista knows something about how to run the hardware on that computer that Ubuntu doesn't.  Just what it is, I don't know.

I don't have a clear idea of how far Ubuntu gets into booting before the error occurs.  Do you get the chance to give it the various boot options, such as to ignore the apci stuff?  If so, try that.  Or try downloading and using the alternate CD image which doesn't use any graphics capabilities -- just text mode display.

No guarantee either of those will get past the problem, but they are things I can think of to try.

It gets no further than the menu.  When I choose an option I get the error message.  When I let the counter go to zero, I get the error message.  The only difference between my system and my wife's is the video card (I have a ATi 1900XTX, hers has a 1650 Pro) and the processor (I have an AMD 64X2 5600 and she has the Black Box 5000)

Torqumada

---

### Post by rkd on 2007-12-20
Maybe try booting the CD on a different computer to see whether the CD was recorded poorly or the image file is defective.  Kind of a long shot, I know.

---

### Post by Torqumada286 on 2007-12-20
No go on the Alternate CD. :(  I think I'll give it a break for the night and try again tomorrow.

Torqumada

---

### Post by ayenack on 2007-12-21
Have you tried switching the graphics card out of your wifes machine and swapping it with yours to see if that makes any difference?

Also the reason I suggested turning off any networking cards in my earlier post was that there seems to be something like an MAC (Media Access Control) network address as the error message at the end of the post.

Originally Posted by Torqumada286
> [I]The bottom horizontal box reads:
err 8
ip 21e5: 10.7[/I]

May be the same motherboard but not the same chip versions on the MOBO.

Just been doing a bit of research on error 8 it seems to be an error with GRUB not loading the Kernel. Reasonably sure this applies to your situation.
Take a look at this. [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting) go to **14.3 Errors reported by the Stage 2** (**section 8**).

Might be worth downloading the 32Bit version of Ubuntu and trying that there's not that much difference at the moment.

---

### Post by Torqumada286 on 2007-12-21
> **ayenack said:**
> Have you tried switching the graphics card out of your wifes machine and swapping it with yours to see if that makes any difference?

Also the reason I suggested turning off any networking cards in my earlier post was that there seems to be something like an MAC (Media Access Control) network address as the error message at the end of the post.

I hadn't tried that yet.


> May be the same motherboard but not the same chip versions on the MOBO.

Just been doing a bit of research on error 8 it seems to be an error with GRUB not loading the Kernel. Reasonably sure this applies to your situation.
Take a look at this. [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting) go to **14.3 Errors reported by the Stage 2** (**section 8**).

Might be worth downloading the 32Bit version of Ubuntu and trying that there's not that much difference at the moment.

Both boards are the 580X chipset from AMD.  The layouts on the board are exactly the same.  I may try the 32bit version, but does that mean losing access to the 4gb of RAM just like Windows?

Some other options I have come up with:
1)  I take out the HD, optical drive and video card and stick in all in the case with the older processor and memory (Athlon 64X2 4200 2gb) and try to load Ubuntu here.  Would it then be possible to swap the parts back to the new machine and have Ubuntu work properly?
2)  Take the HD out of my wife's machine and use my machine to load Ubuntu onto her HD and put it back into her machine and see if Ubuntu runs properly.
3)  When all else fails, try the sledgehammer approach.  It doesn't fix the machine, but it makes the person working on it feel much better.

Torqumada

---

### Post by ayenack on 2007-12-21
Have you installed restricted drivers for your ATI card if so might also be worth turning off restricted drivers popping the ATI card from your wifes comp into your comp and see if there are problems.  As you know your machine is working for sure may be an idea to test individual parts of the other comp in your box and see if you comes up with any errors.

As for the Memory you can have 4Gig installed but it can't all be used by a single process. Theoretically each process can use the low 3GB of address space then high memory kicks in and this all depends on how the high memory has been configured. Also some of the memory will be assigned to the kernel and not accessible to any running process. So it's an advantage to have as much memory as possible in my opinion. After a couple of hours the disk cache will want to take a big chunk when ever possible and just hold onto it even if it's not being used, it's an efficient use of memory that otherwise is just sitting there doing nothing at all most of the time. Just been thinking about this and I think in the 32bit kernel you may have to compile your own kernel to use all the ram and set the kernel to use 4GB and above in menu config. There's a good tool called KernelCheck [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/) that helps with this will probably even compile the new kernel to use 64bit kernel version.

For a bit more info on high memory see this. [http://en.wikipedia.org/wiki/High_Memory_Area](http://en.wikipedia.org/wiki/High_Memory_Area)

As for question 1 I'd say the answer is definitely no on that one. It wouldn't be practical or work I don't think. Same goes for Q2 as well.

 **LOL** Q3 Tried and tested to get the desired result, but also to loose you $1000 or so and make you cry after the satisfaction has dissolved into the ether and your left with a shattered and disintegrated computer components.

I've a feeling that this is probably to do with the processor maybe try the Athlon 64X2 4200 and see if that works before swapping out all the components.
Might also be worth making sure that the BIOS is set exactly the same as your comp if possible, might make a difference.

---

### Post by Torqumada286 on 2007-12-21
OK, more strangeness:  I took the HD, optical drive, and video card and put it in the old box with the 4200...same result!  :confused::shocked::(](*,)](*,)](*,)  Since I have already swapped out the optical drive, that just leaves the video card and the HD.  Time to dig up an IDE drive and see what happens. :roll: 

Torqumada

---

### Post by ayenack on 2007-12-21
:lolflag: Sorry.

Frustrating to say the least.:mad:

---

### Post by Torqumada286 on 2007-12-21
It was the video card the whole time.  This is the second time that I have had a problem with a Radeon 1650 Pro.  It must have been an off day with their QC.  Luckily, CompUSA did an exchange and since they dropped their prices since I got it, I actually got better card for her system.  Thank you everyone for their help.

Torqumada

---

### Post by rkd on 2007-12-21
I'm glad you found the problem.  It must have been an odd sort of failure with the video card to let Vista run it fine but for it to kill Ubuntu completely.  Always surprises.

---

