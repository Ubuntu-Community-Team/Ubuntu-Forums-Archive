---
title: "Does Ubuntu support ISO-13346"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Justin Holt on 2006-08-29
Like the title says...does it?  And if not, how do I make it support it??

---

### Post by TFX360 on 2006-08-29
Dear Justin,


Definately not a beginner question. I have no clue what so ever.


Kind regards,


TFX

---

### Post by stalefries on 2006-08-29
The Wikipedia article says it does. 
[http://en.wikipedia.org/wiki/Universal_Disk_Format#Native_OS_Support](http://en.wikipedia.org/wiki/Universal_Disk_Format#Native_OS_Support)

Please try to do a little research from now on, if you can.

Edit: in fact, it seems to have the best support of any OS.

You can read more about Linux support here: [http://linux-udf.sourceforge.net/](http://linux-udf.sourceforge.net/)

---

### Post by Justin Holt on 2006-08-29
sorry about that...but thanks...i actually found that the dvds i was using to burn actually sucked so i had to get a better brand...w00t memorex

---

### Post by Blario on 2007-01-05
Perhaps this question shoudln't be in the noobie section afterall.  I have been reading the same material that's been posted here.  What you find in practice is quite different though.  I have a Vista DVD that not readable by edgy.  When viewing the DVD, one file is viewable.  The contents of this README are

"This disc contains a "UDF" file system and requires an operating system

that supports the ISO-13346 "UDF" file system specification.
"

What you see at linux-udf.sourceforge is software meant for linux 2.2.  I've tried to compile it and no-go.  It doesn't like 2.6.`7 at all.  

I'm sure I'm not the only person to run across this.  What can be done in order to read ISO-13346 / Vista DVDS?

---

### Post by Bil-E-daKid on 2007-02-26
Blario - I too am experiencing the same problem - did you manage to find an answer to this?

---

### Post by monogoggle on 2007-02-27
I am experiencing a similar issue.

The other day, I received from Amazon a DVD from the people who make IMAX films. The DVD case had two disks, one a regular DVD version of the film, and the other was a WMVHD version of the film. For those who don't know, the WMVHD is a high definition format and would obviously be able to give a better picture than a regular DVD.

I tried playing the regular DVD version in my laptop, works fine, but the WMVHD version does not. Instead, it opens up a directory on my DVD drive which only contains a single readme.txt file:

"This disc contains a "UDF" file system and requires an operating system that supports the ISO-13346 "UDF" file system specification."

Now, I understand that WMVHD stands for something like "Windows Mediaplayer Video High Definition" so I might just be SOL since it's a MS product, but I was curious if anybody knows of a work around?

It should be a well known codec (Windows Media Player 9) and format (since it's an ISO standard) I'd think but I could be wrong. Apparently, from my searches on the web, Microsoft is starting to make more disks in this format too so someone should be working on it someplace I would think.

I've followed the links to Wikipedia links for UDF file support @ [http://en.wikipedia.org/wiki/Universal_Disk_Format](http://en.wikipedia.org/wiki/Universal_Disk_Format) to [http://sourceforge.net/tracker/index.php?func=detail&aid=1476807&group_id=295&atid=300295](http://sourceforge.net/tracker/index.php?func=detail&aid=1476807&group_id=295&atid=300295) but that brings me to files that you can apparently use to patch the kernel. Being a noob, this is about where I begin getting nervous and look for help from others since I have no idea where to start with that or if this is the right thing to do.

Any help would be appreciated. Thanks!

---

### Post by Blario on 2007-02-27
> **Bil-E-daKid said:**
> Blario - I too am experiencing the same problem - did you manage to find an answer to this?

Nope.  I probably copied it on a windows computer at work.  Keep me posted :)

---

### Post by amak79 on 2007-03-05
Hi,

I was able to mount the Vista DVD by doing the following:

[LIST=1]
[*]Change the fstab <type> entry for the DVD-ROM from udf,iso9660 to auto
[*]Insert the Vista DVD
[/LIST]

It appears as though Ubuntu (Edgy) mounts the Vista DVD as an IS09660 filesystem with the original fstab entry. I verified this by running mount after inserting the Vista DVD. Also, my understanding is that Linux has supported ISO13346 (UDF) for a while now.

---

### Post by Bil-E-daKid on 2007-03-05
Hey there amak79 - that's great news.

Yes, I had read that the linux kernel did ISO13346 for ages but couldn't figure out why it wouldn't mount properly.  Obviously dbus or whatever it is that automounts things is detecting the format incorrectly and mounting ISO9660 instead.

I will try your suggestion when I get back to work - I don't have a Vista DVD at home.  I got around it by copying the contents of the DVD to hard disk using a Windows 2003 VM and then burnt it to a new DVD from linux (obviously ISO9660 instead).

Still couldn't boot from the blasted thing though - but that's another story.....  ;-)

I wonder if we should perhaps log a bug for the ISO13346 filesystem detection thing?

---

### Post by amak79 on 2007-03-05
Bil-E-daKid,

If you can verify this on your system, then it's probably a good idea to file a bug report.

---

### Post by amak79 on 2007-03-05
My system is now able to mount the Vista DVD correctly when inserted. I modified the fstab <type> entry for /dev/hdc (DVD-ROM) from udf,iso9660 to auto. This also allows the Vista DVD to mount as your user rather than as root as my previous steps did. I'm not sure why Ubuntu uses udf,iso9660 as the default type as my Gentoo systems have always had auto as the default. I have updated my original post with new the instructions.

---

### Post by Blario on 2007-03-05
> **amak79 said:**
> Hi,

I was able to mount the Vista DVD by doing the following:

[LIST=1]
[*]Change the fstab <type> entry for the DVD-ROM from udf,iso9660 to auto
[*]Insert the Vista DVD
[/LIST]

It appears as though Ubuntu (Edgy) mounts the Vista DVD as an IS09660 filesystem with the original fstab entry. I verified this by running mount after inserting the Vista DVD. Also, my understanding is that Linux has supported ISO13346 (UDF) for a while now.

:guitar: Thanks for the great info Amak79!

---

### Post by Bil-E-daKid on 2007-03-06
Hey there Amak,

I just tried your mount -t udf thing and it worked.  Then I went into the fstab (after looking at 'UDF' bugs in the launchpad) and changed the udf,iso9660 part of the cdrom line to auto.

Presto it works!  Then I come in here to let everyone know and find that you found the same thing too.

I'd say 'great minds think a like' but I don't want to be self presumptous!  ;-)

---

### Post by monogoggle on 2007-03-07
The /etc/fstab edit worked like a champ for me. Thanks for the help guys.  

Now I still need help playing WMVHD formatted videos. Any suggestions? Thanks!

---

### Post by amak79 on 2007-03-07
monogoggle,

I'm assuming you enabled the restricted multimedia formats. Instructions are available here: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") and here: [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs"). The WMVHD video that you have is most likely DRM enabled which means that you will not be able to play it on Linux even with the w32codecs package installed.

---

### Post by SonicSteve on 2007-06-09
> **monogoggle said:**
> The /etc/fstab edit worked like a champ for me. Thanks for the help guys.  

Now I still need help playing WMVHD formatted videos. Any suggestions? Thanks!

Its WMVHD with emphasis on the HD. I ask this question with all honesty, does ubuntu have support for HD video?

---

### Post by SonicSteve on 2007-06-09
And back to the original thread discussion, I have the exact same problem reading a VISTA HOME BASIC DVD. It mounts as a "UDF volume" with one file showing. That being the readme.txt file that tells me;
> This disc contains a "UDF" file system and requires an operating system

that supports the ISO-13346 "UDF" file system specification.

I tried changing the FSTAB mount option to auto and it didn't work.
However could someone post their FSTAB mount option if it is working, I just want to make sure I changed it correctly. In fact I know that I didn't because after I made the change I couldn't mount anything in that drive.
Thanks.

---

### Post by amak79 on 2007-06-09
SonicSteve,

I can confirm that mounting a Vista DVD in Ubuntu 7.04 works, however you need to modify your fstab entry. Here is my fstab entry for my DVD-ROM.```
/dev/hdc /media/cdrom0 auto noauto,user 0 0
```

---

### Post by amak79 on 2007-06-09
> **SonicSteve said:**
> Its WMVHD with emphasis on the HD. I ask this question with all honesty, does ubuntu have support for HD video?
> **amak79 said:**
> monogoggle,

I'm assuming you enabled the restricted multimedia formats. Instructions are available here: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") and here: [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs]("https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs"). The WMVHD video that you have is most likely DRM enabled which means that you will not be able to play it on Linux even with the w32codecs package installed.
WMV playback whether it is HD or not is provided by the w32codecs package. This package contains actual Windows DLL's to allow playback under Linux. As long as the WMVHD files do not have DRM they should play fine. If you want to play WMV files with Totem you need to install the totem-xine package, otherwise use mplayer or xine.

---

### Post by SonicSteve on 2007-06-11
> **amak79 said:**
> SonicSteve,

I can confirm that mounting a Vista DVD in Ubuntu 7.04 works, however you need to modify your fstab entry. Here is my fstab entry for my DVD-ROM.```
/dev/hdc /media/cdrom0 auto noauto,user 0 0
```

I gave this a try exactly as you quoted, after making the changes nothing mounts properly, and I mean nothing.

edit, I made sure that I used the appropriate device listings and also mount points

---

### Post by SonicSteve on 2007-06-11
I've been reading different things about UDF. I'm wondering what UDF revision Ubuntu actually supports. There are so many versions, the latest is v2.60. 
I found different sites that seem to point to this patch as the answer.
[http://sourceforge.net/tracker/index.php?func=detail&aid=1671912&group_id=295&atid=300295](http://sourceforge.net/tracker/index.php?func=detail&aid=1671912&group_id=295&atid=300295) 

search Linux udf vista dvd and you'll find what I did.

HOW DO YOU APPLY A PATCH LIKE THIS?

---

### Post by SonicSteve on 2007-06-11
also read this,
The section about native OS support for UDF mentions this patch for linux kernels v.2.6.x 

[http://en.wikipedia.org/wiki/Universal_Disk_Format](http://en.wikipedia.org/wiki/Universal_Disk_Format)

---

### Post by amak79 on 2007-06-11
SonicSteve,

The latest UDF driver on the [[COLOR="Blue"]SourceForge[/COLOR]]("http://sourceforge.net/project/showfiles.php?group_id=295") project page is 0.9.8. Ubuntu uses vevrsion 0.9.8.1 which is the verison included with the 2.6.20 kernel. I verified this by checking the /var/log/messages after the VIsta DVD was mounted.```
UDF-fs: Partition marked readonly; forcing readonly mount
UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'UDF Volume', timestamp 2006/11/03 06:00 (1258)

```Could you post the output of running [FONT="Courier New"]mount[/FONT] and [FONT="Courier New"]tail /var/log/messages[/FONT] after inserting the Vista DVD. Could you also post your complete fstab file please?

**Edit1**: Regarding the UDF version, It seems Linux supports at least UDF 2.0x after reading the Wikipedia entry. To apply the patch you need to install the kernel source by following these [[COLOR="Blue"]instructions[/COLOR].]("https://help.ubuntu.com/community/Kernel/Compile") After the kernel source is installed run the following commands to merge the patch.```
$ cd /usr/src/linux
$ sudo patch -p1 < UDF-2.50_linux-2.6.20.patch
```Now continue with the instructions to compile and install the kernel.

**Edit2**: After some searching I found this [[COLOR="Blue"]page[/COLOR]]("http://www.groklaw.net/article.php?story=20070422083715451") which discusses UDF support in Vista. Towards the end of the article there is a section which lists UDF version support in Vista and Linux. It confirms the Wikipedia entry that Linux and therefore Ubuntu support UDF 2.0x. UDF 2.50 (read-only ) is only available via the patch you found.

---

### Post by SonicSteve on 2007-06-12
Hmmm,
Read only eh? so here is a question;
I fix computers and I don't like using original disks for general repair installations. If I can only read UDF 2.5.0 will I be able to make a burn copy and then change the output filesystem to something else and then still have no adverse effects on it's functions.

---

