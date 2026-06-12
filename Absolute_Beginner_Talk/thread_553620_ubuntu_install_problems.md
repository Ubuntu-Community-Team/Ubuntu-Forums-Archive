---
title: "ubuntu install problems"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by blackcp on 2007-09-18
I downloaded the 7.04 live cd iso and burned it to my blank cd using iso recorder. Then, I popped the cd in and rebooted this time from the primary cd drive. All seemed well at the install screen. Al went wrong when during the cd was playing. An error read, "job control turned off, can't access tty" or something like that. 

Then I accidently left a blank cd in the cd-rw drive (secondary cd drive) and the problem appeared fixed. I prepared my partitions, and all seemed well again. Then I found out that my secondary drive somehow doesn't register. I noticed this when I was was downloading a xubuntu iso.  It's a sony cd rw drive. I'm not sure on the model number exactly, but this problem seems really bizzare. My pc is a dell dimension 4600 with A12 bios.  

Anybody know about this?

THanks

---

### Post by splintercellguy on 2007-09-18
Have you tried booting with all_generic_ide? That would have been the workaround for the tty job control issue.

---

### Post by blackcp on 2007-09-18
> **splintercellguy said:**
> Have you tried booting with all_generic_ide? That would have been the workaround for the tty job control issue.

what is all_generic_ide? I don't notice it in the boot order in my bios. How do I do something like that otherwise?

---

### Post by Drakkor on 2007-09-18
I don't know but.......Like i really don't know why they didn't put a sticky for this (which I suggested they do), but ....................
1. Did you check the md5sum of the download ??? To make sure you got a non-corrupt download. 
2. Did you check the disc for defects ????  To make sure that there was no burning error .

---

### Post by blackcp on 2007-09-18
> **Drakkor said:**
> I don't know but.......Like i really don't know why they didn't put a sticky for this (which I suggested they do), but ....................
1. Did you check the md5sum of the download ??? To make sure you got a non-corrupt download. 
2. Did you check the disc for defects ????  To make sure that there was no burning error .

I have not done # one but I did do #2 even though a blank cd was in the rewrite drive in order for it to tell whether or not the disk was defective. Says, that it isn't...

Also, how exactly does a md5sum check whether or not my iso download is really uncorrupt?

---

### Post by Drakkor on 2007-09-18
[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)
Also the easiest way to check it is just open a terminal, type ```
md5sum
```
and drag the iso into the terminal, hit enter, it will take a minute or so to calculate it.
Also you get the md5sum the same place you downloaded the iso from, depending on the
distro you got. :)  Then,assuming they match, burn the iso as an image, and then boot
to it, and select "Check CD for defects" to make sure it burned correctly. :)

---

### Post by Skidpad on 2007-09-18
^^^^ I learn something new around here every day!  Thanks Drakkor.

---

### Post by blackcp on 2007-09-18
> **Drakkor said:**
> [http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)
Also the easiest way to check it is just open a terminal, type ```
md5sum
```
and drag the iso into the terminal, hit enter, it will take a minute or so to calculate it.
Also you get the md5sum the same place you downloaded the iso from, depending on the
distro you got. :)  Then,assuming they match, burn the iso as an image, and then boot
to it, and select "Check CD for defects" to make sure it burned correctly. :)

I forgot to mention that I uninstalled ubuntu prior to this thread. I reverted back to windows xp so I'm now checking the file integrity with the link you suggested and having difficulty.

---

