---
title: "Switching considerations?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by vavroom on 2007-02-27
Hello all,

I'm seriously considering switching to Ubuntu from XP.  Before I go ahead with this, I need to know a few things.  One of the biggest issues I have is "will I be able to find applications that do what I need them to do?"...  The other issue is that of sharing a LAN with Windoze based machines.

I particularly need to have a web development application similar to Dreamweaver (no, I don't use it as a WYSIWYG, but I find the syntax highlighting, tag completion, project management, snippet creation, etc to be *very* useful, so please don't tell me to use Notepad.  I was coding HTML in Notepad before Frontpage 1.x.......).  I've heard NVu and Bluefish mentionned.  Has anyone used them that has experience working with Dreamweaver?

Also, I need something with the grunt and abilities of Photoshop.  I've heard GIMP mentionned.  How does GIMP *really* compare to Photoshop?  Batch processing?  Filters and effects???

We connect to the web on ADSL through a router, linked to a hub.  All the PC's are connecting to the hub.  Is running some machines on Windoze and some on Ubuntu create problems with internet connection?  How about file sharing from one PC to another?  Printer sharing?

Any constructive feedback more than welcome :)

Thanks

Nic

---

### Post by ZeroXR on 2007-02-27
As far as Gimp goes, it takes some getting used to, but you can definately shorten that time frame by installing the GIMPshop plug-in which will recustomize the interface to be very familiar to an Adobe Photoshop user. I edit photos and use Gimp for some computer generated images, it works well, although it's a bit hard to find tutorials if you edit images on occaision.

**EDIT:** I'm a recreational user, so as far as my purposes are concerned... Gimp is a good open source solution rather than hearing all of my other friends pirating the new CS3 Beta. If you're more photo centric or image editing intensive and cannot deal with Gimp, you do have the option to emulate it via WINE. If anyone is better versed on Gimp vs. Adobe Photoshop, please chime in.

Here's the Link to GIMPshop if you're curious: [GIMPshop by Plastic Bugs (Click Here!)]("http://plasticbugs.com/?page_id=294")

---

### Post by wireddad on 2007-02-27
The only problem I see is if you have to write to XP system.  Linux can not write to NTFS at the moment; it can get stuff off NTFS though.  A solution could be to have an ternal HD (VFAT) shared among all your PC's.

Do not know about the programs.  I have use Nvu for basic html only.

---

### Post by irish_flu on 2007-02-27
OK, please take note that when I answer your questions, I'm specifically leaving out your questions about Web Design and GIMP/Photoshop.  That's just not my bag, baby.  I strongly suspect that the answer is "yes", but I've use Gimp and Photoshop for only pretty simple things.

As far as most other things, I'll say "yes".  You'll find programs to take care of the "mundane" things you do.  Listen to music, edit sound files, edit MS Word/Excel docs (Open Office handles these well), watch movies (including win32 codecs), etc.

One thing I'll ask is whether or not you buy and download from iTunes?

As for networking, I can also say "yes".  I have had no problem mounting my Windows Fat32 and NTFS shared drives, and my HP printer (shared from a Windows XP box) was simpler to set up in Ubuntu than it was on other Windows boxes.

As far as your internet connection goes, there should be no problems whatsoever; the TCP/IP stack in Linux is at least as stable as the one in Windows XP.

---

### Post by irish_flu on 2007-02-27
> **wireddad said:**
> The only problem I see is if you have to write to XP system.  Linux can not write to NTFS at the moment; it can get stuff off NTFS though.  A solution could be to have an ternal HD (VFAT) shared among all your PC's.

Perhaps I'm wrong, but I thought this NTFS writing issue (for which there are workarounds, but IIRC they don't work great) was only for mounting a local NTFS partition?  My NTFS Windows network shares work in Ubuntu "out of the box".

---

### Post by vavroom on 2007-02-27
Thanks for the answer guys and gals.  I guess I know what I'm doing tonight :)

---

### Post by luke411 on 2007-02-27
Like you, I was doing web pages commercially before you could pick up a program from Walmart for doing your own. If you have the investment and requirements I think you do, you might want to try a dual boot for awhile. The biggest adjustment to Linux is the time it takes to become 'familiar' with the different programs. Every post on here is probably correct in that there is most likely a compatible program that will do everything you need (I haven't had to do a web page with Linux yet but I have played around with some of the editors). Just keep in mind that there is a lot of software to choose from for Linux and many of them do the same things, some better than others. None of them have a huge amount of documentation though and it can take a little time to find all of the hidden features of these programs. Good luck whatever you choose.

---

### Post by russell.h on 2007-02-27
I don't know of a single Linux text editor that doesn't have syntax highlighting. There are probably more "integrated" web development solutions out there, but if all you want is syntax highlighting the default text editor can highlight every major language I know of (including HTML, JavaScript, PHP, CSS and probably whatever else you might use for web development, plus real programming languages).

---

### Post by vavroom on 2007-02-27
@luke, thanks for pointing those potential pitfals

@russel, I am sorry, I thought I had explained myself more clearly than that.  It's not just about syntax highlighting (though I'm glad to hear the default text editor does that).  It's also about project/site management, the ability of using/re-using snippers easily, tag completion, etc.  No worries, i'll have a play.  FWIW, I find it amusing that one asks a question and receives a judgemental statement about not using real programming languages.  <shrug>

---

### Post by wireddad on 2007-02-27
> **irish_flu said:**
> Perhaps I'm wrong, but I thought this NTFS writing issue (for which there are workarounds, but IIRC they don't work great) was only for mounting a local NTFS partition?  My NTFS Windows network shares work in Ubuntu "out of the box".

You could be right. When I'd purchased an external HD, I formatted it vfat just to be sure it can be r, rw from both system.  I did not realize that linux can write to NTFS now.

---

### Post by igknighted on 2007-02-27
> **wireddad said:**
> You could be right. When I'd purchased an external HD, I formatted it vfat just to be sure it can be r, rw from both system.  I did not realize that linux can write to NTFS now.

FWIW, windows can read/write the more stable ext3 file system too.  With ntfs-3g now past beta, and ext3 readable in windows (if you install the driver), fat32 as a shared partition should be on the out, because it's awful.

---

### Post by wireddad on 2007-02-27
> **igknighted said:**
> FWIW, windows can read/write the more stable ext3 file system too.  With ntfs-3g now past beta, and ext3 readable in windows (if you install the driver), fat32 as a shared partition should be on the out, because it's awful.


Can you link me to some instructions?

---

