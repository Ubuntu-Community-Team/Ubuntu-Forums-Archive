---
title: "Mounting An MP3 CD"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by gpeck157 on 2006-03-30
Hi All,

I have an mp3 cd that I created a number of years ago from my music collection, but when I put the CD into the drive of my laptop, it is not recognized at all. When I have attempted to mount the drive, I get the message that there appears to be no media on this drive. Any help would be appreciated. I would simply like to find a way to play my mp3 CD on my Ubuntu Breezy distro.

Thanks,

Glen

---

### Post by Akli on 2006-03-30
If ubuntu has already mounted a cd for you, there is no way that it can't mount your mp3 cd, even if you don't have the mp3 codec...

Your cd must be faulty, try it under windows to see if this is the case.

---

### Post by gpeck157 on 2006-03-30
[QUOTE=Akli]If ubuntu has already mounted a cd for you, there is no way that it can't mount your mp3 cd, even if you don't have the mp3 codec...

Your cd must be faulty, try it under windows to see if this is the case.[/QUOTE]

No, I can play it fine under Windows. The "Windows Media Player" recognizes it fine and lists all the songs, and plays them.

It must be something else.

Glen

---

### Post by Akli on 2006-03-31
Can you see the mp3 files?

---

### Post by erniewinner on 2006-03-31
sounds like a media problem? is the drive constantly spinning up? if so try copying the disk to a cdrw and see if it works. i think ubuntu mounts the cd if it can see it. while it's not a problem with your cd drive you can get inconsistances betwween software... or what did you write it with? is the disk finalised?

---

### Post by 3rdalbum on 2006-03-31
Possibility: There are many different ways to create an ISO 9660 CD.

You can have it using DOS names, or Joliet; you could have it as CD-ROM format or CD-ROM XA.

My father's MP3 CD player only plays CDs which use DOS names. Mine plays pretty much all formats of MP3 CD.

Maybe you created the CD using exotic settings that Ubuntu doesn't support?

---

### Post by gpeck157 on 2006-03-31
[QUOTE=Akli]Can you see the mp3 files?[/QUOTE]
Hi Aki,

I can see the files under Windows, but not in Breezy.

Glen

---

### Post by gpeck157 on 2006-03-31
[QUOTE=erniewinner]sounds like a media problem? is the drive constantly spinning up? if so try copying the disk to a cdrw and see if it works. i think ubuntu mounts the cd if it can see it. while it's not a problem with your cd drive you can get inconsistances betwween software... or what did you write it with? is the disk finalised?[/QUOTE]

No, the drive is not spinning up. The drive is a DVD drive. The media is a DVD +R DVD ROM 4.7 gig disk. I wrote the disk using Windows Media Player using a standard Windows XP system, nothing exotic. It all works fine under Windows. The disk is finalised.

Thanks,

Glen

---

### Post by Mustard on 2006-03-31
[QUOTE=gpeck157]No, the drive is not spinning up. The drive is a DVD drive. The media is a DVD +R DVD ROM 4.7 gig disk. I wrote the disk using Windows Media Player using a standard Windows XP system, nothing exotic. It all works fine under Windows. The disk is finalised.

Thanks,

Glen[/QUOTE]

I'm surprised that what started out being described as a CD has now become a DVD. :)  I'm curious now whether this is the issue, in that the default player for Ubuntu is expecting a CD, and not looking for DVD.

Either way it should automount and at least allow you to see the files on the DVD.  Have you tried manually attempting to the mount the device?

---

### Post by gpeck157 on 2006-03-31
[QUOTE=3rdalbum]Possibility: There are many different ways to create an ISO 9660 CD.

You can have it using DOS names, or Joliet; you could have it as CD-ROM format or CD-ROM XA.

My father's MP3 CD player only plays CDs which use DOS names. Mine plays pretty much all formats of MP3 CD.