### Post by Drakkor on 2007-09-18
Try this: [http://www.nero.com/enu/Nero_MD5_Verifier.html](http://www.nero.com/enu/Nero_MD5_Verifier.html) :)

---

### Post by blackcp on 2007-09-18
> **Drakkor said:**
> Try this: [http://www.nero.com/enu/Nero_MD5_Verifier.html](http://www.nero.com/enu/Nero_MD5_Verifier.html) :)

Great! I'm gonna give it a shot right now and edit this post just to keep you up to date. 

I'm very grateful to your quick responce, Drakkor

BTW, I just reinstalled ubuntu using the suggestion that Splintercellguy did by pressing F6 at the boot screen and adding the "all_generic_ide" and so far I have ubuntu running and so far, it notices that I have a cd-rw drive. But you never know until you have tested the file integrity which I will get back to work on, on windows. 

THanks again

EDIT: I just tried your check sum, and from what I understand on how to use this thing: I downloaded Ubuntu 7.04 on Firefox via Free download Manager (my default download manager) and after it finished, I extraced only the md5sum text from the iso, copied it, and pasted it to the nero md5sum check (step one). I then browsed my folder to where the ubuntu iso was and the md5check sum did its work. So, it didn't match... I hope I did this correctly.

---

### Post by Drakkor on 2007-09-18
Which distro ? e.g. Desktop , Server, AMD64 ? And where did you download it from? 
There usually is a md5sum right there, so as to verify the download. :)

---

### Post by blackcp on 2007-09-18
> **Drakkor said:**
> Which distro ? e.g. Desktop , Server, AMD64 ? And where did you download it from? 
There usually is a md5sum right there, so as to verify the download. :)

I downloaded the Ubuntu feisy fawn 7.04 desktop version. I'll look for the md5sum again.

---

### Post by kevin11951 on 2007-09-18
> **Drakkor said:**
> I don't know but.......Like i really don't know why they didn't put a sticky for this (which I suggested they do), but ....................
1. Did you check the md5sum of the download ??? To make sure you got a non-corrupt download. 
2. Did you check the disc for defects ????  To make sure that there was no burning error .

you dont have to check the cd for defects, you can actually just md5sum the cd directly and check it against the original md5... just a thought.

---

### Post by Drakkor on 2007-09-18
blackcp, is this what you have ? 
e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso

---

### Post by Drakkor on 2007-09-18
Kevin, how do you md5sum a CD ? :)

---

### Post by blackcp on 2007-09-18
> **Drakkor said:**
> blackcp, is this what you have ? 
e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso

Alright, here's what I did with the information you have just provided me: I entered the md5sum text, "e296e3468358789904097fc8df29609a" without the quotes with the nero md5sum check. then I browsed my folder and entered the whole iso image. It didn't pass the test. in my next attempt time I entered the text, "e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso" and then again browsed the directory where the iso image was. It once again failed to pass the test. 

Have I done this right? If so, Must I download from a different location?

---

### Post by Drakkor on 2007-09-18
I'm going to make my Fiesty CD an iso, and boot to xp to check that out, could take awhile. :)

---

### Post by blackcp on 2007-09-18
> **Drakkor said:**
> I'm going to make my Fiesty CD an iso, and boot to xp to check that out, could take awhile. :)

I appreciate that. =)

---

### Post by Drakkor on 2007-09-19
One thing I want to make clear is ask you exactly where you got the .iso from, because I just 
made an .iso of the CD that Ubuntu shipped to me, and checked the md5sum against what
was on a Ubuntu mirror and they did not match. So it may vary even if it's the same distro.
Can you tell me where you downloaded it from ?

---

### Post by blackcp on 2007-09-19
> **Drakkor said:**
> One thing I want to make clear is ask you exactly where you got the .iso from, because I just 
made an .iso of the CD that Ubuntu shipped to me, and checked the md5sum against what
was on a Ubuntu mirror and they did not match. So it may vary even if it's the same distro.
Can you tell me where you downloaded it from ?

I downloaded it from Argonne National Laboratory which is in the North America Section.

---

### Post by Drakkor on 2007-09-19
I will download that iso and see what the md5sum is. :)

---

### Post by blackcp on 2007-09-19
> **Drakkor said:**
> I will download that iso and see what the md5sum is. :)

In that case, I'll just wait for your word.

---

