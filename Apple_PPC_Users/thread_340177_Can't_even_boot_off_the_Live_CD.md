---
title: "Can't even boot off the Live CD"
date: 2007-01-16
forum: Apple PPC Users
---

### Post by ColBalt on 2007-01-16
:-k 
Just got my copy of ubuntu (6.06) in the mail. I've tried it all of how to boot off the disk.
Tried:
-holding down <c>
     flashing folder icon then boot into OS X
-hold in down <option>
     selected CD but nothing happens
-held down <command><option><shift><delete>
     white screen comes up for several seconds, then boots into OS X
tried sudo command ```
sudo nvram autoboot?=false
```
 rebooted but nothing.

](*,) 

I'm n00d at this, so if someone could help with some suggestion would be great.

Cheers

note: running G4 PowerBook 1.33Ghz, OS 10.4.8

---

### Post by linear on 2007-01-16
I seem to recall that some G4 powerbook users have had trouble with the Dapper LiveCD. You may need an alternate install CD (you may even need to start with Breezy and then upgrade). :(

---

### Post by sabertooth_cat on 2007-01-18
ColBalt,

I don't know much about this issue, but can let you know what worked for me (using 867 Mhz Powerbook G4) and Edgy alternate CD. I know how tiresome it can get trying all the different key combinations, wondering if your ISO is bad, if your hardware is messed up, etc.

Did you try zapping the PRAM (cmd-opt-p-r); I think you wait for 4 chimes? 

Here are some things you can try at bootup:

[http://davespicks.com/writing/programming/mackeys.html#boot](http://davespicks.com/writing/programming/mackeys.html#boot)

None of the above worked for me (tried different makes of CDs,  different burn speeds, different machines and software programs to burn the iso), until I did this, located at [http://docs.info.apple.com/article.html?artnum=14449](http://docs.info.apple.com/article.html?artnum=14449). Try at your own risk, it worked for me but YMMV. The site says: 

> PowerBook G4 (12-inch) 
PowerBook G4 (12-inch DVI) 
PowerBook G4 (12-inch 1.33GHz) 
PowerBook G4 (12-inch 1.5GHz) 
PowerBook G4 (15-inch FW 800) 
PowerBook G4 (15-inch 1.5/1.33GHz) 
PowerBook G4 (17-inch) 
PowerBook G4 (17-inch 1.33GHz) 
PowerBook G4 (17-inch 1.5GHz)
If the computer is on, turn it off. 
Reset the power manager by simultaneously pressing and then releasing Shift-Control-Option-Power on the keyboard. Do not press the fn (Function) key while using this combination of keystrokes. 
Wait 5 seconds. 
Press the Power button to restart the computer. 


I'm out of time now but will respond more later about my experience if you wish. I spent a good amount of time looking for answers, but most start and end with "hold the 'c' key down when you boot up." I know it is frustrating, but hope you can find an answer.

---

### Post by ColBalt on 2007-01-18
:-? 
Thank you guys for the suggestions but it seems I still stuck. ???

linear: Took me a while to find the link for Breezy also tried the 6.06 Alternate CD, But I've gotten no further along.  Just getting the same screens as I explained earlier.  :\

sabertooth_cat: Thanks for all the suggestions. So I've tried various Boot Key Commands, to the various copies of ubuntu I have not collected ;) . But ya, I've gotten no further. But because of one of your links I was able to get into the open firmware boot holding down <cmd><opt><o><f>. :-s Am I able to force a CD boot from here? If so, What is the command?

Thanks again,
Cheers

---

### Post by linear on 2007-01-18
The Open Firmware command is:

[B]boot cd:,\\:tbxi

[/B](The mac still needs to recognize the CD as bootable, though.)

---

### Post by ColBalt on 2007-01-20
:frown:  No luck.
I'm thinking it's my system some how. I know I can boot off my OS DVD. Also tried an Os CD.
Thing is that this kind of sucks as I recently reformatted my HD include a partition for ubuntu. ](*,)

---

### Post by sabertooth_cat on 2007-01-20
> **ColBalt said:**
> :frown:  No luck.
I'm thinking it's my system some how. I know I can boot off my OS DVD. Also tried an Os CD.
Thing is that this kind of sucks as I recently reformatted my HD include a partition for ubuntu. ](*,)

ColBalt.
Did you try?:

> If the computer is on, turn it off.
Reset the power manager by simultaneously pressing and then releasing Shift-Control-Option-Power on the keyboard. Do not press the fn (Function) key while using this combination of keystrokes.
Wait 5 seconds.
Press the Power button to restart the computer.

Shift-Control-Option-Power when the Powerbook was shut off was what finally worked for me.

---

### Post by ColBalt on 2007-01-21
> **sabertooth_cat said:**
> Shift-Control-Option-Power when the Powerbook was shut off was what finally worked for me.
I did try your suggestion right away. (heard the long beep) It did not make a difference. I also took out the battery and unplugged the power cord and held down the power button down for 5 sec. Still no difference.  :?

---

### Post by Tommy on 2007-01-21
> **ColBalt said:**
> :frown:  No luck.
I'm thinking it's my system some how. I know I can boot off my OS DVD. Also tried an Os CD.
Thing is that this kind of sucks as I recently reformatted my HD include a partition for ubuntu. ](*,)

