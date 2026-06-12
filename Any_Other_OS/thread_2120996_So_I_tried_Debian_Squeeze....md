---
title: "So I tried Debian Squeeze..."
date: 2013-02-28
forum: Any Other OS
---

### Post by ozz_man on 2013-02-28
What a pain in the butt that's been! ...half of the hardware doesn't work right... :(

I spent so much time fixing my network issues and now I have sound issues.  It's been such a pain that I'm probably going to remove it from that drive.  I already use Ubuntu/RedHat/CentOS but Debian has been the biggest pain so far.

Has anyone else had all these issues? (my hardware is brand new btw)

---

### Post by Dry Lips on 2013-02-28
I haven't got terribly much experience with Debian, I've only tried it a couple of times. However, my main impression is that it isn't as "desktop ready" as for instance Ubuntu. It's more of a tinkerers desktop. When I tried it, it did *not* work out of the box. However, sometimes you just have bad luck, and your problems aren't necessarily the fault of the distro.

---

### Post by ozz_man on 2013-02-28
Yeah, I'm not blaming anyone but it's def been a pain.  I had to work with some developers from Qualcomm to figure out what was wrong with the network driver (which worked perfectly well with CentOS) only to figure out my soundcard isn't working now. ugh!

---

### Post by Adam_GUI on 2013-02-28
Debian Squeeze is considered "stable".  I feel more comfortable calling it "old".
If you needed continued support for an older machine, I'd consider Debian Squeeze.
You may have had better support upgrading to or installing Debian Wheezy "testing".
There's a giant section on Upgrading from Squeeze at Debian.org [here.]("http://www.debian.org/releases/testing/i386/release-notes/ch-upgrading.en.html")

There's a more to-the-point upgrade guide over at DoDebian.  [Here.]("http://dodebian.blogspot.com/2012/02/upgrade-guide-edition-2-start.html")

Or, the official install-from-base directions [straight from the horse's mouth.]("http://www.debian.org/devel/debian-installer/")

Debian has some more err...  traditional linux views when it comes to software.  You'll have to add third-party repositories for things like Firefox and Thunderbird.
Right now, Linux Mint Debian Edition is based on Debian Testing.  It may be better worth your time to give it a shot instead of pure Debian.  [Found here.]("http://www.linuxmint.com/download_lmde.php")

---

### Post by pythonscript on 2013-02-28
I'll second Linux Mint Debian Edition (LMDE). I've found that it offers a good mix of stability and rolling updates because they push out a frozen, tested copy of Debian Testing's repositories on a semi-rolling basis.

If you really want to tinker, run Arch for a while...

---

### Post by ajgreeny on 2013-02-28
I think your problem is probably down to the fact that debian is an unadulterated FOSS operating system with no proprietary packages available from the default repos.  If you want or need proprietary drivers for wireless or graphic cards, you have to work and search a fair bit harder than you do in Ubuntu.

I tried the LMDE, ie, Debian Edition version of Mint when it first appeared, thinking it would be just as easy as normal Mint, but it certainly was not the case, so I quickly gave up on it and went back to Mint, and then from that back to Ubuntu, which for some reason ran faster than Mint on my hardware.

Ubuntu also seems more "pure", though I am not totally sure I know what I mean by that comment; it's just a personal choice thing.

---

### Post by kabukiM0n0 on 2013-02-28
I've been running a distro based on Debian Wheezy for a little bit now, and yes, it does get complicated to set up certain features out of the box - but the list does continue on after that. I think it's just a different way of doing things, that does some getting used to. Hell I don't even come close to understand what I'm doing most of the time, but it runs very well on my system. 

Even though this is not the first time I've tried Debian, it is the longest I have stuck with it - it comes down to how much patience you have really. It either sinks in, you learn it and keep moving (to more complications) or you bin it and go back to basic everything functioning properly out of the box buntu (no offense buntu users)

When it comes down to it - from the little I know about Debian these would be the key points before even attempting to install and run it. 
Do I have enough time to spend trying to figure this, that and the other out?
Am I prepared to take a step deeper into the Linux world? Do I wish to (attempt) learn it?
How much patience do I have? (before I throw my system out the window) 
Am I sure I have this much time to spend trying to figure out even the most basic things?


And of course it all realy depends on how deep you want to go. If you just need a basic system and don't want to tinker with it. That's pretty easy (once you know how of course) but if you do like to play around and see what you are capable of doing, well prepare to feel frustration at it's finest. 


I do wonder sometimes (offtopic) how must it feel like to set up Arch the first time (without superior linux knowledge) because I had a hard time with Debian and yet Arch is meant to be infinately harder.

---

### Post by pythonscript on 2013-02-28
> **ajgreeny said:**
> I tried the LMDE, ie, Debian Edition version of Mint when it first appeared, thinking it would be just as easy as normal Mint, but it certainly was not the case, so I quickly gave up on it and went back to Mint, and then from that back to Ubuntu, which for some reason ran faster than Mint on my hardware.

Ubuntu also seems more "pure", though I am not totally sure I know what I mean by that comment; it's just a personal choice thing.

I had a similar experience with LMDE when I first tried it (around Update Pack 4, I believe). Somewhere along the pipeline before Update Pack 5/6, though, a lot of the kinks got worked out for my hardware, so the newer releases run quite well. 

Personally, I think that illustrates a major benefit to the Linux community. You prefer Ubuntu, so you use Ubuntu. I prefer LMDE, so I use LMDE. Others might prefer <distro>, so they use <distro>. At the risk of sounding trite and overusing a word that's overused a lot already, I enjoy the freedom.

> **kabukiM0n0 said:**
> 
I do wonder sometimes (offtopic) how must it feel like to set up Arch the first time (without superior linux knowledge) because I had a hard time with Debian and yet Arch is meant to be infinately harder.


I don't know how it feels to set it up without *any* Linux knowledge, but when I used Arch for about a year, I didn't possess a great deal of knowledge, but thankfully I could follow the wiki and that worked out fairly well. Patience was a major part of, though, because although the setup wasn't too difficult, it took me several days before I had a system working to my liking. I found package availability lacking, even with the AUR (I could always compile from source, but I mean in the standard repos), but it was nice to be several major versions ahead of distros like Debian/Ubuntu. Can't beat living on the bleeding edge!

---

### Post by ozz_man on 2013-02-28
> **Adam_GUI said:**
> Debian Squeeze is considered "stable". I feel more comfortable calling it "old".
If you needed continued support for an older machine, I'd consider Debian Squeeze.
You may have had better support upgrading to or installing Debian Wheezy "testing".

Problem is that I want a solid, long-term stable release (for this particular case)... but it seems like you have to have old hardware to get Debian (stable) working easily.

I've heard a lot of ranting and raving about Linux Mint and their distros, might give them a shot sometime.

I'm an engineer, so I don't want to spend weeks trying to configure my tool... I want it to work and then I can spend weeks fixing my own software...lol

---

### Post by CharlesA on 2013-02-28
You could try Lucid - the server version is supported for another 2 years. I haven't had any problems with Squeeze. I've got it running the wiki at work.

Friendly note: The multiquote button is your friend, as is the edit button. ;)

---

### Post by MadmanRB on 2013-02-28
Debian is not as good in some areas as ubuntu, its just how the kernel is.

---

### Post by ozz_man on 2013-02-28
> **CharlesA said:**
> 
Friendly note: The multiquote button is your friend, as is the edit button. ;)
I don't get on the forums much. :)

