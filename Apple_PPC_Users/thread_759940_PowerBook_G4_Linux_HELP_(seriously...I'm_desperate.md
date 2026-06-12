---
title: "PowerBook G4 Linux HELP (seriously...I'm desperate)"
date: 2008-04-19
forum: Apple PPC Users
---

### Post by Condip on 2008-04-19
Okay..Heres the story

I downloaded Ubuntu version 6.06 (no problems)
i wrote the .iso to a blank DVD (no problems)
I put the DVD into my PowerBook G4, restarted holding C and nothing. I got the flashing finder symbol with the question mark, then it booted mac os x. I am running leopard. I tried burning the .iso to a DVD and a CD, and tried the same thing with no success. I think i need to use a boot loader or something. I am so frustrated, i was close to throwing my mac on the floor and giving up, but i really want to install linux. I'm not looking for any live CD's or any of that crap. I partitioned my 120 gig hard drive into two portions, 105 gigs for os x, and 15 for linux. How do i install the damn thing....Please please please help. I am desperate. . .
:mad::confused::x:?:


I burned the .iso on a MacBook Pro also running leopard

I'm downloading Ubuntu 7.04 desktop right now, hopefully i will have some more luck with that.

---

### Post by stream303 on 2008-04-19
Did you burn the .iso as an iso image rather than just copy it over?

You probably did, but for the lurkers, just open up Disk Utility, drag the iso image to the left hand pane, highlight it, and then hit burn.  Preferably burn at a low-ish speed.  Are you burning it from a different os?

---

### Post by Condip on 2008-04-19
I burned the .iso on a MacBook Pro also running leopard

---

### Post by stream303 on 2008-04-19
Is it possible you downloaded the image meant for the intel macs instead of for the ppc macs?  (although you can burn it on either one) Have you looked at the other options for the ppc here (for a first-time install many would suggest the Feisty 7.04 using the "alternate" rather than the live-cd desktop version, but it's up to you)

[http://cdimage.ubuntu.com/ports/releases/](http://cdimage.ubuntu.com/ports/releases/)

They don't really show this on the "official" download page. :)
Make sure you get the PPC version.

---

### Post by Caraibes on 2008-04-19
Just like I wrote on the other thread. Move to Debian, as it officially supports PPC :)

Get your Testing netinst iso here:
[http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/powerpc/iso-cd/](http://cdimage.debian.org/cdimage/daily-builds/daily/arch-latest/powerpc/iso-cd/)

---

### Post by BladeMelbourne on 2008-04-19
I have just read 3 posts in 3 minutes saying "move to Debian". I don't care if it is officially supported, nor do I care for your unhelpful posts.

Ubuntu works fine for me. The problem with Debian is their stable release 4 r3 contains way old software. If you want something newer you then have to upgrade to testing or unstable. Not very efficient eh?

---

### Post by Condip on 2008-04-20
Haha! I was successful with Feisty Fawn. Thank you everybody, if only i could get my airport extreme card working now..](*,)

---

### Post by stream303 on 2008-04-20
> **Caraibes said:**
> Just like I wrote on the other thread. Move to Debian, as it officially supports PPC :)

I can understand your enthusiasm for Debian, as I also run both Debian and Ubuntu on my G5 iMac.  However, wholesale "moves" are no guarantee of success, although they may aid in troubleshooting.

For example, the weekly DI installer image for Debian Lenny-Testing, fails to recognize my hardware preventing installation.  To do an install, I have to dist-upgrade from Etch to Lenny-Testing.  Works great, but the DI installer needs some work, at least on my machine.

Had I followed the reverse advice of "just move to Ubuntu", on my machine, I will be met with screaming fans during install, and if you don't know about that up front, you'd be tempted to just quit the install and shut off the machine and blame Ubuntu for a bad installation.  One reboot takes care of that, but if you don't know...

So it goes both ways. :)  And that's kind of the point I try to make in other forums - we still need each other, and many of us run both distros for different reasons, and find that searching for the "one true distro" is a road to dividing a PPC community that has no need for division.

So come on board; dual-boot Ubuntu and get into the win-win situation of learning and helping out both communities.

---

### Post by stream303 on 2008-04-20
> **Condip said:**
> Haha! I was successful with Feisty Fawn. Thank you everybody, if only i could get my airport extreme card working now..](*,)

Great news!  Since I don't have any wireless experience, maybe someone else can jump in.  But here's the good news.  Apparently Hardy has solved the airport extreme problem out of the box - I think it works right now in Hardy-beta or RC if you want to call it that today.  And formal release, even if it still only a "port" is about a week away.

If you "used the whole disk" to install Feisty on, just repeat the process with Hardy and you'll be set.  Maybe some wireless gurus can give some pointers...

---

### Post by Caraibes on 2008-04-20
Ok, guys, I understand it wasn't the most diplomatic move to post a "pro-Debian" stuff in an Ubuntu forum. sorry about it, no offense ;)

I value Ubuntu a lot, and think it has done a lot for the FLOSS community in general. I always have an Ubuntu Live-cd in my toolbox. 

