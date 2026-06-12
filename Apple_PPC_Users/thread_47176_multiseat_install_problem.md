---
title: "multiseat install problem"
date: 2005-07-07
forum: Apple PPC Users
---

### Post by chascon on 2005-07-07
I thought I'd post about this problem I'm having.  I've already posted at bugzilla, but in the interest of transparency here it is.



Ubuntu boots fine from the CD and the install appears normal until it reports
that it has been unable to install the multiseat package.  No further details
are given and it looks as if it would be poosible to continue installing other
packages.

Target machine is a twin CPU 200MHz Pentium Pro NCR box with 256 meg of memory,
installing to a 4 gig SCSI boot disk (single partition).

Is there somewhere I can check for more details of the error ?

I've reverted the machine to Windows 2000 which boots, loads and seems to run
OK.  Machine is currently grinding out seti@home on one CPU and
[www.ud.com/cancer](www.ud.com/cancer) on the other without any indication of underlying hardware issues.

Any thoughts on where to start looking for the problem appreciated !


Cheers, J/.

 ------- Additional Comment  #1 From  Matt Zimmerman  2005-06-28 01:00 UTC  ------- 
When you are asked to choose your language, select "Go back" and run a CD
integrity check from the menu

 ------- Additional Comment  #2 From  mcepeda  2005-07-07 20:53 UTC  ------- 
I'm having the same problem on a 400 mhz iMac DV and hoary ubuntu and kubuntu install CDs, regardless of 
server install or default,  I tried three cds that burned propperly with xcdroast (I know how to do), and 
their md5s checked out.

Since it's third CD and all the md5s check out, I highly doubt it is an issue with data corruption on the 
CDs.
by the way, these settings:
linux multiseat-udeb/disable_multiseat=true
at the first prompt didn't work either.  It gives: cd:2,linux: Unkown or corrupt filesytem


Update:
I tried a fourth atttempt using the burner called firestarter, something I've burned warty with 
succesfully, and I get the same failure.

Checking CD-ROM integrety says,
"Integrety test successful.  The CD-ROM integrety test was successful.  The CD-ROM is valid".

Setting, 'linux multiseat-udeb/disable_multiseat=true' does not reap different results as before with 
earlier CDs.

PS-The burned CDs have been both CD-W and CDRWs.  So this seems to not be a physical problem but a software 
one.

---

### Post by chascon on 2005-07-07
What is this multiseat, and might one be able to just skip it using the setp by step selector?
I assume so as that is what the line command attempts to do.
I'll try this and get back.

---

### Post by Len on 2005-07-07
This multiseat is something that allows multiple users to use the same system with multiple keyboards/mice and graphic cards/screens. According to the dev mailing list it is pretty useless right now (only works with very few configurations), and I guess you're not going to use it if it was useful as well so yes, you can easily skip it.

I have no idea how to do that though... but it causes a helluva lot of problems for some unneeded beta package. Is there already a bug reported about this?

[quote="meager description from the Ubuntu site"]
administration and configuration tools for multiseat systems
multiseat-udeb[/quote]
[quote="... a more clarifying mail from the dev list"]
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA1

Asheesh Laroia wrote:
> I am trying to run a multiseat system, so more than one user can log in
> to the same computer and get a graphical interface.  I have two
> keyboards and two mice connected to the same computer, and two monitors
> each attached to separate ATI Radeon video cards.  (A PCI Radeon 7000
> powers one monitor, while an AGP Radeon 9250 powers the other.)
> 
> With Debian Sarge, I had a setup where init scripts would start X
> servers, and GDM would only run Xnest rather than a real X server. 
> Performance wasn't great, and every once in a while one monitor would
> just go blank (perhaps the other one went to DPMS sleep).
> 
> I noticed the multiseat udeb in the new Hoary system, so I installed
> Hoary instead.  I can get separated keyboard and mouse input on the two
> X servers in Hoary, but when one X server quits (e.g., when a user logs
> out), the second monitor goes blank.

The multiseat system is quite experimental at the moment and it has
some hardencoded values before the udeb can kick in. Basically you
need to have atleast 4 gfx of the same manufacturer to allow multiseat
configurator to run.

We are planning to relax these defaults for breezy, but since the code
is quite experimental and it will be object of several changes, we
restricted it to the 3 setups we have for developing these tools.

Stay tuned :)

Fabio[/quote]

Oh, and if the installer passes the media check you can be 100% sure it is OK. All the packages have a checksum as well (which the installer probably checks when doing the media check), and if the CD boots you can be sure the bootloader is OK as well :P. OS X Disk Utility and Toast also verify a disc after burning, but that doesn't say it will run OK in another drive as well. I must say that I'd had done the same in your case as well though, to be sure.

Good luck! Maybe you can ask how to disable it in the dev mailing list if you get stuck...

---

### Post by chascon on 2005-07-08
The bug is posted.  It's at:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11912](https://bugzilla.ubuntu.com/show_bug.cgi?id=11912)

I was able to circumvent the multiseat install failure using d-i's step by step menu selection.  On the first pass it fails after naming hostname.  You're still missing filling out the domain name, so I selected 'back' and reran network configuration (or the like).  The second time around it fails after setting domain name, which is what I wanted.

Just a few notes if anyone is  interested in installing a fast minimal install (with XFS or any other fs):
[http://ubuntuppc.info/61.html](http://ubuntuppc.info/61.html)
I'll also make it a thread so people can contribute towards enabling the cups webinterface, and editing font sizes manually.

---

