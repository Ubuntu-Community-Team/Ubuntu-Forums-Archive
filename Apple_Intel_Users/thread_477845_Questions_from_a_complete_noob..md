---
title: "Questions from a complete noob."
date: 2007-06-18
forum: Apple Intel Users
---

### Post by K3ITHK on 2007-06-18
I want to dual boot on my MacBook (bottom of the line 1.83 GHz Intel w/ 60 gb hard disk).

Now I have read through some stuff and I sort of know what is going on but I have a few questions.

1. I've read that the minimum space I would want to allot to Ubuntu is 5 gb, but what is a workable minimum? Would 15 gb suffice? I just think it is ridiculous that OSX (and preinstalled apps), MS Office (cause open office for mac sucks), Photoshop, Mathematica and maybe a few other things take up 30 gb. Will I be looking at this situation in Ubuntu?

2. I know there are tutorials and I should be able to follow them, however is there any chance that I could still screw it up being a complete noob. I had installed Ubuntu on an older PPC machine (which died shortly thereafter and consequently I have no real experience) and that was relatively simple, is this going to be the same way?

3. Is this going to void any type of warranty?

4. How long will it take me to get the hang of this? I am relatively computer savvy and have a lot of experience in both OSX and Windows.

5. I have read that Fedora claims to be the first Linux distro to fully support Intel Macs, and I am wondering how much of this is true, as I have read there are plenty of problems (specifically after install). Is Ubuntu a more well qualified distro for running on Intel Macs? Why Should I choose Ubuntu over Fedora (if indeed its claims of being the first distro to fully support Intel Macs is true)?

Thanks in advance for any and all responses. When I finally get around to installing Linux, I'm sure I will be back.

---

### Post by nine01a on 2007-06-18
What's up, K3ITHK?

1. When I tried Ubuntu, I used a 9.5 GB partition and installed all the junk I wanted and played around happily. Even had a couple large games with Wine installed. It only ate like 5-6 GB of the partition.

2. I can't personally be of any help personally with it but you should try installing it and seeing if everything works out of the box and if not, just look through Google or here on the forums. There should be a ton of people doing the same thing =)

3. Nope.

4. Shouldn't take long at all. I randomly put it on our family computer and nobody even noticed, really, since they're typical desktop users.

5. I found [this]("http://bin-false.org/?p=17") on these forums.

Hth, mate.

---

### Post by Anonii on 2007-06-18
First of all, I want to say that I never used an Intel Mac, but I don't think it really matters for your questions (except the fifth which I will dodge.).

1) It depends on what you are gonna do with your system. Right now, I have a fully functional system (I'm not using Windows, just Linux) in 20GB of space. These 20GB include movies, Windows games, work documents, etc. (My music is in a seperate partition.). If you are not planning to store that stuff in your Linux partition you can say that 5GB are more than enough, even with Office and Image Editing applications,

2) There are many tutorials, indeed. There are many chances that you will screw up, indeed. There are also equally many chances that you will have a horde of gentlemen in these forums helping you fix these screw ups. But well, it's sure that you will enjoy your screw ups, and if you decide to use Linux for the years to come, you will laugh one day with them.

3) What? Using Ubuntu? Nah..But you will have us. The forum geeks. To help you with any question!

4) Getting the hang of this, heh. It depends on what you mean? Getting the hang of this, as building your own Linux distro? Getting the hang of this, as beeing able to debug anything in zero time? Getting the hang of this, as beeing able to listen to music and surf the internets? Getting the hang of this, as joining the Linux/Ubuntu community and helping poor people, like you? Getting the hang of this, as joining teams of bug crashers and contributing to the FLOSS movement? Getting the hang of this, as becoming a 1337 hax0r and hax1ng s1t3z with your 1337 tools? What's your, "getting the hang of this", sir? The time, depends on your mood and will-power.

5) dunno lol


Have fun, sir :3

---

### Post by K3ITHK on 2007-06-18
Thanks for the incredibly fast responses and all the help. I figure I'll try tomorrow to put Linux on my MacBook, granted I have time (NYS DMV always takes forever), and if I have any problems I'll return.
:)
Should I use the 64 bit version? I ask because when I tried running Ubuntu 64 bit version in Parallels I received an error that read, "Your CPU does not support long mode. Use a 32 bit distribution."
As far as I know, all core 2 duo processors are 64 bit, and that is something I thought I was damn sure about.

---

### Post by cevans on 2007-06-18
> **K3ITHK said:**
> I want to dual boot on my MacBook (bottom of the line 1.83 GHz Intel w/ 60 gb hard disk).

