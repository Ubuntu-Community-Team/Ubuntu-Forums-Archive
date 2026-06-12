---
title: "Weird problem with Ubuntu 6.06 Live CD, iMac G5"
date: 2006-07-25
forum: Apple PPC Users
---

### Post by bensamples on 2006-07-25
Hi there!

I'm having a really strange problem with the Live CD.  When I first tried to run the CD, it would appear to be booting fine and then tank as soon as X would start -- I'd get the distinctive brown background color (which started off getting called the pleasant "Ubuntu brown" but progressed into the more scatalogical after several failed attempts), the mouse would appear to work for a moment, and then everything would die.  Eventually, if left like this for a while, the CPU fans would kick on, so I figure it's doing something in there but I don't know what.

The CD I am using is the silver (non-CD-R) Ubuntu CD that comes from shipit.ubuntu.com, so I'm pretty sure there isn't a data integrity problem.  However, just for the sake of doing it, I checked the md5sum file against the data on the CD, and that's when the real fun started.  Here's a sample of the output I'm getting.

[INDENT]Lola:/Volumes/Ubuntu_PowerPC_dapper ben$ md5sum -c md5sum.txt 
md5sum: can't open ./pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2_powerpc.deb
md5sum: can't open ./pool/main/b/bpalogin/bpalogin_2.0.2-6ubuntu1_powerpc.deb
md5sum: can't open ./pool/main/b/build-essential/build-essential_11.1_powerpc.deb
md5sum: can't open ./pool/main/i/isdnutils/capiutils_3.8.2005-12-06-2ubuntu4_powerpc.deb
md5sum: can't open ./pool/main/i/isdnutils/ipppd_3.8.2005-12-06-2ubuntu4_powerpc.deb
md5sum: can't open ./pool/main/i/isdnutils/isdnutils-base_3.8.2005-12-06-2ubuntu4_powerpc.deb
(...)[/INDENT]

...and so on.  Thinking this was very strange, I started doing some detective work.  I took the first file that came back (./pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2_powerpc.deb) and looked for it on the CD.

[INDENT]Lola:/Volumes/Ubuntu_PowerPC_dapper ben$ cd pool/main/b/binutils/
Lola:/Volumes/Ubuntu_PowerPC_dapper/pool/main/b/binutils ben$ ls
binutils_2.16.1cvs20060117-1ubu[/INDENT]

The filename is getting silently truncated after 31 characters.  I looked through the next couple of files on the list and they have the same problem.  I also checked the CD on a (Windows-running) PC, too, and it appears to be suffering from a similar ailment -- the file above read on my PC as "binutils_2.16.1cvs20060117.deb", 27 characters with a period and the three-character MS-DOS-style file extension slapped on the end.

My knowledge on CD-rom innards is a bit limited, but I know that very long filenames are generally supported by an extension to the ISO standard.  My suspicion is that my Mac on boot is doing something weird to the CD-ROM drive that's causing Ubuntu to not be able to recognize its own filenames, but I could be totally off base.  Does anyone out there who knows more than I do have any suggestions as to what I might want to try to do from here?

I'd really appreciate the help.  Thanks a bunch!

---

### Post by megabenman on 2006-07-28
It's because ubuntu STILL doesn't work on the iMac G5...

---

### Post by bensamples on 2006-07-29
I didn't know.  Jesus, you could've been a bit nicer about it.

It would be nice if this were posted somewhere prominent on the Mac download page so folks know not to waste their time.  Thanks for the reply.

---

### Post by gwon on 2006-07-29
Yeh it would be nice. But the developers seem to be ignoring the issue.

---

