---
title: "Update ends in black screen"
date: 2012-04-16
forum: Apple Hardware Users
---

### Post by Javelin Dan on 2012-04-16
[FONT=Arial]The machine that is currently vexing me is a Mac G4 “Graphics” model that has a 40GB slave drive, a 450Mhz. processor and what I believe to be the original 256 MB of RAM. [/FONT]
 
[FONT=Arial]This is strictly a test mule, and I have been trying to get an operating system on it that 1.) would actually boot up, 2.) be updatable, and 3.) be hopefully be a little lighter weight. I’ve been downloading and burning various releases of the Lubuntu (Ppc) daily build, but they all end in the common problem I’m about to describe – after installation and re-boot I get a black screen with a cursor I can move but no desktop.[/FONT]
 
[FONT=Arial]I had a full install of Ubuntu 10.10 that though slightly sluggish, actually worked pretty well on this machine, but as everyone has discovered by now recently lost its support. Due to reported problems with Ppc installs of 11.04 and 11.10, I decided to do a minimum install of 10.10, install the Xubuntu desktop, and then do subsequent upgrades through the update manager to get to version 11.10, and then ultimately to 12.04 at the end of the month. [/FONT]
 
[FONT=Arial]The install went without a hitch, and apparently the first update did as well until the first re-boot where I ended up with the same black screen and movable cursor as described above.[/FONT]
 
[FONT=Arial]I posted about this problem when I was trying to install Lubuntu and someone told me it was probably due to lack of RAM. I finally gave it up and ordered 512 MB of RAM which I’m waiting to be delivered. [/FONT]
 
[FONT=Arial]I was wondering however, if this could be tweaked with a different xorg configuration. Is it possible to halt the initial boot-up (since I can’t get a desktop) to get to a terminal and then play with xorg settings? I have Googled this problem and also checked the archives here but have not been able to find the info I’m looking for. Any suggestions would be appreciated. [/FONT]

---

### Post by Javelin Dan on 2012-04-17
I'm still struggling with learning how to post a proper request in a thread. After doing some reading, I realized I should have included the info about my video card. the output of the command: 
"lspci | grep VGA" 
reveals an ATI Tecnologies Inc. Radeon RV250 If {Radeon 9000} (rev 01) graphics card

 I Apologise for the oversight of something obvious to everyone else. I hope this gives someone enough info to offer a suggestion.

---

