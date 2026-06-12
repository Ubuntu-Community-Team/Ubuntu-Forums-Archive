---
title: "Trying to learn Debian"
date: 2011-05-25
forum: Any Other OS
---

### Post by ratcheer on 2011-05-25
A friend on another forum has convinced me to try Debian. Boy, is it a pain!

The first thing I am trying to do is install the nVidia proprietary driver in the hope that the ugly, fuzzy display will look better. So far, everything I have tried has failed. I am trying to follow the instructions in [http://wiki.debian.org/NvidiaGraphicsDrivers#Overview](http://wiki.debian.org/NvidiaGraphicsDrivers#Overview)

I was able to successfully add my username to the sudo group. But, when I gave it the advanced setting to "mount filesystems in the user space", I still cannot mount my external USB drive using the file manager GUI.

This is all very frustrating and I don't know how long I will be able to pursue it. Maybe Ubuntu is too easy and I have gotten too lazy. I used to be halfway decent administering Solaris, HP-UX, and AIX systems at work.

Tim

---

### Post by snowpine on 2011-05-25
Hi Tim, I'm looking at the tutorial you linked to:

[http://wiki.debian.org/NvidiaGraphicsDrivers#Overview](http://wiki.debian.org/NvidiaGraphicsDrivers#Overview)

And I see no mention of "add username to the sudo group" or "mount filesystems in the user space."

Therefore I am extremely confused about what you've done so far and which step of the tutorial you're stuck at. Not sure how to help you... 

If you want to have success with Debian you need to tackle your problems one at a time in a methodical process. Also I highly recommend using the Debian forums (rather than Ubuntu forums) for support: [http://forums.debian.net](http://forums.debian.net)

---

### Post by tgalati4 on 2011-05-25
You really appreciate Ubuntu after trying to configure Debian.

---

### Post by malspa on 2011-05-25
Hang in there, though -- and keep good notes. Debian's great once you get it set up. Actually, my first time installing it went more smoothly than I was expecting; the next few times, even better. No way is it as quick and easy to install and set up as Ubuntu, but it's pretty much smooth sailing for a couple of years after that. Worth it, IMHO.

---

### Post by wweeks on 2011-05-25
Debian rocks, I much prefer it over Ubuntu because it has better hardware support for old computers. :) Kudos for trying it out!

---

### Post by malspa on 2011-05-25
Pros and cons each way. I like both, so I keep them both installed.

---

### Post by ratcheer on 2011-05-25
> **snowpine said:**
> Hi Tim, I'm looking at the tutorial you linked to:

[http://wiki.debian.org/NvidiaGraphicsDrivers#Overview](http://wiki.debian.org/NvidiaGraphicsDrivers#Overview)

And I see no mention of "add username to the sudo group" or "mount filesystems in the user space."

Therefore I am extremely confused about what you've done so far and which step of the tutorial you're stuck at. Not sure how to help you... 



Sorry if that was confusing. Yes, that tutorial is only about installing the nvidia drivers. The mount problem is just general frustration.

Tim

---

### Post by unknownPoster on 2011-05-25
> **tgalati4 said:**
> You really appreciate Ubuntu after trying to configure Debian.

Honestly, I find them about the same on ease of use. But then again, I'm not exactly new to Linux.

---

### Post by wojox on 2011-05-25
> **ratcheer said:**
> Sorry if that was confusing. Yes, that tutorial is only about installing the nvidia drivers. The mount problem is just general frustration.

Tim

Is ConsoleKit installed. I had that problem in Arch.

---

### Post by Arthur_D on 2011-05-25
Hm, I had no problems with enabling the right repo(s), and then I could just apt-get nvidia-current like on Ubuntu.

---

### Post by galacticaboy on 2011-05-25
This may not be relevant, but I had to add my two cents. Debian based Linux OS's to me, are the most easiest to use of them all. When it comes to others like Gentoo, Slackware, Fedora (Fedora is complicated, but I find it the second easiest), and others, they are all complicated to me, especially when you have to start working with .rpm and other file types. .deb to me is super easy.

---

### Post by ratcheer on 2011-05-25
> **Arthur_D said:**
> Hm, I had no problems with enabling the right repo(s), and then I could just apt-get nvidia-current like on Ubuntu.

Hmmm. So, which one is the right one? Never having worked with Debian, I have no idea. My instructions told me to enable contrib and free, so that is all I knew to do.

Anyway, I'm off to try Fedora, now. I may try Debian again later, but for now it is a PITA.

Tim

---

### Post by krapp on 2011-05-25
Considering your resume your difficulties with Debian are puzzling.

---

### Post by ratcheer on 2011-05-25
> **krapp said:**
> Considering your resume your difficulties with Debian are puzzling.

I feel the same way. I follow the documented instructions to the letter, but then the system will not work. Just a black screen with a blinking cursor.

I gave up on Debian and installed Fedora 15, this afternoon. The instructions to install the nvidia driver were almost as complicated as those for Debian, but they worked perfectly the first time. Gnome 3 on Fedora 15 is a real beauty.

So, is it me or is it Debian?

Tim

---

### Post by krapp on 2011-05-25
Well if you followed the Debian wiki to the letter it's most certainly the wiki. I've only ever tried to install ATI proprietary drivers and the wiki pages for those were accurate and easy to follow.

---

### Post by Timmer1240 on 2011-05-25
I installed Mint Debian it WAS harder to get all set up and get the video card drivers installed and printer to work than in Ubuntu but well worth it.Didnt hve any trouble with reaching my external drive.I imagine Debian itself would be a little harder to get setup.Google is always my friend I can usually find some answers good luck with it!

---

### Post by ratcheer on 2011-05-26
I am marking this thread as Solved because I have given up on Debian and installed Fedora 15 to my testing partition. The instructions to install the proprietary nvidia driver into Fedora were almost as complex as those for Debian, but with a huge difference - they worked!

I must say that Fedora 15 is very nice. I think I still prefer Ubuntu, but the default Gnome 3 desktop in Fedora is excellent.

I suppose Ubuntu has made me lazy, leading me to expect more from a desktop OS. I am too old to waste all my time having to perform arcane configuration for every little thing.

Thanks, everyone.

Tim

---