When I chat with developers I mostly use a different website that has a completely different layout.

---

### Post by codingman on 2013-02-28
I'm currently distro jumping, and so far I am very happy with Netrunner, or maybe that's just because every other KDE distro out there has a billion unused applications and eye-candy hainging around every corner. I was wondering if anyone here has tried Crunchbang. I wanted to know if it was worth trying.

---

### Post by UltimateCat on 2013-03-01
I've been running Debian Stable for about 8 months now and yes, at first I had the network issue and the sound issue like you.

However after I solved those 2 issues I have never encountered any more problems.

Debians sound is Alsa by default- -
Try this:
Open the mixer and raise up the PCM and the Master
You can also try running:
```
alsa+l init

```
Add yourself to the audio group log out and log back in again.
<adduser yourname audio>
Open the terminal:
```
alsamixer

```
You'll see a black/grey background with multiple columns. Raise all columns all the way up, mute and un-mute each column.
Do a sound test which is file 'noise.wav'
{oo} means un-muted and {mm} means muted- This worked for me-

Make sure you have the Linux Sound Architecture Driver

And the internet connection problem I had to edit my interfaces file.
Check in on your interfaces file and see that the arguments are what you want. In my case, I had to comment out the 'Wired' arguments in order for my wireless to work.

Hope this helps

