---
title: "Should I install Linux?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by sangram on 2007-08-27
Hi, 

My first post, so hi everyone - I'm from India.

This is probably a stupid post, I'm basically looking for a few basic answers before I jump in and install Linux on a target machine.

I'm not a pure Linux noob, I did install Mandrake 9.0 about five years ago but that was for a lark - never got down to using it at all. But I'm not daunted by it, at least not yet.

I need a music production studio built from the ground up with Linux, so far I'm thinking Ubuntu Studio. I have no programming knowledge, but am pretty good at tech things, since I build PCs myself.

I already have all the hardware. The machine will be based on an AMD64 3200+ (older processor) and nforce3 chipset with 1GB PC3200 RAM and about 200-240 GB of disk space, split over a couple of disks. Plus a Delta66 for an interface, which I read is well-supported on Linux, and an nVidia FX5200, which I know has good support (right?)

Reason for the move is primarily cost and stability/latency. I am still at the bottom end of the learning curve as far as editing and sequencing software is concerned, so I could pick up new UIs and capabilities - not yet fixated on software. I have some very basic questions. I thank you in advance for reading my long post and taking the time to answer them.

1. Which flavour of Ubuntu is right for me? I'm currently downloading the Ubuntu Studio version but it looks like it's only available in 32-bit. Will the 64-bit version be much better for me?

2. If I do get the 64-bit, will I need to be patching the kernel using RT (I assume that means real-time), and is there a walkthrough that shows me how to do that? 

3. What about sound support in 64-bit versus 32-bit? I was hoping that my card worked out of the box, but just in case I've already downloaded the OSS packages. I need full support though I'm not used to anything apart from WDM and ASIO.

4. I had installed the 64-bit XP when it was in public beta, and 32-bit apps ran fine on it for the most part, but drivers were somewhat wonky. In a 64-bit Ubuntu, can I run 32-bit apps, or do the apps also need to be 64-bit?

5. This machine will not have an internet connection. Is that a deal breaker? Can we still downlaod RPMs the old-fashioned way and install them manually? Doing that from another machine will not be a problem.

6. Is there some place where I can see a list of 'bundled' packages for Ubuntu (all versions)? I've been searching and while there are some summaries, I can't see anything conclusive. I have downloaded a lot of basic install info for Ubuntu and Ubuntu Studio, so I think the install would be pretty painless.

7. Finally, is there a way to mount and see my NTFS partitions and drives out of the box, or do I have to manually install the linux-ntfs packages? I have a lot of my data on those drives.

8. Last (really), is there a way to carry over my Adobe Audition projects into Ubuntu seamlessly, or do I have to remix everything with new plugins?

Thanks for the attention.

Regards

Sangram

---

### Post by LaRoza on 2007-08-27


Hi! Yours is a long post, so I might miss something, but others will get it!