Maybe you created the CD using exotic settings that Ubuntu doesn't 
--------------------------------------------------------------------
My system is two years old. It's an HP ZD7000 laptop with a DVD Rom drive. It plays everything fine under Windows. If I have a "standard" music CD in the drive when I boot into Breezy, it is recognized and mounted automatically like it's supposed to. With this CD though, presumably because it's an mp3 CD, it is not mounted automatically, and the disk cannot be read.

Thanks,

Glen

---

### Post by trent dillman on 2006-03-31
You could try finalizing it:

First, find out what device is your cdrom (probably /dev/hdc):

```
cat /etc/fstab | grep cdrom
```

Then fix the cd, replacing /dev/hdc with your device:

```
cdrecord -dev=/dev/hdc -fix
```

---

### Post by gpeck157 on 2006-03-31
[QUOTE=Mustard]I'm surprised that what started out being described as a CD has now become a DVD. :)  I'm curious now whether this is the issue, in that the default player for Ubuntu is expecting a CD, and not looking for DVD.

Either way it should automount and at least allow you to see the files on the DVD.  Have you tried manually attempting to the mount the device?[/QUOTE]

Hi Mustard, 

In my original post, I explained that when I tried to mount the drive myself, I got the message that there appeared to be no media in the drive, so for some reason it's not being read. I can put a standard commercial DVD in the drive and it is picked right up no problem. I can put a standard CD in the drive, and same thing , no problem. It's just this particular disk (which can be read and played under Windows with no problems) that I am not able to read under Breezy.

Thanks,

Glen

---

### Post by gpeck157 on 2006-03-31
[QUOTE=trent dillman]You could try finalizing it:

First, find out what device is your cdrom (probably /dev/hdc):

```
cat /etc/fstab | grep cdrom
```

Then fix the cd, replacing /dev/hdc with your device:

```
cdrecord -dev=/dev/hdc -fix
```[/QUOTE]

Hi Trent,

This is what I got when I ran the first line of code:

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

The disk is finalised already, so there really isn't anything I can do with it other than copy it to something else under Windows.

Thanks, 

Glen

---

### Post by trent dillman on 2006-03-31
hmmm....try this, then, and see if this works

```

dd if=/dev/hdc of=mymp3s.iso
du -h mymp3s.iso

```

If the iso is > 0, then mount it:

```

sudo mkdir /mnt/iso
sudo mount -o loop mymp3s.iso /mnt/iso

```

---

### Post by Mustard on 2006-03-31
[QUOTE=gpeck157]Hi Mustard, 

In my original post, I explained that when I tried to mount the drive myself, I got the message that there appeared to be no media in the drive, so for some reason it's not being read. I can put a standard commercial DVD in the drive and it is picked right up no problem. I can put a standard CD in the drive, and same thing , no problem. It's just this particular disk (which can be read and played under Windows with no problems) that I am not able to read under Breezy.

Thanks,

Glen[/QUOTE]

Ah ok..I can see I'm not following the plot here. :)  I best stay quiet.

---

### Post by gpeck157 on 2006-03-31
[QUOTE=Mustard]Ah ok..I can see I'm not following the plot here. :)  I best stay quiet.[/QUOTE]

No, not at all, just trying to clarify. I'm always interested in what you may have to offer.

Thanks,

Glen

---

### Post by halitech on 2006-03-31
I'm no expect so I may be completely off base but, if I remember right, you said you used Windows Media Player to create the dvd and it seems fine in Windows. I'm wondering if MS didn't pull a fast one on *nix/MAC/*BSD users by putting some kind of code in the media writer to prevent it from being seen on any other OS except Windows. Could brother bill be actually smart enough to think of something like that?

---

### Post by Mustard on 2006-03-31
I'm very curious as to whether Trent Dillman's last suggested ideas above will work. He has some very interesting suggestions.

I'm wondering whether hard drive space will permit it the copying of the iso to the hard drive, but I guess thats what the du -h option is for.  If the iso copies nicely to the hard drive it could play from the hard drive and even be burnt to a new media.

Trent, is this going to fail if the the cdrom is not mounted?  Or will dd copy from an umounted source?

---

### Post by trent dillman on 2006-03-31
Thx.

