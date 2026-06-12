---
title: "Several BIG Problems With Hoary"
date: 2005-04-10
forum: Apple PPC Users
---

### Post by ibookg4 on 2005-04-10
I have a G4 iBook dual partitioned - OSX 10.3.x and Ubuntu 5.04.  I love what the open source community has accomplished with: Linux, Gnome, OpenOffice.  I especially love what Ubuntu has done to elegantly tie it all together.  That said, the system still needs a lot of work.  Here are the probems I ecncountered so far - I would recommend comments on how to address each.

1) Click 'ctrl' whilc clicking track pad does not envoke context sensitive menu.  I disovered that 'F12' the eject button envokes the menu but does not function as an eject buttton.

2) I put in an audio cd yesterday.  I had play back but the volume was so low.  I turned both the system volume and the volume on the cd applicaiton all the way up but still no improvement.

3) I tried watching a DVD - inserting the DVD would launch the DVD player and then the system would crash.

4) Something many are already aware of - Aiport Extreme does not work.  This is obviously a major issue.

5) Flash for Firefox.  I was able to easy download the plug in but getting it installed seems quite a bit more difficult then it is for OSX or XP.

6) This is NOT a big deal, but still something to consider in making Linux easier on the eyes.  During boot sequence, we see a black screen with text - command line looking stuff.  When a user boots either OSX or XP this is hidden from them.  I think it would be great if it was hidden in Linux / Ubuntu as well.  Possibly have something that looks similar to OSX during bootup.  Any comments?

7) Again, not not a big issue - I would like help on this one though.  I was able to setup my iBook to run both OSX and Ubuntu.  Unfortunately, if booting without my intervention, it will automatically default to OSX.  I am required to hold down the 'option' key which they takes me to Apple's OS launcher.  This screen takes about 20 seconds or so before I am able to select Linux.  One I do, I am then taken to Yaboo or whatever the screenis called, where I must yet again choose either Linux, OSX or CD.  I'm guessing that I am encountering this because I did not proprly install Ununtu.

Thanks Ubuntu for all your efforts.  I hope that this is a highly useable product soon.

---

### Post by godsunderstudy on 2005-04-10
[QUOTE=ibookg4]
1) Click 'ctrl' whilc clicking track pad does not envoke context sensitive menu...

2) I put in an audio cd yesterday...

3) I tried watching a DVD - inserting the DVD would launch the DVD player and then the system would crash.

4) Something many are already aware of - Aiport Extreme does not work.  This is obviously a major issue.

5) Flash for Firefox.  I was able to easy download the plug in but getting it installed seems quite a bit more difficult then it is for OSX or XP.

6) This is NOT a big deal, but still something to consider in making Linux easier on the eyes...

7) Again, not not a big issue - I would like help on this one though.  I was able to setup my iBook to run both OSX and Ubuntu...

Thanks Ubuntu for all your efforts.  I hope that this is a highly useable product soon.[/QUOTE]

2) Same with me. It seems fine when I put headphones, but seriously low volume on its own.

4) There will never be a fix unless Apple releases AE specifications, which it will never do. Unfortunatly, you'll have to get usde to this.

5) Again, this will not be fixed unlesss Macromedia makes a PPC Linux Flash plug in, which they don't look like doing.

6) Graphical bootloader, you mean. This will probably be introduced in Breezy, the next release.

7) This happened with me, until I re-installed Hoary.  Just to let you know :)

I would try simply updating as much as possible. None of these seam deal-breakers, so stick with it, Hoary is great :P

---

### Post by eBeL on 2005-04-10
Same trouble for number one, but on my desktop... I had to resort to using this MAJORLY ANNOYING 2 button mini laptop mouse.. >.< Its TINY

---

### Post by revs on 2005-04-11
Regards (1) - function F12 will eject, wile F12 is right click, and F11 is middle click. These keys can be changed to be other keys if you want.

For dvd etc just install VideoLan Client (vlc)

---

### Post by chascon on 2005-04-11
[QUOTE=][/QUOTE]
 I run a ibook g4 (early 2004) and I have not had CDs crash my system, perhaps th DVD wxvilc crash my system once although I'm still reviewing why.