0. No matter what Ubuntu you get, you can get everything the others have. (If you get Ubuntu you can install KDE with "sudo aptitude install kubuntu-desktop) 32 will work fine, and may be better, at least for now.

1. I would recommend the 32 bit, for now.

2. n/a

3. 32 bit works fine on 64 bit, and sometimes better.

4. Ubuntu uses debs, not RPM, you can download the seperately, there is a guide for it, but I don't remember the address, I or someone else will get back to you.

5. There are a lot of packages, and some are not installed, but are on the cd so you can install them after. What packages are you looking for?

6. ntfs-32g *might* be on the cd, so you can install it from there, others will clarify.

7. don't know, not familar with that

---

### Post by Hobo Joe on 2007-08-27
> **sangram said:**
> Hi, 

My first post, so hi everyone - I'm from India.

This is probably a stupid post, I'm basically looking for a few basic answers before I jump in and install Linux on a target machine.

I'm not a pure Linux noob, I did install Mandrake 9.0 about five years ago but that was for a lark - never got down to using it at all. But I'm not daunted by it, at least not yet.

I need a music production studio built from the ground up with Linux, so far I'm thinking Ubuntu Studio. I have no programming knowledge, but am pretty good at tech things, since I build PCs myself.

I already have all the hardware. The machine will be based on an AMD64 3200+ (older processor) and nforce3 chipset with 1GB PC3200 RAM and about 200-240 GB of disk space, split over a couple of disks. Plus a Delta66 for an interface, which I read is well-supported on Linux, and an nVidia FX5200, which I know has good support (right?)

Reason for the move is primarily cost and stability/latency. I am still at the bottom end of the learning curve as far as editing and sequencing software is concerned, so I could pick up new UIs and capabilities - not yet fixated on software. I have some very basic questions. I thank you in advance for reading my long post and taking the time to answer them.

1. Which flavour of Ubuntu is right for me? I'm currently downloading the Ubuntu Studio version but it looks like it's only available in 32-bit. Will the 64-bit version be much better for me?

2. If I do get the 64-bit, will I need to be patching the kernel using RT (I assume that means real-time), and is there a walkthrough that shows me how to do that? 

3. What about sound support in 64-bit versus 32-bit? I was hoping that my card worked out of the box, but just in case I've already downloaded the OSS packages. I need full support though I'm not used to anything apart from WDM and ASIO.

4. I had installed the 64-bit XP when it was in public beta, and 32-bit apps ran fine on it for the most part, but drivers were somewhat wonky. In a 64-bit Ubuntu, can I run 32-bit apps, or do the apps also need to be 64-bit?

5. This machine will not have an internet connection. Is that a deal breaker? Can we still downlaod RPMs the old-fashioned way and install them manually? Doing that from another machine will not be a problem.  [http://www.getdeb.net/](http://www.getdeb.net/)

6. Is there some place where I can see a list of 'bundled' packages for Ubuntu (all versions)? I've been searching and while there are some summaries, I can't see anything conclusive. I have downloaded a lot of basic install info for Ubuntu and Ubuntu Studio, so I think the install would be pretty painless.

7. Finally, is there a way to mount and see my NTFS partitions and drives out of the box, or do I have to manually install the linux-ntfs packages? I have a lot of my data on those drives.

8. Last (really), is there a way to carry over my Adobe Audition projects into Ubuntu seamlessly, or do I have to remix everything with new plugins?

Thanks for the attention.

Regards

Sangram

Hello, and welcome. I'll answer your questions as well as I can.

1. While I'm not positive, I think that Ubuntu studio does have a 64 bit version. I personally think 64 bit is much better than 32, but that's just me.

2. I highly doubt you'll need to do that.

3. Hardware upport in 32bit and 64bit is nearly identical. 

4. Windows 64 bit was a flop because of bad support and terrible drivers. In Ubuntu, nearly every single program has a 64 bit version. And in the few cases that don't, you can just compile them.

5. While it would be better to run on a internet connection, it's not totally necessary. Yes, it's still possible to download the files manually.

6. [http://packages.ubuntu.com/feisty/](http://packages.ubuntu.com/feisty/)

7. You can see NTFS partitions out of the box, however, if you want to edit them, you have to download a driver.

8. I'm not really familiar with that program, and a lot depends on how they are saved. But I would say that you probably could do it.

---

### Post by scrooge_74 on 2007-08-27
Hi, nice list you got there.

For what I can help, you can use 64 bit no problem, I read here about 32 bits apps been use with 64 bit system in those few cases where there is not. 

Lates editions of Ubuntu will read from NTFS, for writting to them you just need to check the [HOWTO]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs+driver+install")

You can download .deb packages (RPM is for Red Hat) manually you just may need to download other packages asked because of their dependencies.  If you can download the DVD edition you will get all package as far as I know.

The package list I can't find it, so I give you the link for the Debian list which should be pretty close [http://packages.debian.org/unstable/](http://packages.debian.org/unstable/)

That as much as I can help.  Good Luck

---

### Post by christhemonkey on 2007-08-27
As there are pretty frequent requests of how to use Ubuntu off line, you can use a program that i wrote, wubdepends, you can use it on a windows pc to download programs.

See the link in my signature.
</plug>


1. I would stick with Ubuntu studio 32 bit for a studio setup.

2. There is a walk through for patching your kernel with -rt patches, but i would just stick with 32 bit as the speed increase (at the moment) is not too great with audio applications.

3. Sounds support should be relatively the same between 32 an 64 bit editions. The equivalent of ASIO and WDM would be the JACK sound server. This is included with the Ubuntu studio distribution.

4. You can run 32 bit apps just not necessarily what you should do.

5. See above :D

6. [http://packages.ubuntu.com](http://packages.ubuntu.com)

7. You need to install ntfs-3g to write to them in 7.04 (its included with 7.10 i think) but you can read by default.

8. I have a bad feeling that you wont be able to use those particular files, maybe try exporting to wav or flac or something and then you can do whatever you like with them.

---

### Post by sangram on 2007-08-28
Hi, thanks everybody for the responses.

Downloading 32-bit studio and NTFS3G,  and going to install, will post back later.

Last question: What are the chances of my m-audio Delta 66 being supported out of the box?

Thanks again for your help and patience.

Edit: Thanks for that link Chris, but sourceforge is blocked on my work 'puter and I don't have the net at home just yet. I'm hoping it'll work out for me anyway, though!

---

### Post by fenian on 2007-08-28
The Delta 66 should work fine alsa has drivers for it.

---

### Post by southernman on 2007-08-28
Welcome to Ubuntu Sangram. It's refreshing to see someone actually do their homework prior to installing *anything* let alone *nix in general.

To respond to the question in your thread title... Yes, I think you should. It appears you aren't scared to get your hands dirty and that's partially what it takes to use Linux. It may get frustrating at times, but hang with it and you will reap the benefits of using Open Source Software (aka FOSS).

I might add that there is a tool called aptoncd too. Look into it after you have your system up and running.

Best of Luck...

---

### Post by sangram on 2007-08-28
Fenian, thanks for that, I've been reading a bit on getting the 66 to work almost out of the box with support for the major sample rates.

southernman: Thanks for the welcome and the encouraging words. I'm not worried about getting the thing to work more than I am about it staying up in the middle of a recording session. From what I generally hear, that is where Linux has the edge, apart from the actual recording packages being essentially free or very close to it. I really can't (won't) afford a Cubase or Nuendo right now.

Off I go to install, hopefully will not have many questions, but will BRB if I do!

---

