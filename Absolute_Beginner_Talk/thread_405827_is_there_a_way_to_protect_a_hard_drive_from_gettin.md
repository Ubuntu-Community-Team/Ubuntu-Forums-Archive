---
title: "is there a way to protect a hard drive from getting formatted??"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Cippa Lippa on 2007-04-10
Hi guys

the title of the post says it all. I recently formatted by mistake (how stupid can one be?) my backup hard drive where I had my thesis, all my recordings and all my websites. 
I would like to avoid that in the future. 

Any idea?

P.S. any clue about a company that provides data recovery? I could recover tons of files but none of the really important ones for me... (Murphy's law...)

Cheers

---

### Post by thefoolisme on 2007-04-10
Well, the obvious answer would be to unplug the hard drive that you want to protect.  That way, even if you make a mistake, it will be safe.  

I also highly recommend backing up your important files regularly regardless of whether you are going to attempt a hard drive format.  Hard drives do fail, and if the files are that important, they should be backed up on a DVD or CD, or in the case of your thesis, even emailed to yourself so there is another copy of it out there.  

In terms of recovery, I have tried several different programs in the past for friends who neglected to back up important documents, but all were only partially successful, so I can't give you a sure-fire answer there.

---

### Post by kazuya on 2007-04-10
There are some companies and softwares that do so. It would cost you alot of money though. Just google and you would find ones like this here:

[http://www.google.com/search?hl=en&q=data+recovery](http://www.google.com/search?hl=en&q=data+recovery)

Good luck though. Some really works, but you have to measure the worth of your data?

Sorry again about this. How did this happen if I may ask?

Also, if installing another OS, I recommend a totally different hard drive not just hard drive partition. This way, you know for sure you are not touching what needs to be untouched..

---

### Post by az on 2007-04-10
No, you cannot "write-protect" a hard drive.

As for data recovery:
[http://ubuntuforums.org/showthread.php?t=401093](http://ubuntuforums.org/showthread.php?t=401093)

---

### Post by Cippa Lippa on 2007-04-10
[quote: Sorry again about this. How did this happen if I may ask?]

It happened because ubuntu really s*rewed me! Basically I have two external hard drives and I was trying to recover one of them that had fell and is not readable anymore. When I was going for reformatting I didn't realize that I plugged in the hard drives in the opposite order that I usually use so what was usually my /dev/sda became the /dev/sdb and vice versa... so... I formatted the wrong hard drive.
I know it is in the end my fault but I still have to see an OS that really makes sure that you are not screwing up something at least furing thhe most delicate operation of all computing: formatting.
Is it so hard to make this thing work on hard drive labels insteadof labeling the hard drive depending on in which order it is mounted????


Sorry for venting but that was precious.

Cheers

---

### Post by Cippa Lippa on 2007-04-10
by the way, I think I am going to switch to ubuntu at 99% (still need flash, rhino, matlab). You know these incredible strong of accidents (hard drive falling and other hard drive screwed in the process of repairing the other) just mean to me that a new beginning has to take place. And now I can't go back to win, as it would really be a defeat (my Linux experience would have meant just two sacrificed hard drives and nothing more). 
Anyway...,
Do you guys know how to really blank a hard drive? I want to start clean and I am having trouble to find something that really wipes the hard drive down to a strong of zeros.

Cheers

---

### Post by jhenager on 2007-04-10
> **Cippa Lippa said:**
> 
Do you guys know how to really blank a hard drive? I want to start clean and I am having trouble to find something that really wipes the hard drive down to a strong of zeros.

Cheers

Darik's Boot and Nuke (DBAN).
If you can recover any data after this has run, you are good. You can find it with just about any search engine.

---

### Post by az on 2007-04-10
> **Cippa Lippa said:**
>  really blank a hard drive? I want to start clean and I am having trouble to find something that really wipes the hard drive down to a strong of zeros.

Cheers

You mean, after you recover your thesis.  You should really try using foremost to save your files on the drive before you wipe it.  Only about one percet of the data is overwritten when you format a partition to ext3.

Use badblocks to wipe the drive.  Use the "write" test.

sudo badblocks /dev/hda -w

---

### Post by Cippa Lippa on 2007-04-10
> **az said:**
> You mean, after you recover your thesis.  You should really try using foremost to save your files on the drive before you wipe it.  Only about one percet of the data is overwritten when you format a partition to ext3.

Use badblocks to wipe the drive.  Use the "write" test.

sudo badblocks /dev/hda -w

Yes of course...
Then there is something odd because the best software I could find for windows (R-studio) was maybe able to recover at most 20% of the total hard drive and many files were corrupted or partials. I was also surprised at the level of damage that seem to have happened. Might it been that it was horribly fragmented? Even though I ran Norton systemworks regularly (last time maybe one month ago)? I reallyy can't explain me this damage... I mean the formatting lasted only something like one minute... come on!

Cheers

P.S. by the way I like a lot that command you wrote down. It looks so darn SCARY easy too literally wipe the hard drive...

---