I know this sounds basic but... are you sure you are trying to boot your Mac using the correct CD? It requires the PowerPC version of Ubuntu. Also, do you have a way to verify the integrity of the iso and of the finished CD? Your first post says you got the CD in the mail, but it's still possible that one is defective. It could even have the wrong label on it, for example (meaning maybe the label SAYS PowerPC but it isn't actually).

It won't tell you much but you can try booting OS X and popping in the Ubuntu CD and seeing what you see on the CD using the Finder. If you get some errors or if you have a disk with only one file on it you will know the CD didn't burn right. If it looks like an install disk, check any text files on it to see if it's actually a PPC disk.

As for verifying the integrity of the disk without booting it, I don't know whether OS X has a compatible utility, but that seems like it would be a reasonable next step. If you don't learn anything definitive, write back to this thread and I'll find a 6.06 CD and see what it looks like on my wife's iBook G4 running OS X 10.3.9. The PPC disk will have somewhat different files than an Intel disk, so it should be easy to tell.

---

### Post by ColBalt on 2007-01-21
The CDs are fine. I followed the steps for burring the ISO files too a 'T'. And most definitely I am using the PowerPC compatible images. 

This is the first line from the "README.diskdefines" file off each disk:
#define DISKNAME  Ubuntu 6.06.1 "Dapper Drake" - Release powerpc
#define DISKNAME  Ubuntu 6.06.1 "Dapper Drake" - Release powerpc  <<-Alternate
#define DISKNAME  Ubuntu 5.10 "Breezy Badger" - Release powerpc

I was looking through some of the other text files on Breezy. one has the line ```
boot cd:,\install\yaboot
```. I wonder if this will work in the Open firmware boot. I understand that it's the 'yaboot' the makes a computer dual booting. Am I wrong?

---

### Post by linear on 2007-01-21
> **ColBalt said:**
> I understand that it's the 'yaboot' the makes a computer dual booting.

Not exactly. Yaboot is the bootloader for PPC Linux; it's used whether you dual boot or not.

---

### Post by acaid on 2007-01-22
I'm on a Powerbook G4 and was having the same problem.  I downloaded and burned the Live CD, tried to boot (on a few different macs) but had no success.  
At this point I've managed to get to the splash screen by going through Openfirmware and using the "boot cd:, \install\yaboot" command but when yaboot comes up it gives me a warning, saying that the boot partition is Apple HFS and should be Apple_Bootstrap, but I don't see how I can burn a CD partitioned like that.  In any case, I ignored that and the splash screen came up and it got to where it said it was loading the root file system then the screen flashed, turned black and a cursor came up but it wouldn't respond to any commands... essentially restart time.

Anyone have any ideas?

---

### Post by hammonjj on 2007-01-22
Dumb question:

Are you sure you have the PPC Version?

---

### Post by ColBalt on 2007-01-23
Didn't you read my last post?

---

### Post by Tommy on 2007-01-23
We've already determined it's the right cd -- if you look in the README.diskdefines document, the first line will have the disk version and say it's for powerpc

I have a Dapper 6.06.1 cd here and I'll carry it home to my wife's iBook G4 and see whether it boots. I presome others have been able to boot them (surely someone tested the image)!  If it doesn't boot from the CD I'll report back here.