Actually, the du -h was to check the size of the resulting iso, not the space on the hard drive. I figured he'd have at least ~700m.

That reminds me though. What does 

```
df -h
```

say?

df = disk free
du = disk usage (file size)

---

### Post by gpeck157 on 2006-03-31
[QUOTE=halitech]I'm no expect so I may be completely off base but, if I remember right, you said you used Windows Media Player to create the dvd and it seems fine in Windows. I'm wondering if MS didn't pull a fast one on *nix/MAC/*BSD users by putting some kind of code in the media writer to prevent it from being seen on any other OS except Windows. Could brother bill be actually smart enough to think of something like that?[/QUOTE]

I wouldn't put it past him or his minions. I really don't' know. They're certainly not above doing something like that (IMHO).

Thanks,

Glen

---

### Post by gpeck157 on 2006-03-31
[QUOTE=Mustard]I'm very curious as to whether Trent Dillman's last suggested ideas above will work. He has some very interesting suggestions.

I'm wondering whether hard drive space will permit it the copying of the iso to the hard drive, but I guess thats what the du -h option is for.  If the iso copies nicely to the hard drive it could play from the hard drive and even be burnt to a new media.

Trent, is this going to fail if the the cdrom is not mounted?  Or will dd copy from an umounted source?[/QUOTE]

Hey Mustard, Trent, and All,

My apologies, I just checked the disc using my Windows partition. As of now it is NOT working as before, which leads me to believe this is not a Breezy problem, but a media problem. If the disc is dead, I'm really bummed. If it's for some other reason, I'm not really sure where to go from here. I'm going to see if I can find a stand alone mp3 player to see if the disc can be read and played, but as of this moment the disc is hosed (apparently). I also tried to play it under Nero (full version), and no go. My DVD drive F: (Windows) does not even show that there is a disc in the drive. I ejected the disc and reinserted it. I shut down and reboot and in both cases no go. The disc was working fine a few weeks ago because I listened to some of my music on it. Now it's not. Sorry I wasted  everyone's time. I should have checked it again under Windows before posting. Also, sorry if I came off short or rude. I've been sick this week, and really not up to snuff. Not an excuse, just fact.

Thanks for all your help, interest, and input.

Glen

---

### Post by trent dillman on 2006-03-31
No problem. But don't throw the disk away just yet. You may be able to recover files from it somehow. I have a program for Windows I bought ~2 years ago called Active File Recovery. It was only $30, and did a fine job.

---

### Post by gpeck157 on 2006-03-31
[QUOTE=trent dillman]No problem. But don't throw the disk away just yet. You may be able to recover files from it somehow. I have a program for Windows I bought ~2 years ago called Active File Recovery. It was only $30, and did a fine job.[/QUOTE]

Thanks, no I won't. I'll look into it. Yeah, I've got a lot of music on that disc, and I really don't want to lose it all. I have all the music, but putting it on the disc took hours.

Thanks,

Glen

---

### Post by halitech on 2006-04-01
well, so much for my conspiracy theory (least for now ;) )

---

### Post by gpeck157 on 2006-04-01
[QUOTE=halitech]well, so much for my conspiracy theory (least for now ;) )[/QUOTE]

I wouldn't abandon your theory just yet. Believe me I've heard of Microsoft doing much worse.;) 

Glen

---

### Post by halitech on 2006-04-01
oh believe me I know, been mucking around windows since 3.1 was introduced as a shell for DOS 5. I've also read the book Silicon Valley, the one that tells the story of Steve Jobs and BIll and how things got started as well as a book that was written by one of the former Apple CEOs and nothing surprises me from M$ except when it works :D

---

### Post by gpeck157 on 2006-04-10
[QUOTE=halitech]oh believe me I know, been mucking around windows since 3.1 was introduced as a shell for DOS 5. I've also read the book Silicon Valley, the one that tells the story of Steve Jobs and BIll and how things got started as well as a book that was written by one of the former Apple CEOs and nothing surprises me from M$ except when it works :D[/QUOTE]

That's hilarious (and true)! Thanks for the chuckle.

Glen

---