### Post by Drakkor on 2007-09-19
Ok just downloaded it, and did the md5sum in Ubuntu and got this:
So if you got something different you should probably re-download it.

---

### Post by Drakkor on 2007-09-19
BTW, the md5sum was different on the disk Ubuntu sent, yours should look like this:
:)

---

### Post by blackcp on 2007-09-19
> **Drakkor said:**
> Ok just downloaded it, and did the md5sum in Ubuntu and got this:
So if you got something different you should probably re-download it.

I'll just redownload it tomorrow. since I must log off now.

---

### Post by blackcp on 2007-09-19
> **Drakkor said:**
> BTW, the md5sum was different on the disk Ubuntu sent, yours should look like this:
:)

And it does! I want to thank you so very much for the kind help. My iso (live version) is now perfectly clean thanks to your advice! On to burning it! I just hope it doesn't give me that job control error.

And you are right about one thing that is so crucial: there should be a sticky for md5sum checks because it is likely that at least 70% of the people who download ubuntu don't even know what it is.

---

### Post by blackcp on 2007-09-19
Sorry for double posting, but I now I keep getting this job control error inspite of the fact that it passed the MD5SUM check test. This happened when I proceeded to the boot screen to check the cd for defects. So then I suppose I should just press f6 at boot screen and add "all_generic_ide" ?

---

### Post by Drakkor on 2007-09-19
Jeez,blackcp, never had that problem, you could try this:
[http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error](http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error)

---

### Post by blackcp on 2007-09-20
> **Drakkor said:**
> Jeez,blackcp, never had that problem, you could try this:
[http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error](http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error)

Well, I managed to avoid the job control madness by inserting a cd in the re-write drive and thus it had no defects at all. 

I re-installed Ubuntu despite the link that you gave me, via the all-generic_ide method. So far, everything works decently. My system has 256 mb of ddr ram so and 7.04 requires that much. Some things do run a bit slow, but not relentlessly slow. 

btw, now that ubuntu is my primary system, I think I might try the alternate cd... or not depending on how well the system is performing.

In anycase, I decided to make a separate logical partition beside my primary ubuntu root partition for my personal files, yet I don't have any permission to copy any files to it. This is all practice for me though. Any tips otherwise?

Btw I'm now desiring to use the md5sum check via linux, from the wikipedia link you gave me because the simple method you gave me for ubuntu didn't do anything. I'm hoping it's my fault =)

---

### Post by Drakkor on 2007-09-20
Yes, it is,lol, sorry, just cut my left index finger up pretty bad,lol,hey there's blood on the keybord, ceap, can'r type, have to heal

---

### Post by blackcp on 2007-09-20
> **Drakkor said:**
> Yes, it is,lol, sorry, just cut my left index finger up pretty bad,lol,hey there's blood on the keybord, ceap, can'r type, have to heal

It's all good. I'll await your help.

BTW, the way I did the md5sum check on ubuntu was that I typed md5sum just like that on the terminal. I pressed enter then pasted the original md5sum text. I then dragged the ubuntu iso and pressed enter, nothing happened. I'd like to correct this with your help. =)

---

### Post by Drakkor on 2007-09-21
Just type in ```
md5sum
```  then a space ,then drag the .iso file into the terminal
then, click in the window, to make sure you have a flashing black prompt, then hit enter.
Compare it with the md5sum for the iso.It'll take a minute or so to calculate, then should be like this:

---

### Post by blackcp on 2007-09-21
> **Drakkor said:**
> Just type in ```
md5sum
```  then a space ,then drag the .iso file into the terminal
then, click in the window, to make sure you have a flashing black prompt, then hit enter.
Compare it with the md5sum for the iso.It'll take a minute or so to calculate, then should be like this:

Now I get it! I just got a bit impatient with it, that's all. Thanks alot for the help! =) Next stop, is checking whether my xubuntu iso image is clean.

---

