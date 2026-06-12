---
title: "trying to download Feisty Fawn - 75 hrs?"
date: 2008-01-24
forum: Apple PPC Users
---

### Post by roybatty on 2008-01-24
Howdy Folks :

Am trying to grab Feisty Fawn from the site listed here -  75 hrs to download -  does this seem correct -  is there a torrent file so when I shut my computer down - I wont have issues restarting the downloads/

Cheers:

---

### Post by tstack77 on 2008-01-24
That is ridiculous! I just downloaded it a few hours ago from a dsl line and it took less than half an hour.

Use this link [HERE]("http://cdimage.ubuntu.com/ports/releases/feisty/release/") and go for the straight download (first option). I tried the torrent at first but there weren't enough seeders since this is so old/rare.

Good luck

---

### Post by roybatty on 2008-01-24
Howdy tstack :

this is the link I just tried - download rate kept dropping - till I saw 75 hrs 

someone posted the torrent address for 7.04 and I will have that in 17 minutes 

6.10 will take 10 days on torrent 

Is Feisty supported for PPC -  i am G5 iMac 17" 1.8 PPC

Cheers:

---

### Post by stream303 on 2008-01-25
Not only is Feisty supported, but Gutsy is too albeit with a slight screen problem that I'm working on.

My 20" is running Feisty really well, although I ONLY install from the "alternate" CD.  Should be a no-brainer with the alternate.  I used to dual-boot OSX, but found that I can live without it and now have a dedicated system.

---

### Post by roybatty on 2008-01-25
Howdy Folks:

Ok Right on :  Cheers for the replies:

I have 6.06 desktop power PC.iso

---

### Post by roybatty on 2008-01-25
Howdy Folks:

Ok Right on :  Cheers for the replies:

I have 6.06 desktop power PC.iso
           6.10 desktop power PC . iso

---

### Post by roybatty on 2008-01-25
Howdy Folks:

Ok Right on :  Cheers for the replies:

I have 6.06 desktop power PC.iso
           6.10 desktop power PC . iso
and 7.04 ( Feisty Fawn no? ) all downloaded 

Noob Question .........-  Burn these as data files no?

and ......  Should I start with Feisty first or one of the 6 series and then graduate to Feisty

installing a fresh HD so machine will be clean till I install OS x Tiger

enjoy weeks end:

Cheers :

---

### Post by stream303 on 2008-01-26
> **roybatty said:**
> Noob Question .........-  Burn these as data files no?

Nope. If you want to burn an iso from an already working Ubuntu installation, when you insert the blank cd and the "Choose Disk Type" window pops up, I just click "Ignore".  Then find your iso file, right click it, and choose "Write to Disk".  When the Write To Disk window appears, be mindful of the write-speed chosen to be equal to or lower than the specified read speed of your target machine.  Ubuntu really makes it easy to burn bootable iso's.

In OSX, you can open up Disk Utility, and just drag your iso file onto it.  Or you can use File > Open Disk Image and choose your iso image.  Then click "Burn".  Again, when the burn window appears, be sure not to exceed the read-speed of your target machine.

---

### Post by ssam on 2008-01-26
there will be very few people seeding old ubuntu release especially for powerpc. try downloading it with gwget, that should be able to resume

---

### Post by roybatty on 2008-01-26
Howdy Foks:

When I drag the iso. file into Toast 7 -  Remember I am Mac OS X 10.4.11
I have 4 options -  Data , Audio, Video , & Copy 

the only options I can think on is Data or Video -  and of course Video does not recognize file format:

Cheers:

---

### Post by guidop on 2008-01-26
It's fairly straightforward to burn the .iso image using the Mac OS X 10.4 Disk Utility program:

1) Download the .iso image and save it to disk (don't open it).

2) Open a terminal window [/Applications/Utilities/Terminal], cd to the location of the .iso file and check its md5sum to verify you have a valid image:
```

# me@mymachine:/Users/me/Desktop/ $ md5sum ./ubuntu-7.04-desktop-powerpc.iso
2081e7968e35480a8e3550abac3a086a ./ubuntu-7.04-desktop-powerpc.iso

```

3) Open Disk Utility [/Applications/Utilities/Disk Utility].

4) Use the finder to drag the .iso image file to the left sidebar of Disk Utility.

5) Click on the .iso file in the sidebar to select it, then click the "Burn" button.

6) Insert a blank CD, then select the _lowest_ burn Speed available, and Burn the CD.

---