### Post by linuxopjemac on 2012-04-18
Have a look here:
[http://mac.linux.be/content/g4-ati-and-17-inch-apple-studio-display](http://mac.linux.be/content/g4-ati-and-17-inch-apple-studio-display) or [http://mac.linux.be/content/powermac-g4-ati-radeon-9000-and-apple-studio-display-17](http://mac.linux.be/content/powermac-g4-ati-radeon-9000-and-apple-studio-display-17)

In principle I would think that this card should not give any problems. You might need to disable KMS to get X going in combination with an xorg.conf file...

To turn off KMS do the following:
```
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
```

---

### Post by Javelin Dan on 2012-04-18
[FONT=Arial]Thanks for responding linuxopjmac. I will gladly try your suggestion if I can figure out how to get to a terminal. Can I do it from the initial boot screen? If so, how? To clarify, once the full boot sequence has completed, all I have is a dark (not truly black) screen and a movable cursor. I keep searching for a thread that addresses this on this forum, but as yet have been unable to find it.[/FONT]
 
[FONT=Arial]Also, what is the difference between 10.10 and 11.04 – a newer kernel? If so is this also the case with Lubuntu 12.04 Ppc? I was just wondering why Lubuntu, which is supposed to be easier on resources on older equipment would be harder to run than Ubuntu 10.10 (which runs fine) on my particular machine. The lack of enough RAM may well be the problem, but that’s a big part of why I did the mini install as I read that it is supposed to require less RAM. Inquiring minds want to know…[/FONT]

---

### Post by linuxopjemac on 2012-04-18
You can boot with KMS disabled by adding the following kernel command:
```
nomodeset
```

so suppose in yaboot, Linux is your Ubuntu installation, you'd type
```
Linux nomodeset
```

you could also try with video=ofonly:
```
Linux nomodeset video=ofonly

```

In any case, CTRl-ALT-F1-F6 would give you a tty, where you could do some commands in the console.

---

### Post by Javelin Dan on 2012-04-18
Thanks - I'll try it and report back! May take a couple of days till I have the time.

---

### Post by rsavage on 2012-04-18
I regret to inform you that linuxopjemac's suggestions will have no effect in ubuntu 11.04 or 12.04.  You'd just be wasting your time.  
 
The ubuntu kernel config changed in 11.04.  Have a look at the PowerPC FAQ.  It tells you how to boot to a console prompt.

---

### Post by rsavage on 2012-04-18
Can you let me know if ubuntu 10.04/10.10 boots okay if you use the radeon.modeset=0 boot parameter?  So at the second yaboot prompt you would probably type:
 
Linux radeon.modeset=0
 
If you were trying a live CD it would be
 
live radeon.modeset=0
 
It's pretty urgent that I get a response since I'm currently trying to get the 12.04 kernel config sorted.  We are under kernel freeze at the moment.

---

### Post by Javelin Dan on 2012-04-18
I'll make sure I find the time to do it tonight and let you know.

---

### Post by Javelin Dan on 2012-04-18
By the way, could you please direct me to the Powerpc FAQ's? I found one link to it in this forum but it was a header over a blank page. Thanks.

---

### Post by linuxopjemac on 2012-04-18
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by Javelin Dan on 2012-04-18
Thank you!

---

### Post by Javelin Dan on 2012-04-18
***Success!!***

That did it rsavage! At the boot screen? (first black screen that says "boot" and some other things) I tried to type your command. My input wasn't accepted at first, but the screen flickered and changed to a new black screen that said only "boot". I assume that's what you meant by second boot screen (floundering in uncharted waters here). I had read the Powerpc FAQ's but didn't see anything I clearly understood that would get me to an actual terminal at boot. If I missed it, please correct me. Next to "boot" I typed in the command "*Linux radeon.modeset=0", *hit enter, and bingo - the boot continued to an 11.04 desktop. If I sequentially upgrade to 11.10 and ultimately to 12.04 am I likely to experience the same problem and will the fix be the same? You rock by the way!

---

### Post by rsavage on 2012-04-19
Eh? That was in 11.04??? radeon.modeset=0 does what linuxopjemac was saying which I said wouldn't work. It turns off KMS wich should be off by default in 11.04. 
 
I wanted you to try it in 10.04, but it doesn't really matter now.
 
I'll have to have a think about this why that command fixed it for you. If you can try a live 12.04 CD (try lubuntu) and let me know if you need that parameter I'd be grateful.
 
Thanks

---

### Post by Javelin Dan on 2012-04-19
You read my mind. I didn't have time last night due to a meeting, but tonight I planned to try the last daily build of Lubuntu I burned that wouldn't bring up a desktop and try the same command. Since I recorded it on the disk, do you need to know the date of that build? Just for the record, I never had a problem in 10.10 and don't recall ever trying 10.04. Also for the record, most of the daily builds that failed to boot a desktop on this particular machine *_would_* boot on my wife's G4 eMac that has 1 GB of RAM. So the problems I'm having seem to be limited to this box. I'll let you know...

---

### Post by rsavage on 2012-04-19
Thanks Dan.  It doesn't matter which daily build you try.  I still can't figure out why that works.....

---

### Post by rsavage on 2012-04-19
I don't think the kernel config can be changed now.  It is too late.  Hopefully radeon.modeset=0 will work for you in 12.04.

---

### Post by Javelin Dan on 2012-04-19
***Lubuntu 12.04 Failure!***

I loaded the last live Lubuntu disk I burned and entered at the boot prompt:  "*live radeon.modeset=0". *It booted through to the same thing I had before - a dark screen with a movable cursor. However, I did want to confirm that this _*did*_ work a second time on 11.04. 

Early this morning, I rebooted the computer and it had a safe landing into an 11.04 desktop. Tonight after I tried what you asked, I rebooted into 11.04 to a dark screen and movable cursor. So I repeated the process:  at second boot screen I entered *"Linux radeon.modeset=0" *and it booted into an 11.04 desktop again.

I received my 512 MB memory chip in the mail today. I'm anxious to see what it does, but will hold out to see if there's anything else you would like me to try with this machine in it's current configuration. My skills are very limited, but I'm eager to help if I can.

---

### Post by rsavage on 2012-04-20
I don't know what is wrong.  You could try it the opposite way and boot using
 
live radeon.modeset=1 radeon.agpmode=-1
 
Note the 1 and minus 1.
 
This will probably dump you at a prompt.
 
If you then issue the command
 
sudo start lightdm
 
you should get to a desktop.
 
The best long term thing though would probably be to run through the configure graphics sections of the FAQ.  I'll update it and the known issues page over the next week for 12.04.

---

### Post by Javelin Dan on 2012-04-20
I'll try it tonight and let you know.

---

### Post by rsavage on 2012-04-20
The other thing you could try is this:
 
At the yaboot prompt with 12.04 live CD type:
 
[noparse]live single video=offb:off[/noparse]
 
This will boot into a root prompt although you won't be able to see it!!!! You'll have to judge when the machine has finished booting.
 
Type the command (you are typing this blind):
 
modprobe radeonfb
 
You should then see text on the screen.
 
You can then type
 
sudo start lightdm
 
to get to the desktop. This is a bit of a bodged way because I don't know a better way at the moment!

---

### Post by Javelin Dan on 2012-04-20
For someone of my skill level it sounds a little like trying to catch a bullet in the dark with a pair of plyers, but I'll try it if I have to.

---

### Post by Javelin Dan on 2012-04-20
[FONT=Arial]I also failed to mention previously that I actually did print out the “configure graphics” section of the Powerpc FAQ, had it at my side last night while trying to boot Lubuntu 12.04, and tried virtually every command on those pages all to no avail. I just wanted you to know…[/FONT]

---

### Post by Javelin Dan on 2012-04-20
[I][B]Almost!  

[/B][/I]I did as you instructed with the 12.04 live CD. At the boot prompt, I entered *"live radeon.modeset=1 radeon.agpmode=-1" *and hit "enter". It immediately began to load the kernal and boot up to the Lubuntu splash screen and eventually went  to a black screen with a prompt. I then entered *"sudo start lightdm"*, hit "enter" and I eventually got to the blue Lubuntu "2012 Welcome" screen - but no icons. About 30 seconds later, it went to a black screen with a bunch of code. The top half appeared to list a bunch of software programs that all checked (OK) except the audio restart which said "failed"; the bottom half listed a lot of numbered code lines I didn't understand, but the numbers ran from 337.280218 to 338.987717. 

If you think this is related to RAM, I'll gladly put the new chip in and call it good to go. I know you must enjoy the challenge, but you may have better things to do...

On the other hand, if you are intent on solving this puzzle, I'll hang with you as long as I am able.

---

### Post by rsavage on 2012-04-21
Yeah, try your extra ram. If that doesn't solve it, then how about post #21?
 
FYI, ram usage is disussed on the lubuntu-qa mailing list at the moment [https://lists.launchpad.net/lubuntu-qa/msg00638.html](https://lists.launchpad.net/lubuntu-qa/msg00638.html) .

---

### Post by Javelin Dan on 2012-04-21
I'll try one or the other or both over the weekend and let you know.

---

### Post by Javelin Dan on 2012-04-21
[FONT=Arial]Strange things happening here today! I anxiously installed my new 512Mb memory chip to find my computer would not boot. I could hear the CPU whirring and whining, but the monitor would not respond - the little LED wouldn’t even change from yellow to green. I subsequently tried that chip in all four slots with the same result. Only after I put the original chips back would it work normally. So I guess I got a bad chip - I’ll have to send it back and see if they will exchange. 
[/FONT]
        [FONT=Arial]I did discover while doing this that I originally had 3 chips of 128 Mb and 1 of 64 Mb for a total of 448 of RAM. Not stellar, but from what I read in the Lubuntu qa you forwarded, it should be more than enough to boot Lubuntu Ppc.  [/FONT]
        
[FONT=Arial]Here’s where it got weird. The first time I pulled the new chip out, put the original back in and rebooted, I inadvertently still had the Lubuntu 12.04 CD in the tray. The Live CD booted up [/FONT][FONT=Arial]*_without_*[/FONT][FONT=Arial] holding down the “C” key, and it booted up [/FONT][FONT=Arial]*_FAST_*[/FONT][FONT=Arial]! As fast as if it were installed on the hard drive. I got a full desktop WITH icons and an update message telling me I had umpteen different updates to add. I swear to God it thought it was an installed OS! I played around on it just a little ( internet and such)  and it ran as fast as I always hoped it would on this machine. At this point I still didn’t believe I had a bad chip, so I continued to screw with it and interchanged the new chip for old again. I rebooted, and this time it brought up a usable desktop once again, but it behaved exactly as it had the precious few times I was previously able to get the live CD to boot on this machine - slow and sluggish. Subsequent re-boots failed to bring up a desktop and I’m right back where I started from. 
[/FONT]
        [FONT=Arial]So now I’m second guessing myself in a bunch of different ways. Do I have an intermittent problem with these memory chips locking down or connecting properly? When I started, I observed that all latches where securely in place. I had previously watched a video on changing these, but let’s be honest - a trained monkey could do this. I always made sure my alignment notches were lined up, inserted one end at a time, and pressed down gently until the latches clicked in place. Easy, peasy. Or do I have another hardware problem that is way above my pay grade to diagnose?  I should point out that at the end of it all, I popped in my trusty live CD of 10.10 and all was right with the world. Sometimes you get the bear, and sometimes the bear gets you.
[/FONT]

---

### Post by Javelin Dan on 2012-04-23
rsavage -

If you're still watching, I did try your suggestion in post #21 of this thread - no luck. After my initial command, it did go to a blank white screen. But after more than enough time to finish booting, the second command simply didn't take. I think it's probably time to let this thread die a natural death.

 I have sent my Ram back to where I bought it, and if they send me a new one and it works I'll submit a new post on the Lubuntu forum just to let you know it worked. If not, I may just have to resign myself to an unsupported version of 10.10 or possibly Debian 6 on this machine - that ran OK too. Thanks for trying.

---

### Post by rsavage on 2012-04-24
I can suggest a few things with your 11.04 install if you like.  Otherwise, you can install 10.04 lubuntu.  10.04 still has another year of support.

---

### Post by rsavage on 2012-04-24
I should of read my emails before replying. 12.04 is getting its kernel config changed.
 
See [https://lists.ubuntu.com/archives/kernel-team/2012-April/020013.html](https://lists.ubuntu.com/archives/kernel-team/2012-April/020013.html) .  It looks like the change won't make the ISOs, but will be available as a kernel update.

---

### Post by Javelin Dan on 2012-04-24
[FONT=Arial]I only stayed with this as an exercise in learning (I learned a lot!) and was willing to take each step to its next logical conclusion just for the educational value. However, it became only an exercise when I realized that this install, just like the last time I tried the mini install with the Xubuntu desktop, ran like a slug on this machine. It may well be because of the relatively low amount of RAM, but in its current state it was almost unusable. [/FONT]
 
[FONT=Arial]When I was given choices for partitioning, I chose “guided” but I don’t recall the option to erase the entire disk and install this one over it. This happened once before and I had two OS’s installed on the same drive. If I had a desktop I could check, but I can’t.[/FONT]
 
[FONT=Arial]I really want Lubuntu on this machine. That glitch I had the other day where it acted as if it was installed gave me a taste of the good life and I want it back. *If* I get a new RAM chip, and *if* it works, that will be the direction I’m headed.[/FONT]
 
[FONT=Arial]I don’t have many skills here, but one thing I do have is quite a bit of experience installing various flavors of Linux (primarily Puppy Linux) on old, underpowered PC junk. When not relying on skills to make an OS bend to your will, you pretty much have to evaluate what works out of the box. I’ve tried virtually dozens of distros on an old Dell Inspiron 8000 laptop of mine with 128 MB of RAM, and only two would run extremely well – Antix and Wary Pup 5.1.2. While most (not quite all) versions of Puppy would boot on this computer, only this one was fast out of the box and had no glitches. Lubuntu failed to launch.[/FONT]
 
[FONT=Arial]What I’m getting out of all this is that if you don’t have the skills of a code-writer (and I don’t), you have to rely on the natural match-up of a given distro (kernel) with your particular equipment. The Linux people do a marvelous job of trying to be all things to all people, but sometimes it just isn’t possible. I think this old G4 is just going to be cranky and limited in its compatibility. I’ll let you know if it decides to get along with anything I’m attempting here. [/FONT]

---

### Post by Javelin Dan on 2012-05-21
I finally got a 512 memory card that would boot this machine and now have 896 MB of Ram. I have successfully installed Lubuntu 12.04 Ppc. This box is still no speed demon, but it works. Now contemplating whether to max out the Ram to 1.5 GB to see if I can improve performance. I will mark this as solved.

---