---

### Post by Peripheral Visionary on 2013-03-01
> **codingman said:**
>  I was wondering if anyone here has tried Crunchbang. I wanted to know if it was worth trying.

My dance teacher loved Crunchbang back when it was built from an Ubuntu base.  When they switched to the Debian base it became about as troublesome on his laptop as Debian had been, with sound and network issues.  If someone makes an "UbuBang" or a "CrunchBuntu" I would have to try it!

---

### Post by mamamia88 on 2013-03-02
What exactly is your hardware and what doesn't work right?  My experience has been the only issues i ever had with hardware is having to enable non-free and download my wireless driver over Ethernet.

---

### Post by malspa on 2013-03-02
> **MadmanRB said:**
> Debian is not as good in some areas as ubuntu, its just how the kernel is.

And Ubuntu is not as good in some areas as Debian. That's why I run both.

> **Peripheral Visionary said:**
> My dance teacher loved Crunchbang back when it was built from an Ubuntu base.  When they switched to the Debian base it became about as troublesome on his laptop as Debian had been, with sound and network issues.

It seems that you paid very close attention to your dance teacher's Linux experiences.

---

### Post by iamkuriouspurpleoranj on 2013-03-02
Debian's primary worth is its stability and this is why people love it for servers. Of course, that stability comes at a price. However, if you're willing to forego 100% stability Debian 7 testing aka Wheezy is as good in terms of hardware compatibility as Ubuntu in my experience.

Debian and Ubuntu complement each other but it would be a shame for Debian to simply become the Ubuntu that's not Ubuntu. Sometimes, it's forgotten that the Debian social contract also includes a commitment to quality. So the answer to when Debian 7 will be released is "when it's ready". That should be the only answer for Debian.

---

### Post by mamamia88 on 2013-03-02
> **iamkuriouspurpleoranj said:**
> Debian's primary worth is its stability and this is why people love it for servers. Of course, that stability comes at a price. However, if you're willing to forego 100% stability Debian 7 testing aka Wheezy is as good in terms of hardware compatibility as Ubuntu in my experience.

Debian and Ubuntu complement each other but it would be a shame for Debian to simply become the Ubuntu that's not Ubuntu. Sometimes, it's forgotten that the Debian social contract also includes a commitment to quality. So the answer to when Debian 7 will be released is "when it's ready". That should be the only answer for Debian.

Not really a big risk.  Debian Wheezy should be released any time now.  Debian releases new versions roughly every 2 years and it's been about that since the last one.   It's been in freeze for awhile and it's in bug squashing mode right now.   Like I said the only hardware compatibility problems I've had have been due to Debian's strict adherence to free software.  So they don't include stuff like non free drivers by default. Adding the word non-free in sources.list and running sudo apt-get update && sudo apt-get install nameofnonfreedriver fixes that easily enough.  Is it kind of unconvenient to plug my laptop into the router to download my wifi driver? Sure it is but I only have to do it once and it takes 5 minutes longer than it would in Ubuntu.  It's a lot less annoying though than fixing something in Ubuntu because it was shipped before it was ready though.

---

### Post by cwsnyder on 2013-03-02
In my experience, you pay for stability with a lack of proper drivers.  CentOS/RedHat are supported for a long time, but if the version is more than 2 years old (like Debian Squeeze is), the kernel supported usually does not have support for all of the latest whiz-bang hardware.  Go with Wheezy for now if you have new hardware and you are more likely to have proper hardware support, although you may have to do some Internet searching to find the proper drivers.  If you want support equivalent to RedHat/CentOS, you could also try one of the *BSDs, but be prepared for even worse hardware support than with Debian stable.

