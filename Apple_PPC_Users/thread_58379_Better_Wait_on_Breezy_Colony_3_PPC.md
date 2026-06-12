---
title: "Better Wait on Breezy Colony 3 PPC"
date: 2005-08-19
forum: Apple PPC Users
---

### Post by Down8ve on 2005-08-19
Greetings,

I just attempted a clean install of Breezy Colony 3 on my Lombard G3 Powerbook.  The installer freezes during the Yaboot Configuration, right at the 50% mark.  Tried it three times on two different install discs.  Seems others have had the same problem.

Just a FYI,

DSM

---

### Post by MojoX on 2005-08-20
I have the same problem installing Breezy Colony 3 on my Powerbook G4 (15", 1.25Ghz).  The yaboot install freezes at 50% while it is "looking for other operating systems."

Anyone have any ideas on how to deal with this?

---

### Post by callipeo on 2005-08-22
Hi all,

I had the same problem on an iBook G4. It seems to me that the installer is not able
to mount HFS partitions.

I've sent an installation report on the development mailing list. Maybe in the next days 
we will get some hints (or at least a bugzilla item to refer).

---

### Post by Entity on 2005-08-22
I also have the exact same problem installing Breezy. So I reinstalled Hoary and dist-upgrade to Breezy and it worked fine.

But!...

I suggest to dist-upgrade using the Colony 3 CD since I had a few problems using a french mirror (fr.archive.ubuntu.com). Some packages were simply missing from the server and my system became a real mess.

So I used apt-cdrom to re-enable the CD in /etc/apt/source.list and apt-get install the missing packages from the CD and it was repaired.

Have fun

---

### Post by callipeo on 2005-08-22
In fact, I found breezy to work pretty well on powerpc (I had it installed until two days ago). It is just an installation problem.

---

### Post by Entity on 2005-08-22
Well the only problem I had after the installation mess is that my gnome-panel was always crashing ([http://bugzilla.ubuntu.com/show_bug.cgi?id=13861](http://bugzilla.ubuntu.com/show_bug.cgi?id=13861)). But the bug report has been marked as resolved and fixed (Last modified: 2005-08-22 13:31 UTC).

---

### Post by callipeo on 2005-08-22
[QUOTE=Entity]Well the only problem I had after the installation mess is that my gnome-panel was always crashing ([http://bugzilla.ubuntu.com/show_bug.cgi?id=13861](http://bugzilla.ubuntu.com/show_bug.cgi?id=13861)). But the bug report has been marked as resolved and fixed (Last modified: 2005-08-22 13:31 UTC).[/QUOTE]

The only powerpc-specific problem I am aware of is related to poppler. Have you
had success in viewing a pdf document with evince?

---

### Post by Entity on 2005-08-22
[QUOTE=callipeo]The only powerpc-specific problem I am aware of is related to poppler. Have you
had success in viewing a pdf document with evince?[/QUOTE]

I don't extensively use evince but I didn't have any problem with it.

Check [IMG]http://ubuntuforums.org/attachment.php?attachmentid=2014&stc=1[/IMG]

---

### Post by callipeo on 2005-08-22
[QUOTE=Entity]I don't extensively use evince but I didn't have any problem with it.

Check [IMG]http://ubuntuforums.org/attachment.php?attachmentid=2014&stc=1[/IMG][/QUOTE]

Oops... sorry, I forgot the important part :-). What I meant was a pdf produced by openoffice.

---

### Post by Entity on 2005-08-22
[QUOTE=callipeo]Oops... sorry, I forgot the important part :-). What I meant was a pdf produced by openoffice.[/QUOTE]

After exporting an openoffice file as a pdf, all I see is a white page using evince but xpdf works fine.

---

### Post by callipeo on 2005-08-22
[QUOTE=Entity]After exporting an openoffice file as a pdf, all I see is a white page using evince but xpdf works fine.[/QUOTE]

OK, this is a known problem. I've pointed it out because you said that your only problem was the gnome-panel bug, and I was not sure if evince was displaying the files correctly for you, or you simply did not try with a file produced by openoffice (they are not too common, after all); ironically, the first PDF document I tried to view came from openoffice, so I noticed the issue immediately :-)

In any case, this should be fixed for the final release as far as I know.

---

### Post by dietrying on 2005-08-23
cups didn't work for me in breezy - with brother HL 1430 laserprinter. That was the only reason why i switched back to Hoary. Let's wait until it's stable ;-)

David

---

### Post by spacejunk on 2005-09-09
Does anyone know if the yaboot issue is resolved in Breezy Preview Release? I currently have Breezy installed dirty-hack style, but I would like to start it over with a working Breezy CD, should one exist.

---

### Post by callipeo on 2005-09-11
[QUOTE=spacejunk]Does anyone know if the yaboot issue is resolved in Breezy Preview Release? I currently have Breezy installed dirty-hack style, but I would like to start it over with a working Breezy CD, should one exist.[/QUOTE]

I have planned to try a fresh preview install this evening (which, in Rome, means in the next hours). I'll post my experience in this thread.

---

### Post by callipeo on 2005-09-11
Just tried with the 5.10-preview install cd: the installation went fine, but OSX was simply expunged by the yaboot menu, resulting in an unbootable OSX installation.

---

### Post by spacejunk on 2005-09-11
By unbootable, do you mean that OS X is completely unbootable or that it's just inaccessable from yaboot (and can be manually added back after booting into Ubuntu)?

---

### Post by callipeo on 2005-09-11
[QUOTE=spacejunk]By unbootable, do you mean that OS X is completely unbootable or that it's just inaccessable from yaboot (and can be manually added back after booting into Ubuntu)?[/QUOTE]

To be honest, I have still not checked because I do not use OSX :-). It really seems to me that the installer silently skipped the HFS partition, so OSX could be easily re-enabled. A few minutes and I'll come back with a definitive answer.

---

### Post by spacejunk on 2005-09-11
Thank you :)

---

### Post by callipeo on 2005-09-11
OK, as I thougth, OSX was just purged from yaboot.conf. Adding "macosx=/dev/<your_osx_partition>" to that file should be all you need to re-enable it. Of course you can always use the current yaboot.conf as a reference.

---

### Post by spacejunk on 2005-09-11
Kickass! Thank you again.

---

### Post by spacejunk on 2005-09-11
Well, I managed to install this successfully on my Powerbook G4. Like callipeo says, the yaboot installer will skip over HFS+ partitions when it does its installation. These can be added later from within Ubuntu.

I did notice that the pbbuttonsd daemon is constantly sucking up anywhere from 75%-95% of the CPU. Other than that, I've had no issues with this at all.

:)

---

### Post by callipeo on 2005-09-12
[QUOTE=spacejunk]I did notice that the pbbuttonsd daemon it constantly sucking up anywhere from 75%-95% of the CPU constantly.[/QUOTE]

Yes, this is a known bug, see [http://bugzilla.ubuntu.com/show_bug.cgi?id=13909](http://bugzilla.ubuntu.com/show_bug.cgi?id=13909). As a workaround, you can restart pbbuttonsd after the login. Hope that it will be fixed for the final release :-)

---

### Post by DoubleDangerClub on 2005-09-13
By saying "Other than that, I've had no problems at all," is that including the non-working touchpad?  I used the Live CD and still had no luck on the touchpad on my Powerbook.  I know this is an age old question, but I'm just hoping for a resolution.

DDC

---

### Post by spacejunk on 2005-09-13
To be honest, I never thought to check it, as my mouse was hooked up at the time (I try to avoid using touchpads whenever possible).

I will check and report back ASAP.

---

