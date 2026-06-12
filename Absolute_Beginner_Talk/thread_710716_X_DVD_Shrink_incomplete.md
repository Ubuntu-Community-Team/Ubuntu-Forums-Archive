---
title: "X DVD Shrink incomplete"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by newbeeman on 2008-02-28
I have been doing some experiments with Xdvd Shrink as I have to rework some of out Tutorial dvds with quite limited sucess.

The program will run through it's sequence but fails to write an ISO to finish, which is what I need.

Here is the last few lines of the log. Can someone tell me what I'm missing!

"02/28/08 19:22:47    ISO file /david/GLADIATOR.iso creation commenced.
02/28/08 19:22:47    nice -n +19 mkisofs -dvd-video -V GLADIATOR -o /david/GLADIATOR.iso /tmp/GLADIATOR/BUILD/ > /dev/null 2> /tmp/GLADIATOR/mkisodebug.txt failed!
                     mkisofs reported an error creating the ISO!
                     Run terminated!
                       
                     Output of debug file
                       
Setting input-charset to 'UTF-8' from locale.
Unknown file type (unallocated) /tmp/GLADIATOR/BUILD/.. - ignoring and continuing.
mkisofs: No such file or directory. Unable to open disc image file '/david/GLADIATOR.iso'."

As you can see it write all sorts of files, but fails to complete an .iso

---

### Post by crjackson on 2008-02-28
> **newbeeman said:**
> I have been doing some experiments with Xdvd Shrink as I have to rework some of out Tutorial dvds with quite limited sucess.

The program will run through it's sequence but fails to write an ISO to finish, which is what I need.

Here is the last few lines of the log. Can someone tell me what I'm missing!

"02/28/08 19:22:47    ISO file /david/GLADIATOR.iso creation commenced.
02/28/08 19:22:47    nice -n +19 mkisofs -dvd-video -V GLADIATOR -o /david/GLADIATOR.iso /tmp/GLADIATOR/BUILD/ > /dev/null 2> /tmp/GLADIATOR/mkisodebug.txt failed!
                     mkisofs reported an error creating the ISO!
                     Run terminated!
                       
                     Output of debug file
                       
Setting input-charset to 'UTF-8' from locale.
Unknown file type (unallocated) /tmp/GLADIATOR/BUILD/.. - ignoring and continuing.
mkisofs: No such file or directory. Unable to open disc image file '/david/GLADIATOR.iso'."

As you can see it write all sorts of files, but fails to complete an .iso

Is this a copy protected DVD?  xDVDShrink won't remove protection, it only transcodes the files to a highly compressed state for placing onto smaller media.  Also (I could be wrong here) it looks like your source file is an ISO already.  I don't think it can directly compress an ISO.

---

### Post by newbeeman on 2008-02-28
> **crjackson said:**
> Is this a copy protected DVD?  xDVDShrink won't remove protection, it only transcodes the files to a highly compressed state for placing onto smaller media.  Also (I could be wrong here) it looks like your source file is an ISO already.  I don't think it can directly compress an ISO.

Don't believe so. I have .m2v  .mpg  Video TS and a list of .VOB files, all of which I could use to burn another disc if I wanted to.

The instructions I gave at the start was to build an .ISO

---

### Post by drvid on 2008-03-06
[DVD Shrink 3.2]("http://www.dvdshrink.org/") works great under Wine...

The easiest way I found to burn VOBs back to DVD-Video in Linux still uses a Windows program :P 

Just shrink or re-author it to an ISO and burn it with whatever. I believe it may even remove that pesky encryption too!

---

### Post by Eddie Wilson on 2008-03-06
xDVDShrink does work but I don't use it. It won't do the whole dvd, just the movie or main file. To rip a dvd and make an iso file I use K9copy. Its fast, its easy to use, it will run under Gnome just fine and I haven't found a dvd yet that it wouldl not reduce so I could put it on a smaller dvd. I use Gnomebaker to burn the iso back to dvd. This process works like a charm for me. In Windows I use to use 1ClickDvdCopy and AnyDvd. They were very good but you had to buy them. I haven't found anything that they could do that K9copy and Gnomebaker couldn't.

Just my Opinion,
Eddie

---

