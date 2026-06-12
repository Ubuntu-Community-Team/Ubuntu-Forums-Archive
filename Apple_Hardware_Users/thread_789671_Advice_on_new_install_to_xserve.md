---
title: "Advice on new install to xserve"
date: 2008-05-10
forum: Apple Hardware Users
---

### Post by docfx on 2008-05-10
After fighting to get a Tiger OSX G5 2Ghz Xserve configured and setup as a DNS/webserver (to replace my aging IBM eServe running redhat w/ approx 250 client domains), I've given up and want to try it w/ Ubuntu. I've pulled the last server version 7.04 prior to 8.04, and the install seemed to go well, appears to have setup DNS and web services ok.

I've considered briefly going to 8.04, but it doesn't sound quite stable yet from what I'm seeing elsewhere in the forum.

Am getting ready to format 2nd drive to make a place for client websites, mySQL databases, etc., when I decided I should also look at LVM. It appears there's a linux LVM on sda4 of the main boot drive, but I don't recall it giving me an option for this during install, so before I go too far down this road, I'm seeking advice on both go/no go w/ LVM or is it there already? and if go, how to do it?

---

### Post by stream303 on 2008-05-11
Wow!  First confirmed install of Ubuntu on a PPC xserve I've seen!

In regards to LVM, be sure to see the release notes regarding this issue on Feisty 7.04:
[http://www.ubuntu.com/getubuntu/releasenotes/704](http://www.ubuntu.com/getubuntu/releasenotes/704)

I'm not experienced with lvm, so I'm afraid I can't help you there.  I haven't seen a server-install image for Gutsy 7.10 for PPC, although the Hardy 8.04 PPC server image is available.

I took a look at the release notes for Hardy and don't see any lvm problems specifically:
[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

Be sure to see the note about the /etc/apt/sources.list file for ppc changing to ports.ubuntu.com

Congrats on the xserve!  Hopefully someone much smarter than me can provide some lvm / stability info...

---

### Post by kokoroexchange on 2008-05-25
Couldn't resist chiming in here.  I've had 7.04 LAMP up and running on a G5 XServe (Dual 2.3Mhz) for over a year now.  It has been very stable.  Never crashed or frozen.


I'm running a Moodle site on it that has approximately 3000 registered users.  The first year was a trial phase with fairly low usage and we are now moving into more active use with an average of around 100 unique logins per day.  Could be up to 500+ very soon.

As I remember, the only difficulty I had in setting up the LAMP on an XServer was that initially the temperature monitoring of the processors etc. was not coded into the standard LAMP distribution so the fans (windfarm) would run full speed which sounds like a jet taking off. :-(  That was fixed (by someone's contribution) and everything works like a charm now.

Jason

---

