---
title: "Better support for installing programs without internet"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Ella Huovinen on 2007-05-28
Hi!
I have both XP and latest Ubuntu Studio up and running smoothly on my computer. I have had few distros earlier (Ubuntu 5.04, OpenSuse10, PuppyLinux) and absolutely adore Ubuntu to be the best of them so far.
My problem is that I don't have internet at home (yes, I'm from Neolithic age :D ) and probably won't get one 'cos I can't afford it ( I surf in work/school/at my parents). 

So what I have encountered due to this is the HUGE obstacle in installing new programs. I managed to install Ubuntu 5.04 some programs by downloading libraries from net and breaking the packages quite giftedly in order to get e.g. Inkscape working. 

My conclusion was that it's really pain in the buttocks to try do it and not necessary worth it because there are
few "includes all the necessary libraries"-packaged programs (or .deb files). Fortunately Ubuntu Studio has all the important graphics-software installed. Now, suprisingly, I would like to get the media codecs so I could play mp3's. 

As funny it is (and you can blaim me for that) the one reason why I don't have Ubuntu in usage 90% (versus the situation now is circa 90% XP, 10% Ubuntu) is that when I work I like to listen to music and play dvds. 
It's silly but I have the same software on XP as I have in Ubuntu (Gimp, Inkscape, Scribus, Ooffice.. which work better in Linux) and then I use XP for mp3/dvd-playing possibility.

Well, all in all, XP is much more user friendly for people without net. I know that media codecs aren't open sourced material and there is movement to find simpler package methods (have I understood correctly?).
But it would be nice to have codecs in your package immediately (Ubuntu Mint has them? but don't have scribus at least? always battle of programs for me). That would help a lot for people to move to Linux. One alternative would be to create new and as small (or smaller) format as mp3 for saving music (but I guess can't be happening because it is not ok to rip wavs in copyright sense... :( )

However, maybe in future this all will change. Anyways, if you have suggestions what is the best way to download material for Ubuntu without net I'd appreaciate it! Even though my posting is quite negative in some respects don't get me wrong; I do like Ubuntu and all the good work people have done for it! Hopefully  I will be able to get net someday but 'til then I keep hoping that something comes up ;). 

me

---

### Post by aysiu on 2007-05-28
I really don't know why Ubuntu doesn't provide some official add-on CDs. If they're worried about confusing new users (and add-on CDs *can* be confusing, because you may not know you need only one CD to install Ubuntu and that the add-on CDs are, in fact, only add-ons), they could always just tuck them away somewhere... as long as they exist *somewhere*.

As it is now, there are [two community-developed add-on CDs, and they're for only 5.10 and 6.06.](https://ubuntuplus.bountysource.com/) There are no add-on CDs that I know of for 6.10 or 7.04.

You may be able to dig up an old unofficial add-on CD for 5.04, but the links may all be dead now. I'll see if I can find something for you. **Edit**: Try [this link](http://www.mrbass.org/linux/ubuntu/).

So, yeah, it's a real problem. You may want to consider using a Linux distro that has a wealth of add-on CDs. Fedora, Debian, and Mandriva all have add-on CDs for software installation.

By the way, 5.04 is *really* old. I don't think it even gets security updates any more. Of course, if you have no internet connection, you may not need security updates.

---

### Post by ugm6hr on 2007-05-28
I have seenAPTonCD
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

Has anyone used it?  It's in the Ubuntu repository.  Presumably this would allow any community member to create an "Add-on CD" for themselves or others?  It seems like a nice idea.  And all that would be required is someone to host the CD.iso for those people who only have broadband at a location other than where their computer is.

Have I got that right?

---

### Post by Ella Huovinen on 2007-05-28
Thanks for advices! I think my (current distro) Ubuntu Studio version is based on Feisty. I shall try if those older add-ons will help (as soon as I get to a place where I can download&burn them).

---

### Post by mikewhatever on 2007-05-28
Try getting vlc player form here [http://nl.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.6.release-0ubuntu4_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc_0.8.6.release-0ubuntu4_i386.deb)
To install it you may need a dependency package called vlc-nox
[http://nl.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6.release-0ubuntu4_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/universe/v/vlc/vlc-nox_0.8.6.release-0ubuntu4_i386.deb)
Once installed, vlc can play most of the popular formats, including dvd and mp3.
I haven't tried it this way, so a fit back would be more then welcome.

---

### Post by Ella Huovinen on 2007-05-28
Thank you mikewhatever!! 
I will try it as soon as I get home and tell you how it went!!

---

### Post by Ella Huovinen on 2007-05-29
The Ubuntu Add-On (old 5.04) worked so far that I got mp3's working! VLC needed some extra libraries. However, I managed to find libdvdcss2 and w32codecs.deb-packages on the net so I shall try them next.
*fingers crossed* ;)

---

### Post by SoulinEther on 2007-05-29
I was actually thinking of a certain project... Sharebuntu, or the like.... 

Basically we would release every month a snapshot of the current Ubuntu distribution on a DVD, taking the latest updates to the base software plus adding on some other extra stuff as well, since it is on a DVD and can hold more items. It would also just have a plain, constantly updated CD based on the LiveCD or AlternateCD... but better.
Here's how it's "Share"buntu: We use recordable DVDs (not rewritable, because we don't want any funky stuff going on) with a certain peer to peer mailing system (akin to Peerflix), burn a whole bunch and send em out to anybody that needs them. Then, users can simply mail the DVD to the next person who needs it...

It would all be very secure... and it could use stuff like MD5 thingies.. that I'm not 100% sure about YET, to make sure the DVD has maintained integrity and is the correct DVD.

That way, you could get all the extra features you want and you could keep getting updates for your system.

Edit... the original goal was to help those with dialup or with slow connections.. but it can help you too, lol.

---

### Post by Ella Huovinen on 2007-05-29
That's a good idea! Of course, the authentication issues needs to be thought. 
For me, the dependencies are a nightmare. I mean, you can install programs in XP with the help of USB on the fly but with Linux it almost always comes to missing libraries. 
Plus, when I  started searching I couldn't find a place where to add my home folder as a repository (I last had SUSE and it had that option clearly visible). I still haven't found that option.. But dpkg -i command is helpful.

---