I have been running Ubuntu on and off since 7.10 Gutsy until the change was made to Unity (no proper support for my hardware).  I still run Xubuntu or Lubuntu in VirtualBox, now with Raring (13.04) in testing.  I run Debian as my stable backup system, usually on stable, although I usually switch over about the time of the feature freeze to check for incompatibilities, and have since Sarge (4.0) was stable and Lenny (5.0) was testing.  I have been running LMDE as my trial and (mostly) working distro (again, usually with Xfce).  My present third non-virtual distro of choice is Bodhi, which is based on Ubuntu LTS, so it is also only upgraded about once every 2 years.

---

### Post by Peripheral Visionary on 2013-03-02
> **malspa said:**
> 
It seems that you paid very close attention to your dance teacher's Linux experiences.

He used that laptop in dance class to play music from so he could slow the music down while teaching a routine and gradually speed it up until we could all do it full speed.  I thought it was all dark and sinister looking but it had a funny name - Crunchbang Linux.  

That's when I learned that there are many different Linux OSes to choose from.  He had "Robin's Remix" on the computer at the dance school, which was a really simple Windows-98-looking desktop.  I learned from that, that you can make your own Linux OS just the way you want it.

All I did was ask.  Robin loved to share his own journey with others, whether it was dance, or computer stuff, choral singing, or his love of his religion.  He was passionate about everything he did, and it was just contagious.  There are at least a dozen new Linux users from his dance class, and how many more from his church and college classmates he turned on to Linux.  Every one of us shared his "adventures in Linux."  You couldn't help it.

---

### Post by mips on 2013-03-03
Are you talking about [COLOR=#282828][FONT=helvetica]Robin Anderson aka DixieDancer?[/FONT][/COLOR]

---

### Post by iamkuriouspurpleoranj on 2013-03-03
> **mamamia88 said:**
> Not really a big risk.  Debian Wheezy should be released any time now.  Debian releases new versions roughly every 2 years and it's been about that since the last one.   It's been in freeze for awhile and it's in bug squashing mode right now.   Like I said the only hardware compatibility problems I've had have been due to Debian's strict adherence to free software.  So they don't include stuff like non free drivers by default. Adding the word non-free in sources.list and running sudo apt-get update && sudo apt-get install nameofnonfreedriver fixes that easily enough.  Is it kind of unconvenient to plug my laptop into the router to download my wifi driver? Sure it is but I only have to do it once and it takes 5 minutes longer than it would in Ubuntu.  It's a lot less annoying though than fixing something in Ubuntu because it was shipped before it was ready though.

*Roughly* every 2 years. My point was only that they release when ready and not before. There are still more than 100 bugs to fix before it can go live.

I know how to get the multimedia repository but had no joy with Squeeze on one laptop for the headphones. It's all fixable stuff but after a while I figured the time investment wasn't worth it, so I just installed Wheezy. It's a laptop I use as a radio/stereo so the headphones working is important.

Honestly, I would only run Squeeze now a) for a server b) out of respect for the Debian project as 6 a.k.a. Squeeze is still the most recent official Debian **release**.

---

### Post by malspa on 2013-03-03
> **mips said:**
> Are you talking about [COLOR=#282828][FONT=helvetica]Robin Anderson aka DixieDancer?[/FONT][/COLOR]

Yeah; and I guess it's good to see that "Robin/DixieDancer" *yet lives*, through "Peripheral Visionary," in a way. Lots of interesting posts and insight here and at other Linux forums. Hm. Anyway, back on topic, for me at least...

> **iamkuriouspurpleoranj said:**
> There are still more than 100 bugs to fix before it can go live.

Even so, I installed Wheezy back in September and it's been so problem-free that it's almost boring. On three different computers, actually.

---

### Post by iamkuriouspurpleoranj on 2013-03-03
> **malspa said:**
> Yeah; and I guess it's good to see that "Robin/DixieDancer" *yet lives*, through "Peripheral Visionary," in a way. Lots of interesting posts and insight here and at other Linux forums. Hm. Anyway, back on topic, for me at least...



Even so, I installed Wheezy back in September and it's been so problem-free that it's almost boring. On three different computers, actually.

That's because Debian sets a high standard for itself. Wheezy is totally useable but it's still not "ready" according to its own standards. You don't get a "rock solid" reputation for nothing.

My point is that when Ubuntu issues a release, you expect it to be bug-free and are disappointed when it isn't because you've been led to expect a bug-free release by its pitch.

Debian doesn't do this. You can download and install the pre-release version - in fact it's essential to its development that people do this - and yes right now Wheezy is more or less stable and arguably more stable than Ubuntu 12.04. However, it's still not a **release** so any bugs noticed should be fed back into the project and not be seen as faults with the final product. I'd hate for people running a beta to become disillusioned with "buggy Debian".

---

### Post by snowpine on 2013-03-03
Brand new hardware + 2 year old distro = problems no matter how good the distro was 2 years ago. :)