---

### Post by Tommy on 2007-01-24
I just booted my wife's iBook G4 using the 6.0.6.1 live CD and the 6.0.6.1 Alternate CD -- 

since it worked for me I guess I can't suggest much different. I booted by restarting, popping in the CD as soon as the screen was dark, and held down the C key on the keyboard until I heard CD activity.

I don't know if there's a setting to restrict how the Mac can start -- is there any way to tell it to only boot from a DVD but not a CD? (You did say the OS X DVD would start it, I believe.) You might try booting from an AppleCare CD and let it check out the hardware.

In the "olden days" I would have suggested that if you were using a non-Apple keyboard you might want to try the standard one, but I believe any USB keyboard should work in this case (since you're using a G4).

---

### Post by sabertooth_cat on 2007-01-31
ColBalt, any luck yet? If you solve the problem, please let us know what worked. I think 
this is a fairly common problem and that many people  give up without getting Ubuntu installed.

---

### Post by Myk0 on 2007-02-05
i have the exact same problem verbatim. im totally lost and did EXACTLY the same steps that you have taken. I also have hte same comp 1.33 powerbook g4... seems as if this is a major problem!

any ideas?

---

### Post by russ-&gt;b on 2007-02-05
OK.  I've been having lots of issues trying to boot from the live CD as well and I think I have a solution that has worked (for me at least) which gets me past that part.

By the way, this a PowerMac G3 350 MHz with 384 megabytes of RAM (new world mac).

1) Holding down the c key at startup did not work, the drive worked for a long time and then it gave up and booted up OS 9 off of the hard drive.  

2) Started in open firmware and told it boot cd -- it replied and said LOAD-SIZE is too small.
Then I told it boot cd:,\\:tbxi  --  again with the load size.
Then I told it boot cd:,\install\yaboot  -- still with the load size.

3)  I then executed reset-nvram, reset-all and as it was rebooting after the reset-all command, I caught it with the command-option-p-r key combo and let it do the boot chime 5 times or so. (reseting the pram)

4)  After that I immediately caught it in open firmware again and then miraculously boot cd:,\\tbxi worked!

It told me it was loading the kernel, etc.  From there I had a black screen for the longest time and then finally started seeing things, about 5 minutes of blackness though to be a little more precise.

Hope this helps some people.

---

### Post by russ-&gt;b on 2007-02-06
To clarify something in my last post, my installation completely froze and I needed to reboot from the cd.  When following my own advice I saw that it was not working and I was not able to boot off the cd again.

What got it working, same as before I just didn't include a step because I assumed it wasn't necessary, is after reseting the nvram and all and zapping the pram, get into open firmware and try boot cd.  This fails for me but then boot cd:,\\:tbxi works.  It's the strangest thing and I wish I knew more about why this happens.

If I skip the failed step of trying to execute boot cd, then from there everything else fails, really bizarre.

Good luck, etc.

---

### Post by I922sParkCir on 2007-02-08
On thing I ran into was an issue with my RAM. The live cd booted, but I couldn't get into Ubuntu until I swapped the RAM out. Hope this helps.

---

### Post by ColBalt on 2007-02-19
> **sabertooth_cat said:**
> ColBalt, any luck yet? If you solve the problem, please let us know what worked. I think 
this is a fairly common problem and that many people  give up without getting Ubuntu installed.

Still at a lost. I've done all that I can figure. :( 
I just can boot off any Ubuntu disk.

---

### Post by grazie on 2007-02-20
Did you read [this thread]("http://www.ubuntuforums.org/showthread.php?t=353955")? Someone with the same machine solved the same problem by replacing the DVD/CD rom.

---

### Post by jazzman on 2007-02-22
Did you use a CD-R? That's the only disks that worked in my G3s. Don't use CD-RW, DVD-R or DVD-RW.

I burned about 3 copies on different disks before I used a CD-R. Worked perfectly.

Good Luck!

Jazz

---

### Post by sabertooth_cat on 2007-03-02
I think a sticky or "how-to" addressing this PPC boot from cd issue would help a lot of people. If I was a reasonable person, I would have given up. I only got mine working because I have fairly good web search skills and refused to give up (because I like Ubuntu so much better than OSX).

---

