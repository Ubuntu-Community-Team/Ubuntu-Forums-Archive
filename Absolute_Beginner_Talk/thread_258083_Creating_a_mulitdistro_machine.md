---
title: "Creating a mulitdistro machine"
date: 2006-09-15
forum: Absolute Beginner Talk
---

### Post by dna_media on 2006-09-15
Hello,

I am a relative newbie who was running Dapper 64 until I distroyed it on accident. I am trying to set up my machine to run 7+ OS's. Let me explain.

I am a video content producer and web designer trying to switch completely to linux. (Please no comments about how difficult editing (insert medium here) is on Linux. I have Windows and my proprietary software running on one 250GB disk. If all else fails I know I can do what I need to do in Windows.)

I have a second 320GB hd that I want to put the following on:

-Ubuntu x86
-Ubuntu 64
-Fedora 5 x86
-Fedora 5 ...64
-OpenSUSE10.1 x86
-OpenSUSE10.1 ...64

I want to do this because I can't get Cinellera working in Ubuntu and as a newbie, I am trying to figure out what distro will be the best for doing all my content creation. Frankly, I also do not believe any one distro is going to be the perfect OS to do everything I want to do. Subsequently I want on communal partition to store all my media that needs worked on and stored, and it would be nice to not eat up a lot of disk space puting the same config and setting files multiple times, but I am willing to do that if I need to.

Specs: (Hardware)
Athlon 64 3500+, 2.21 GHz (need the 64 bit versions for cinelerra, x86 for flash, a few other things w/out 64bit support)
320GB SATA 3.0GB/s disk
1.00GHz RAM

Specs: (Personal)
Tons of experience with multimedia apps of all platforms
Believe that I can overcome software shortfalls through planning and creativity
Frustrated out of my head that my linux installs keep overwriting each other.
Tiny amount of expereince as a linux administrator.
Not afraid of the commandline, just not my strongest suit.

What I am looking for:
Besides a partitioner that can create extended partitions, (Gparted greys it out for some reason) I am looking for any tips, howto's, and tricks to get this going. I have been trying via google and forum searchs and trial and error for two weeks to no avail. I assume that someone has done this before, and documented it for a newbie. I will be damned if I can find it though. Does anyone know of a step by step procedure guide for doing this from a blank disk? Again, no Windows to worry about, it has its own disk.

I am willing to write a complete guide, if anyone is willing to help me with the steps. Ideally I would just get it to work, then I would start over and redo it from scratch and document the process as I go. Any ideas?

---

### Post by Najand on 2006-09-15
You can install Cinellera in UBUNTU using this guide:
[http://doc.gwos.org/index.php/Cinerella](http://doc.gwos.org/index.php/Cinerella)

---

### Post by dna_media on 2006-09-15
Thanks, but I am running 64 bit version, and this is a 386 version of cinelerra. I have also tried this option in the x86 version of dapper and I couldn't get it to work anyway.

---

### Post by haxer on 2006-09-15
Why not install freebsd and mac os tiger as well? =D>

---

### Post by bodhi.zazen on 2006-09-15
LOL :lol:

This is very easy. The hardest part is deciding how big to make each partition.

I advise that for now you stay with x86. Once you settle into a distro, try the 64 bit....

Next broaden you types of distro's. I suggest you try SUSE, Fedora, Ubuntu/Debian, PCLinuxOS, and possible Slackware/Zenwalk.

Arch or Sabayon are also considerations.

Now, as you are just experimenting I suggest 10 GB partitions for each OS.

I also suggest you partition with fdisk as GParted will give you problems.

Best distro to partition with a GUI, for what you want, is SUSE.

Once you have partitioned install away.

As far as multiboot, no problem. You could use a /boot partition (use ext2), but this can get messy.

Rather, choose 1 distro (the first one you install) to be the "boot master". Install GRUB onto MBR and root partition.

Install distro 2++. When installing the boot loader (grub or LILO) install it to the root partition NOT THE MBR.

Now edit Ubuntu_root/boot/grub/menu.lst and add entries for your new OS.

That is it. If you have questions, get stuck, or do not understand any step re-post. 8)

---

### Post by dna_media on 2006-09-15
Thanks, hopefully this will be a big help. One question. Does SUSE have some live component, or do I need to install the whole thing, then repartition, and add new distros on top. Or can i do the partitioning while setting up SUSE... nevermind that is probably what I will do.

I will certainly try your suggestions when I get a free moment, but it may be a couple days. Been nearly a month now, what is another 48 hours...

---

### Post by bodhi.zazen on 2006-09-15
I use SUSE to partition a new box. No need for SUSE Live, just the main disk is "A OK". I multi-boot to try new things. I have a more "mission critical" partition I do not like to "try new things" on.

You can partition with SUSE and abort the install, or just install SUSE as your first OS.

As far as experimentation I like Debian/Ubuntu because of the large repositories. If I find something I like, and it is not in the repo of my main OS, at least I know what I am getting for my ./configure; make; make install.

Just brush up on GRUB and you will be fine. 8)

---

### Post by user1397 on 2006-09-15
[off topic]dude, bodhi.zazen, is your avatar the symbol for satanic people?  it just looks like it does, i don't really know. [/off topic]

as for the OP's post, ive found fedora to be....umm....not so good. thats of course comparing it to ubuntu. 

opensuse is really "polished" tho.  it has its advantages/disadvantages, just like ubuntu.  overall though, i prefer ubuntu because of all the software in its repos.  there's over 18,000 of them.  i dont know if suse has this much, but i doubt it...

also, debs are known for less installation problems, and almost no dependency hell. :cool:

---

### Post by bodhi.zazen on 2006-09-15
> **erik1397 said:**
> dude, bodhi.zazen, is your avatar the symbol for satanic people?  it just looks like it does, i don't really know.

It is Pagan. It was usurped by the satanists (like Hitler and the swastika). In the words of the Buddha, symbols are empty.

I just like the way it looks.

---

### Post by user1397 on 2006-09-15
> **bodhi.zazen said:**
> It is Pagan. It was usurped by the satanists (like Hitler and the swastika). In the words of the Buddha, symbols are empty.

I just like the way it looks.glad to know that.  i was afraid we had a devil-worshipper in these forums...:p

---

### Post by bodhi.zazen on 2006-09-15
> **erik1397 said:**
> glad to know that.  i was afraid we had a devil-worshipper in these forums...:p

I should not tell you this, but there are daemons running in thousands of Ubuntu installations as we speak. :twisted:

If you play a Windows XP install CD backwards you will hear demonic voices worshiping Satan.

[indent]**Worse**..... If you play it forwards it installs Windows XP. :evil:[/indent]

---

### Post by user1397 on 2006-09-16
> **bodhi.zazen said:**
> I should not tell you this, but there are daemons running in thousands of Ubuntu installations as we speak. :twisted:

If you play a Windows XP install CD backwards you will hear demonic voices worshiping Satan.
[INDENT]**Worse**..... If you play it forwards it installs Windows XP. :evil:[/INDENT]lol

---

