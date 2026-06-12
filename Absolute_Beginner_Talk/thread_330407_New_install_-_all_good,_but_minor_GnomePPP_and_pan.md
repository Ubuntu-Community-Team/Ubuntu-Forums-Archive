---
title: "New install - all good, but minor GnomePPP and panel issues"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by WMC on 2007-01-03
I've just done my very first Ubuntu installation (6.06).  My sister-in-law's aging P3 XP desktop just couldn't stand up to the onslaught of spyware and viruses, eventually sucumbing to the Project1 bug that snuck in while my niece was chatting on MSN.  I didn't have a spare Mac lying about, so I thought I'd give Ubuntu a go after a stranger gave me a disc about six months ago. 

I've tried various Linux distros over the last six or seven years and I've never had any luck getting them going.  Ubuntu, though, was a breeze.  I even managed to get an old Netcomm external modem up and running to replace the internal Winmodem, and got the Riva TNT2 video card working with the glx-legacy drivers (yay - glMatrix screensaver!).  I added the T-ish and OSX icon themes to Mac-ify it (my nieces really, really wanted a Mac), and you'd have trouble telling it apart from the real deal.  I'm tempted to give them my iMac and keep the old P3 for myself! ;)  Thanks to [**_Lauri Taimila_**]("http://www.taimila.com/ubuntuosx.php") for the easy-to-follow instructions on making Ubuntu look like OS X.

I do have a couple of issues, though.  Firstly, they're using the Network panel to connect to their dial-up ISP, activating the modem interface to connect and deactivating to disconnect.  I installed GnomePPP to make things more straight forward, but it says it can't detect the modem, even though it's working fine.  The modem is on dev/ttys0 rather than dev/modem - do I need to make some sort of link between the two before GnomePPP will see the modem?  It's no big deal - dial-up works fine with the current arrangement.  I just thought it'd be easier to have a 'click and dial' setup.

Secondly, I turned the bottom Gnome panel into a Mac-style dock by removing all the standard items, changing the colour to white, making it semi-transparent and changing the size to 50.  Drag in a few frequently used icons (Firefox, Evolution, Kopete, terminal, trash can etc) and it's pretty close to the real thing.  It looks best when the panel's 'expand' option is unticked - this keeps it in the middle of the screen like a real Mac dock.  All is well until I log out or restart - upon logging in again, the panel is about halfway up the screen.  Turning the 'expand' option on sends it back to the bottom (and if I restart with the expand option still on, it stays on the bottom).  Turn expand off, and the panel stays in the right position at the bottom of the screen, but log out and it's back to the middle.  Any idea what may be causing this, or how I could fix it?

Cheers
WMC in Canberra, Australia

---

### Post by kurup on 2007-08-07
> **WMC said:**
> All is well until I log out or restart - upon logging in again, the panel is about halfway up the screen.  Turning the 'expand' option on sends it back to the bottom (and if I restart with the expand option still on, it stays on the bottom).  Turn expand off, and the panel stays in the right position at the bottom of the screen, but log out and it's back to the middle.

Hi..am having the exact same problem of the panel that you mentioned.

Any luck so far?

---

### Post by _duncan_ on 2007-08-08
> I installed GnomePPP to make things more straight forward, but it says it can't detect the modem, even though it's working fine. The modem is on dev/ttys0 rather than dev/modem - do I need to make some sort of link between the two before GnomePPP will see the modem?

In the gnome-ppp set-up screen, you can force the modem selection to /dev/ttyS0 either by choosing from the list or manually typing it. It usually works even if the modem is not autodetected.

BTW, the correct syntax should be /dev/ttyS0, not dev/ttys0. You're missing a slash character at the start and 's' should be capital.

---

### Post by Bartender on 2007-08-08
If you've got the time (and access to broadband somewhere for the download) you might want to start over again with 7.04, the latest version of Ubuntu.  You'll probably like it better than Dapper.  Just a suggestion.  Dapper is LTS (long-term support).  Feisty isn't.  I don't see this as a big deal myself but some do.
And duncan is very good with dial-up issues, so try what he says and see what happens.

---