Hey, I even run Xubuntu Dapper on my (very old) Toshiba laptop :)

Apart from that, I was really conquered by Debian, hence my comments, especially in the PPC world, since Ubuntu doesn't officially support it anymore, I thought it would make sense to go for a "supported" distro, that was "related" to Ubuntu :)

On my other desktops (amd64, i586, i686, K7) I run Debian Stable, and I really don't have a problem if it is not the latest and most cutting edge, as I enjoy a "non crashing" environment...

But on PPC I went direct for Debian Testing because of Gnash. Gnash works very well now, and it is available in Testing.

However Debian Stable PPC users could simply add Gnash from the backports:
[http://packages.debian.org/search?keywords=gnash&searchon=names&section=all&suite=etch-backports](http://packages.debian.org/search?keywords=gnash&searchon=names&section=all&suite=etch-backports)

Anyway, I just wanted to say that... All the best to the Ubunteros, Long life to Debian, long life to Ubuntu !

---

### Post by Condip on 2008-04-20
.

---

### Post by Condip on 2008-04-20
Okay guys thanks for the advice so far. Is there any version of Linux, with the airport, video card, sound cars, pretty much everything 'pre-loaded' for my powerbook G4. Ubuntu Feisty Fawn has almost everything except for the airport drivers, and i'm having an extremely difficult time with those. I was going to try Hardy-beta but i cant find any versions for ppc processors, can someone give me the direct link for the live-cd download, for my powerbook? Please please, anything would be so helpful, i want linux for a change, osx is getting old (although dual booting would be awesome) one again please and thank you!

---

### Post by Caraibes on 2008-04-20
Here, your Debian buddy still gives you the proper Ubuntu links:
[http://cdimage.ubuntu.com/ports/daily/current/](http://cdimage.ubuntu.com/ports/daily/current/)
;)

---

### Post by Condip on 2008-04-20
Thank so much, you are brillint! :)

---

### Post by Condip on 2008-04-20
So right no my machine is running Feisty Fawn, soon to be Hardy Heron...Good. Wouold it make more sense to install hardy, then OSX? Thats what i'm going with

---

### Post by stream303 on 2008-04-20
Cool.  Caraibes's link points to the "alternate" install-only image for Hardy, which is what I usually recommend over the "live desktop" version - so you should be good to go from there.

I think dual-booting osx will be made easier by installing OSX first.  Let's say you want to cut your drive in half to run both.  At the OSX installation, before proceeding with the install, go up to the menu bar, and start Disk Utility.  Delete the existing partitions, and set up one partition for OSX to use just half the disk, and leave the rest as free space.

Back at the OSX installer menu, you can now install OSX onto that partition that takes up only half the drive now.  I'd recommend getting the "combo update" from Apple first and copying them to cd, rather than having to go through the extensive sequential-update.  The combo update will take you to the latest version.
[http://www.apple.com/downloads/macosx/apple/](http://www.apple.com/downloads/macosx/apple/)

You can also get the latest iTunes, Quicktime, iPhoto, etc that way as well, rather than do the sequential update.

Once OSX is working well, just install Ubuntu and let it install "to free space".  Ubuntu will work out all the special partitioning for you, and should provide you an option at the yaboot menu the choice of booting with Linux or OSX - this time usually seen as an "X" choice.  Or if you just let the yaboot boot menu time out on it's own, rather than interrupting the second-stage by hitting -tab-, it will automatically boot into one or the other - I forget which now...

---

### Post by Condip on 2008-04-20
Okay Hardy is installed and working. (wahoo!) Unfortunately, no airpirt extreme card rviers, no sound card drivers!!!! PLESE HELP, i am considering giving up on linux completly.:(:mad:

---

### Post by Caraibes on 2008-04-20
[http://forums.debian.net/viewtopic.php?p=128646&sid=12cc2e2be825af1dea1a650fa80573a2](http://forums.debian.net/viewtopic.php?p=128646&sid=12cc2e2be825af1dea1a650fa80573a2)

[http://forums.debian.net/viewtopic.php?t=24376](http://forums.debian.net/viewtopic.php?t=24376)

---

### Post by Condip on 2008-04-20
Okay...Good news this time!!!
I read about six hours worth of articles on people with the same problem, trying artials in french, German, and some other foreign languages. Finally i found a nifty little terminal command dmesg. I ran that (having no clue what it did) and it told me to fallow a link. I typed in the link while wired using an ethernet connection and was browsing that pages, when suddenly in the toolbar with the clock and time, a icon appeared saying "new drivers available for your computer"  I didn't click it in time, but went to System, Administration, Hardware Drivers, and it found and installed the update!
Only two more problems left, 1. No sound =[ 2. How the !@#$ do i right click?:lolflag:

---

### Post by Condip on 2008-04-20
F12 works for now but seriously...

---

### Post by slacka-vt on 2008-04-20
sound

type in terminal:

```
modprobe snd_powermac
```

you should hear beep

edit your module list like such:

```
sudo nano /etc/modules
```

and add

```
snd_powermac
```

so it loads every-time you boot.

I'm still hittin' F12 to right+click :confused:

~s

---

