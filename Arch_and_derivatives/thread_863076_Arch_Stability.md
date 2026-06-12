---
title: "Arch Stability?"
date: 2008-07-18
forum: Arch and derivatives
---

### Post by CJ56 on 2008-07-18
Well I installed Arch a couple of weeks ago on a test hard drive & I like it. A bit of an effort to set up, but everything they say about it is true... a real pleasure to use...:)

So now I'm thinking about putting it on my 'proper' working 160Gb HDD and settling in for the duration. I'm not so crazy as to believe that Arch is the final version of Linux I'll ever use but it looks good so far.

My only question is about stability. I've come back from a week away, I do my -Syu update and a shedload of stuff comes through. This is all good, I know, keeps me right up to date, but you know what it's like with updates... I don't want to break a near-perfect system & have to fix it on account of a buggy new version of an application suddenly appearing. I'm not really a tinkerer (I'm supposed to be using this machine to make a living... ;) ) I just want it to keep going.

So how does Arch work out for you long term? Any stability/update problems? Or am I just looking for drawbacks where there aren't any?

---

### Post by morgan141 on 2008-07-18
I haven't had any huge problems with updates. I had a slight problem with one update which lost video playback but it was easily resolved by editing the xorg.conf. The problem was well documented on the forum too. From what I understand since the packages in arch are as vanilla as possible the vast majority of bugs are solved by the program developers. For me anyway this seems to be true :)

That said, I create an image of my arch install fairly regularly using partimage for this very reason. This is especially important with kernel updates where there is a risk of a kernel panic.

---

### Post by Barrucadu on 2008-07-18
I've been using Arch exclusively since March, with the testing and unstable repos enabled, and the only problems have been caused by me, ubdates have all been fine.

---

### Post by Rumor on 2008-07-18
> **CJ56 said:**
> 
So how does Arch work out for you long term? Any stability/update problems? Or am I just looking for drawbacks where there aren't any?

I've been using Arch for a couple years and am in the habit of doing -Syu once a week. I have never encountered any issues with stability. Since you control which repositories you enable, you can have as stable a system as you wish. Even with testing enabled, you shouldn't encounter any problems. You can run Arch with confidence. Even if something does develop a glitch, the Arch community is generally knowledgeable enough to help you around it.

---

### Post by chucky chuckaluck on 2008-07-19
i've only had one problem with an update. it was an update to spidermonkey that caused elinks to no longer work (elinks is in the 'extra' repo). i started a thread about it and some fine person came by to solve the problem. if there were such a thing as a 'perfect setup', then you would never need to update anything. in reality, today's 'perfect' is tomorrow's 'outdated'.

---

### Post by sujoy on 2008-07-19
arch has been rock stable for me, using it for the last 6 months. only once my xserver broke after a kernel upgrade, which i could fix myself in about a couple of minutes (xorg.conf and video drivers).

you just need to watch out for .pacnew files after an upgrade and .pacsave files after an uninstall.

---

### Post by Dr Small on 2008-07-19
Arch has been stable for me, except the one kernel panic I received for kernel26-2.6.25. Nothing else has broken, so I just don't upgrade anymore because of that problem kernel.

---

### Post by kpkeerthi on 2008-07-19
Unless you are using the Testing repository, you do not have to worry about Arch's stability. Unlike Debian Sid or Sidux, The 'core' packages get into the main repository after they undergo sufficient testing and are considered stable. 

Moreover, Arch packages does not include distro specific patches (like Ubuntu's) and are retained mostly in vanilla form released by the upstream owners. So bugs that may otherwise be introduced, due to distro specific patches, are minimal or non-existent.

I've been using Arch for about 9 months now, so far the only issue I faced was a minor VLC breakage due to a bad FFMPEG upgrade. But that was fixed almost instantly. 

Arch is very stable and like others have mentioned watch out for the important post install messages everytime you do **pacman -Syu**.

---

### Post by RedSquirrel on 2008-07-19
> **Dr Small said:**
> Arch has been stable for me, except the one kernel panic I received for kernel26-2.6.25. Nothing else has broken, so I just don't upgrade anymore because of that problem kernel.
When you say, "I don't upgrade anymore", do you mean the kernel or the entire system?

---

### Post by fwojciec on 2008-07-19
Kernel panics -- all the ones that I've had were easily dealt with by booting using a fallback image, or the kernel from an install cd, and then making sure that everything is correct in /etc/mkinitcpio.conf and regenerating the image with mkinitcpio -p kernel26.  It is important to look when images are generated to look for potential issues or anything out of the ordinary.  Unless there is some generic hardware incompatibility due to regression in the kernel itself one should be able to fix the cause of kernel panics easily.

Stability question -- I have Arch installed on two systems and it has always been perfectly stable for me.  I run [testing], because that way I get upstream bug fixes earlier.  There are no "stability" issues of any kind, though there obviously are glitches, known issues, and regressions that you have to live with, or occasionally patch yourself if they get on your nerves too much.  Every once in a while, especially with [testing] enabled, one might find it necessary to manually rebuild a package against a new set of libraries, but that's about as serious as issues get with Arch, at least for me.

---

### Post by Dr Small on 2008-07-19
> **RedSquirrel said:**
> When you say, "I don't upgrade anymore", do you mean the kernel or the entire system?
The entire system, because everything is dependant upon the newer kernel now, when I upgrade.

---

### Post by ODF on 2008-07-19
Very stable, testing and unstable repos are turned off of course.

But someone not familiar to linux should not use Arch in my opinion even if its reliable.

---

### Post by RedSquirrel on 2008-07-28
> **Dr Small said:**
> The entire system, because everything is dependant upon the newer kernel now, when I upgrade.

I've hesitated to get into this further, but what the heck. :D

So, your system is stable as long as you don't upgrade?

How can you stand to run a system you cannot keep up-to-date? Having packages with higher version numbers isn't necessarily a priority, but keeping on top of security fixes which might come with new packages is something that would be of concern (for me, anyway).

:confused:

---

### Post by Dr Small on 2008-07-28
> **RedSquirrel said:**
> I've hesitated to get into this further, but what the heck. :D

So, your system is stable as long as you don't upgrade?

How can you stand to run a system you cannot keep up-to-date? Having packages with higher version numbers isn't necessarily a priority, but keeping on top of security fixes which might come with new packages is something that would be of concern (for me, anyway).

:confused:
Updating breaks my system, so I can't. It's that simple.

---

### Post by cardinals_fan on 2008-07-28
If you update EVERY DAY, the system will probably be reasonably stable.  Nothing like RHEL or Slackware, but pretty stable.  The big problems come when you wait a month or two and then install a boatload of updates.

---

### Post by basenvironment on 2008-07-31
Does arch have a separate repo JUST for security updates?

---

### Post by Barrucadu on 2008-07-31
Nope

---

### Post by Vorian Grey on 2008-07-31
> **Dr Small said:**
> Updating breaks my system, so I can't. It's that simple.
I've always thought I might want to try Arch but now I'm not so sure. Not being able to update without breaking something is a major bummer. That really annoys me when Ubuntu manages to do it and I would probably be even more annoyed if I spend days and weeks learning Arch and it went belly up because of an update.

---

### Post by mips on 2008-07-31
> **Vorian Grey said:**
> I've always thought I might want to try Arch but now I'm not so sure. Not being able to update without breaking something is a major bummer. That really annoys me when Ubuntu manages to do it and I would probably be even more annoyed if I spend days and weeks learning Arch and it went belly up because of an update.

He has one specific problem with that kernel. Not everyone has it. Sorry but when it comes to update stability Arch beats Ubuntu hands down. There are many examples of ubuntu updates borking something like xorg etc. Nevermind trying to upgrade from one version of ubuntu to next via synaptic or apt-get.

If you experience a problem like this it is not that hard to roll back. He would most likely have to sit out this kernel version until the next one is available which hopefully addresses his issue.

You would be better of with something that does not get upgraded at all as I do not believe everything out there is 100% stable.

---

### Post by basenvironment on 2008-07-31
So, in arch, it isn't possible to update the rest of the system and not the kernel? 

Also, I like having a separate repo for security updates so that is another mark against arch for me.

---

### Post by morgan141 on 2008-07-31
> **basenvironment said:**
> So, in arch, it isn't possible to update the rest of the system and not the kernel? 

Yes it's very easy, all it requires is adding a single line to the /etc/pacman.conf and it will ignore updates to the kernel (or any other package you choose). The problems occur when one updates packages which are dependent on the newer package, then I'm not too sure what happens. Pacman will probably just update whatever it can but to be honest I've never had to do it so I don't know.

---

### Post by Dr Small on 2008-07-31
> **Vorian Grey said:**
> I've always thought I might want to try Arch but now I'm not so sure. Not being able to update without breaking something is a major bummer. That really annoys me when Ubuntu manages to do it and I would probably be even more annoyed if I spend days and weeks learning Arch and it went belly up because of an update.
Mips is right. I am only having kernel panics for this certain kernel. I may try it out next time around, or I may just sit and be content with my working system :) I'm not much of one for change. But anyhow, alot of people updated and didn't have problems, so don't let my problem bother you. :)

---

### Post by chucky chuckaluck on 2008-07-31
> **Dr Small said:**
> Mips is right. I am only having kernel panics for this certain kernel. I may try it out next time around, or I may just sit and be content with my working system :) I'm not much of one for change. But anyhow, alot of people updated and didn't have problems, so don't let my problem bother you. :)