Now I have read through some stuff and I sort of know what is going on but I have a few questions.

1. I've read that the minimum space I would want to allot to Ubuntu is 5 gb, but what is a workable minimum? Would 15 gb suffice? I just think it is ridiculous that OSX (and preinstalled apps), MS Office (cause open office for mac sucks), Photoshop, Mathematica and maybe a few other things take up 30 gb. Will I be looking at this situation in Ubuntu?

After years of using only Linux (first Debian, then Ubuntu when it came out), I can tell you that I was quite shocked by the absurd sizes of applications in OS X. Linux applications are usually smaller, since they don't include useless binaries ("Universal" OS X applications are actually just applications with multiple copies of the same code compiled for different architectures, resulting in quite a bit of wasted space), and tend to make better use of shared libraries - in fact, I've generally found that Linux applications tend to be smaller than the libraries they depend upon, due to massive code reuse.

With Ubuntu, I generally use two partitions, with one containing my data and the other containing the OS. I've never needed more than 10 to 15 GiB for the latter, even when I've had ubuntu-desktop, kubuntu-desktop, and xubuntu-desktop installed. 

By the way, you might want to look at Monolingual for OS X, which can reduce the size of installed applications somewhat by removing extra language files and code for other architectures.

> 
2. I know there are tutorials and I should be able to follow them, however is there any chance that I could still screw it up being a complete noob. I had installed Ubuntu on an older PPC machine (which died shortly thereafter and consequently I have no real experience) and that was relatively simple, is this going to be the same way?


Even for a highly experienced user or developer, it is very difficult to make Ubuntu work perfectly on a MacBook, but it isn't very hard to make it work acceptably. In my opinion, however, one of the best advantages that Linux has over OS X is the community, and so if you have problems you will usually be able to solve them by asking here.

---

### Post by K3ITHK on 2007-06-18
Just to make sure this isn't missed, as I edited it in.

Should I use the 64 bit version? I ask because when I tried running Ubuntu 64 bit version in Parallels I received an error that read, "Your CPU does not support long mode. Use a 32 bit distribution."
As far as I know, all core 2 duo processors are 64 bit, and that is something I thought I was damn sure about.

TIA

---

### Post by cevans on 2007-06-18
If I recall correctly, Parallels doesn't support 64 bit instructions even when using a 64 bit processor. In theory, you can install the x86-64 edition of Ubuntu on a MacBook, but in general, it just causes some problems, and doesn't really result in any benefits if you don't have some specific reason to need that edition.

---

### Post by K3ITHK on 2007-06-18
OK, thanks. So I won't be able to take advantage of my 64 bit processing power? Well, I guess most programs really can't anyway.

---

### Post by eldepeche on 2007-06-19
If you're willing to reinstall, you can get OS X quite slim. The absolute minimum is about 4GB. My install, with GarageBand and all the sample loops and a few other useful programs is around 11GB. Oh, that includes a lot of the developer tools as well.

Just make sure to look for the Customize button. It wants to install drivers for every printer on the planet by default.

---

### Post by ronocdh on 2007-06-19
> **eldepeche said:**
> If you're willing to reinstall, you can get OS X quite slim. The absolute minimum is about 4GB. My install, with GarageBand and all the sample loops and a few other useful programs is around 11GB. Oh, that includes a lot of the developer tools as well.

Just make sure to look for the Customize button. It wants to install drivers for every printer on the planet by default.
Actually I believe these components can be removed without reinstalling. Just boot to the OS X DVD and remove them. I might be mistaken here, though, so please do some research before trying it out. I know there are applications such as [Monolingual]("http://monolingual.sourceforge.net/") which remove unwanted packages to free up diskspace.

---

### Post by K3ITHK on 2007-06-19
Let's hope I can find my OSX DVD. 

Another thing I found is that Core 2 Duo chips aren't really 64-bit. It can run 64 bit process, but it really isnt.:(

And oh yea, I didn't have time today to install Ubuntu. Tomorrow maybe.

---

### Post by ivesjd on 2007-06-20
The core duo chips are not 64bit, but the core 2 duo chips are. And about monolingual, I used it and saved almost 2gbs. And then I went through and deleted things like, other language dictionaries for MS office. And then all the sample stuff for photoshop. I ended up reclaiming almost 4 GBS just by deleteing un-need things. Oh, I also went through and deleted programs that I no longer use.
In Ubuntu, I use about 5Gbs, and thats with a 700MB movie sittin on my desktop. I have all kinds of programs (probably alot that will never get used) and its still the smallest install of any of my OS's. Hope that helps!

---