Just burn a bunch of Live USB's and find the distro that works the best for you. I bet if you'd tried Squeeze live, you could have quickly eliminated it as a possibility and saved yourself a lot of aggravation. If you are looking for a debian-based distro that "just works" then why not give Mint a try (13 is LTS) or (shocking!) Ubuntu? 

I miss DixieDancer. :(

---

### Post by mips on 2013-03-03
> **iamkuriouspurpleoranj said:**
> That's because Debian sets a high standard for itself. Wheezy is totally useable but it's still not "ready" according to its own standards. You don't get a "rock solid" reputation for nothing.


+1 I would be quite comfortable to use Wheezy right now even though it's still not 'ready' according to debian standards. I downloaded Crunchbang Waldorf (Based on Wheezy) the other day and I think it's gonna go on my old laptop.

---

### Post by Cheesemill on 2013-03-03
> **mips said:**
> +1 I would be quite comfortable to use Wheezy right now even though it's still not 'ready' according to debian standards. I downloaded Crunchbang Waldorf (Based on Wheezy) the other day and I think it's gonna go on my old laptop.

+1

I've been using #! Waldorf for about 6 months now on my old laptop and haven't had a single issue.

Crunchbang is always my go to distro for older hardware.

---

### Post by malspa on 2013-03-05
> **iamkuriouspurpleoranj said:**
> My point is that when Ubuntu issues a release, you expect it to be bug-free and are disappointed when it isn't because you've been led to expect a bug-free release by its pitch.

I don't have that expectation of Ubuntu. With software in general, "bug-free" usually only means no bugs have been found yet, seems to me.

---

### Post by lykwydchykyn on 2013-03-06
I wrote this a while back, it might be helpful here:
[Debian for Ubuntu people](http://www.alandmoore.com/blog/2012/05/17/debian-for-ubuntu-people/)

I love Debian, but I see it as kind of a "proto-distribution":  a base for other things.  I think people make too much of its difficulties, though.  Proprietary hardware?  Add the non-free repo and install the firmware and drivers.  Yes, it takes some reading, but it's not *hard*.

FWIW, though, I only use it on servers and older hardware.

---

### Post by buzzingrobot on 2013-03-07
Old + bugfixes = stable.  New software, and new releases, aren't added to Debian Stable. That's what keeps it stable.

So, hardware that's younger than the current Stable release might have problems.  

RHEL/CentOS is of similar vintage.  Red Hat also focuses on bugfix updates and avoids adding new software and new releases to RHEL.  It does, though, backport many new kernel features into the RHEL kernel which might mean it is more amenable to newer hardware than Debian Stable. I'm not familiar with how Debian handles the kernel in a Stable release.

---

### Post by cortman on 2013-03-07
> **codingman said:**
> I'm currently distro jumping, and so far I am very happy with Netrunner, or maybe that's just because every other KDE distro out there has a billion unused applications and eye-candy hainging around every corner. I was wondering if anyone here has tried Crunchbang. I wanted to know if it was worth trying.

I use Crunchbang exclusively on all my machines. I love the distro and especially that it's Debian based.
@OP- Debian does occasionally require a little more initial setup- it's free as in freedom, and built from the ground up for stability. If you want everything done for you, you're going to sacrifice some simplicity (and therefore) stability as well. At the risk of sounding like a snobby Debian user, it's not for someone who can't be asked to help themselves. :)
I've found that it's been worth the extra effort I put into it.

---

