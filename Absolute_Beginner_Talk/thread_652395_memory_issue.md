---
title: "memory issue"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by popimp on 2007-12-28
First off I like this ubuntu.  Not a computer programmer type but it's neat.  
I replaced the guts of a computer from 1999,  Biostar mobo, p4 2.8 gig cpu with ht, 2 gig ram.  Problem is when I install both sticks of ram, the biostar logo ( first thing that shows on screen)  is pixelized in spots, and nothing happens.  If only 1 stick is installed, doesn't matter which stick or slot, everything is fine.

I don't know how to post a screen shot of the memory info which I read on another post. 

Like I said, I am far from a programmer.  Just trying to get to play bf2 game... yeah its old.

---

### Post by LinuxIsInnovation on 2007-12-28
Ehh??

---

### Post by popimp on 2007-12-28
I hit the wrong button, before I was done.......what a way to start..

---

### Post by CREEPING DEATH on 2007-12-28
Clear the CMOS and try again, there should be a jumper on the mobo.
How much RAM are you talking about?  A lot of older mobos have fairly low RAM limits and won't boot on more.

CD

---

### Post by RomeReactor on 2007-12-28
Hi. Look in your motherboard's documentation to see if it supports the two GB of RAM.

---

### Post by skymera on 2007-12-28
also check the slot supports it.

i have 4 slots and the ram i have on works in 2 =S

---

### Post by popimp on 2007-12-28
The mobo supports 2 gig ram.  Its a biostar P4M900-M4, two memory slots.  In the coms, it only shows 784K of ram.  I set it to defaults and saved/exited.  Any thing else to investigate?  Thank you sofar  

When I cleared the cmos, and installed the 2nd stick and it showed up in cmos as 196402K, but after i exited, to went to a blank screen and blinking cursor.  Am I supposed to type something?  I powered down and removed a stick and now I am reporting to you guys/gals.

---

### Post by popimp on 2008-01-01
ttt

---

### Post by RomeReactor on 2008-01-01
If you can, try running this command with each of the memory cards in the system:
```
sudo lshw -C memory
```
Are they different brands? are they the exact same type--for example, PC3200 400mhz? have you tried these memories in another system? are the memory slots in your motherboard clean? Biostar motherboards being cheap (I have one also), make sure you insert the memories correctly, all the way down, and that they are locked in place before turning the system on.

---

### Post by az on 2008-01-01
I gather that both memory sticks are not identical.

Not all ram is the same.  Some sticks have different timings and densities.  Your motherboard is what determines how you get them to work together.

The best you can do is try the stick in different order.  If you can't get them to work together, blame your motherboard.

Do not try to boot an operating system to check you ram.  Boot the Ubuntu cd and pick the memtest86 option.

Memtest only takes up a few kilobytes of ram.  It tests the remainder of your ram.  This is useful, since your ram can appear at the beginning of the powerup stage, but be completely unusable to the motherboard nonetheless.  Memtest will be able to boot and check it.  What you would see is memtest finding the first 50 pecent of your ram okay (the first stick) and then showing errors for the rest.

It's a good idea to let memtest run overnight on a rebuild.  There are memory faults that can take up to a half hour to show up.  In some of the later passes, memtest will write a pattern to ram, wait a half hour and then check it again, rinse and repeat.

---

### Post by popimp on 2008-01-02
> **RomeReactor said:**
> If you can, try running this command with each of the memory cards in the system:
```
sudo lshw -C memory
```
Are they different brands? are they the exact same type--for example, PC3200 400mhz? have you tried these memories in another system? are the memory slots in your motherboard clean? Biostar motherboards being cheap (I have one also), make sure you insert the memories correctly, all the way down, and that they are locked in place before turning the system on.

[IMG]http://i138.photobucket.com/albums/q251/fl96thunderbird/Screenshot-memtest1-OpenOfficeorgWr.png[/IMG]

---

### Post by popimp on 2008-01-02
I ran the memtest from the cd and the first stick was okay after an hour......the 2nd stick failed after 4:19.  But then why will they run okay in  my g/f's pc no problem?  I ran the memtest on hers with my two sticks and her 1 gig stick as a comparision.  And after an hour, no problems from any stick.  If its the mobo, should it be replaced? Or just a new stick?  They are the same Kingston KVR667D2/1GR.
  Thanks for the help guys.

---

### Post by RomeReactor on 2008-01-02
It is possible the problem is the motherboard, but unless you're willing to spend 20 or 30 dollars for a new one, first make sure the slots are not dirty, broken, and that there are no signs of them being burnt.

---

### Post by warrior24 on 2008-01-02
It might be that the stick is not seated properly. Happened to me yesterday out of nowhere.

---

### Post by az on 2008-01-02
> **popimp said:**
> And after an hour, no problems from any stick.  If its the mobo, should it be replaced? Or just a new stick?  They are the same Kingston KVR667D2/1GR.
  Thanks for the help guys.

I would say it's the motherboard.  Should it be replaced?  Well, I wouldn't use it as a production machine (mission-critical stuff), and I would not put any ram in that second slot...  If you can run it with just one stick, and it passes memtest overnight, it should continue to work fine.

Check your fans, too.  An overheating CPU can mimic any other hardware problem.

---

### Post by popimp on 2008-01-02
Upon closer inspection of the ram, they have different names on the black square (don't know the technical term) but they both say kingston.  The good stick can run in either slot no problem.  So I guess my g/f got some extra memory, and i'm in search of another stick.  I know, I know, it'll be the same as I have.  Thanks very much for the help.

The side panel has not been replaced yet cause of the memory issue.

---

