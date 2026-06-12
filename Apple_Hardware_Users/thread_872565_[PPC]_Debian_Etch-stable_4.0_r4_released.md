---
title: "[PPC] Debian Etch-stable 4.0_r4 released"
date: 2008-07-28
forum: Apple Hardware Users
---

### Post by stream303 on 2008-07-28
As a tribute to the devs that work on PPC for both Debian and Ubuntu, I'd like to point out that the latest stable release, Debian 4.0_r4 is out and should be hitting the usual download locations soon for PPC.

It looks like some specific powerpc fixes are included, along with some other nifty stuff.  I'll have to try it when I get some time, since the last Etch worked really well on my G5 iMac.  This release is considered "Etch-n-half", since it seems to be more than just the usual update - you can choose to use a newer kernel, 2.6.24 vs the original 2.6.18 for example.  Don't confuse it with Lenny-Testing which is slated for full release later this year.  This release of Etch breaks ground in some new ways.  Interesting.

I enjoy using both Ubuntu and Debian myself, and have learned lessons from each that have solved problems on the other.  Win-Win!  It should come as no surprise since our base code is Debian, and anyone running it should feel comfortable using either distro.

I thought I'd bring this to the attention of those who can't get Ubuntu working for some reason, or those who have no problems belonging to multiple communities without trying to convince ourselves about which one is best. They both are! :)

---

### Post by mfox on 2008-07-29
Any way to find out what specific powerpc fixes are included?  I tried Etch last month on my PowerBook G4 and was unable to get AirPort wireless to work.  This is unfortunate because Etch runs MOL, which neither Ubuntu Hardy nor Debian Lenny does.

---

### Post by stream303 on 2008-07-29
I only know what I've seen here:

[http://www.debian.org/News/2008/20080726](http://www.debian.org/News/2008/20080726)

It shows that it now correctly identifies PowerPC 64 (G5) systems, (although mine seemed to work ok with previous releases), and there is some hope for your Airport with b43-fwcutter and some new wireless tools.  I'm not into wireless, so I can't say for sure.

---

### Post by oswaldkelso on 2008-07-29
Also Debian Lenny is now Frozen. I know the MOL devs were racing to get it in before the freeze, hope they succeeded.

[http://lists.debian.org/debian-devel-announce/2008/07/msg00007.html](http://lists.debian.org/debian-devel-announce/2008/07/msg00007.html)

---

### Post by mfox on 2008-07-29
I don't think MOL has been fixed in the posted Lenny distribution.  I tried it a week ago and it didn't work then.  I have been following the problem as best I can with communication posted on the Debian site ([here]("http://www.mail-archive.com/debian-powerpc@lists.debian.org/msg59687.html")).  Apparently one of the programmers was able to patch MOL with the patch developed by openSUSE, but when he submitted it to the Debian team for inclusion, it was rejected by the upstream Debian team.  There are instructions of a sort to apply the patch in this set of communications, but it's not written in a way that a newbie like me can use.  Perhaps someone with more experience could write this out in "cookbook" style?

---

### Post by oswaldkelso on 2008-07-29
Yea I recon unless you really need Lenny stick with Etch and use backports for newer stuff. If Mol dies and you must have osx for work  etc. A macbook seems the way to go  or Suse if needs must (tbh the novel thing goes gets to me) Maybe someone will rescue it for lenny but it looks unlikely atm.

---