The yaboot selector deaulting to mac os is not a sign that you installed ubuntu wrong, just learn to set up yaboot.
I believe you simply need to stick in "defaultos=macosx" into /etc/yaboot.conf then run ybin. Read an manual on how to do this at penguinppc
The issue of having start up not on verbose output ... I asked myself, are you on crack?  There are important messages there. ie., if your fireswall fails it'll tell you there, meanwhile you want ubuntu to follow OS X with their ignorance is bliss modus operandi that doesn't give you any warning if something should go wrong? 

The REAL bug issue is getting sleep supported for ibooks such as mine, not cosmetic.
As for DVDs crashing your ibook, use another DVD player.  And/or report it as a bug to bugzilla.  God knows I have reported several issues in warty.  As for OS X, sane on OS X sometimes makes my Panther install crash but I don't labell that a REAL big issue, of course I've come to expect that from OS X.

---

### Post by chascon on 2005-04-11
I run a ibook g4 (early 2004) and I have not had CDs crash my system, perhaps th DVD wxvilc crash my system once although I'm still reviewing why.
The yaboot selector deaulting to mac os is not a sign that you installed ubuntu wrong, just learn to set up yaboot.
I believe you simply need to stick in "defaultos=macosx" into /etc/yaboot.conf then run ybin. Read an manual on how to do this at penguinppc
The issue of having start up not on verbose output ... I asked myself, are you on crack?  There are important messages there. ie., if your fireswall fails it'll tell you there, meanwhile you want ubuntu to follow OS X with their ignorance is bliss modus operandi that doesn't give you any warning if something should go wrong? 

The REAL bug issue is getting sleep supported for ibooks such as mine, not cosmetic.
As for DVDs crashing your ibook, use another DVD player.  And/or report it as a bug to bugzilla.  God knows I have reported several issues in warty.  As for OS X, sane on OS X sometimes makes my Panther install crash but I don't labell that a REAL big issue, of course I've come to expect that from OS X.

As for setting the subcontextual menus, if ubuntu hasn't set them already,  you can look at the unofficial ubnutnu-ppc wiki as I should be posting on how I got mine to work and other things latter this week -end.

[http://ubuntuppc.webplazahosting.com/](http://ubuntuppc.webplazahosting.com/)

---

### Post by Castaa on 2005-04-11
[QUOTE=revs]Regards (1) - function F12 will eject, wile F12 is right click, and F11 is middle click. These keys can be changed to be other keys if you want.

For dvd etc just install VideoLan Client (vlc)[/QUOTE]

It appears that fn+F12 doesn't eject my CD-ROM for my iBook.

---

### Post by khc on 2005-04-14
[QUOTE=ibookg4]I have a G4 iBook dual partitioned - OSX 10.3.x and Ubuntu 5.04.  I love what the open source community has accomplished with: Linux, Gnome, OpenOffice.  I especially love what Ubuntu has done to elegantly tie it all together.  That said, the system still needs a lot of work.  Here are the probems I ecncountered so far - I would recommend comments on how to address each.

2) I put in an audio cd yesterday.  I had play back but the volume was so low.  I turned both the system volume and the volume on the cd applicaiton all the way up but still no improvement.

7) Again, not not a big issue - I would like help on this one though.  I was able to setup my iBook to run both OSX and Ubuntu.  Unfortunately, if booting without my intervention, it will automatically default to OSX.  I am required to hold down the 'option' key which they takes me to Apple's OS launcher.  This screen takes about 20 seconds or so before I am able to select Linux.  One I do, I am then taken to Yaboo or whatever the screenis called, where I must yet again choose either Linux, OSX or CD.  I'm guessing that I am encountering this because I did not proprly install Ununtu.

Thanks Ubuntu for all your efforts.  I hope that this is a highly useable product soon.[/QUOTE]

2) see [http://ubuntuforums.org/showthread.php?t=21900](http://ubuntuforums.org/showthread.php?t=21900)
7) Once you are in linux, run 'sudo ybin'. You may need to do it again when you upgrade OS X.

---