do you have any idea why you're having the trouble?

---

### Post by mips on 2008-07-31
> **basenvironment said:**
> So, in arch, it isn't possible to update the rest of the system and not the kernel? 

Also, I like having a separate repo for security updates so that is another mark against arch for me.

Then stick with ubuntu or whatever else works for you.

---

### Post by basenvironment on 2008-07-31
> **morgan141 said:**
>  The problems occur when one updates packages which are dependent on the new kernel
I have never known a kernel to be dependent on other packages or vice versa???

---

### Post by basenvironment on 2008-07-31
> **mips said:**
> Then stick with ubuntu or whatever else works for you.

obviously.... :lolflag:

Just offering my 2 cents on the topic.

---

### Post by morgan141 on 2008-07-31
> **basenvironment said:**
> I have never known a kernel to be dependent on other packages or vice versa???

My apologies I meant packages in general, not a kernel specifically. I'm not quite sure why I wrote that... Technically speaking the kernel is dependent on the likes of mkinitcpio and stuff but you're quite right.

---

### Post by MONODA on 2008-07-31
> The big problems come when you wait a month or two and then install a boatload of updates.
why would that cause problems?

---

### Post by cardinals_fan on 2008-07-31
> **MONODA said:**
> why would that cause problems?
Updates tend to cause small amounts of breakage.  Many updates at once magnify that breakage.

---

### Post by kevinmchapman on 2008-08-01
> **cardinals_fan said:**
> The big problems come when you wait a month or two and then install a boatload of updates.

I think that is an oft-repeated fallacy. The main problem of infrequent updates is updating all the config files from the pacnew files - but it is the same work, just more of it in one go.

You could also argue that by waiting a while you will jump a version for some packages and therefore miss some of the potential minor breakages...

I may report back in a month. I have been running an Arch install on a box at a house without internet since April and am thinking about bringing it home temporarily to update.

---

### Post by cardinals_fan on 2008-08-01
> **kevinmchapman said:**
> I think that is an oft-repeated fallacy. The main problem of infrequent updates is updating all the config files from the pacnew files - but it is the same work, just more of it in one go.

My point exactly.  I'm more likely to update them properly when there are only a couple files to deal with.

---

