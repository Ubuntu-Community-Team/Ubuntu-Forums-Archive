---
title: "Announcing X.Org packages for Hoary"
date: 2004-11-09
forum: Announcements &amp; News
---

### Post by Daniel Stone on 2004-11-09
Announcing a long-awaited feature for Ubuntu: X.Org packages.

Since Ubuntu's public announcement in September, 'does it have X.Org?'
has been one of the most frequently-asked questions.  Until now, the
answer to that was that we were based on XFree86 4.3.0, with some
320,000 lines of patches; however, the answer to that question is now
dead simple: Yes!

For the last two weeks, Fabio Massimo Di Nitto and Daniel Stone have
been locked in a room together, and we now have packages to show for it.
The upgrade from XFree86 to X.Org should be perfectly smooth and
seamless, and it is supported across Ubuntu's three architectures:
amd64, i386, and powerpc.

This release brings many new features, and hopefully even more hardware
support than before.  This represents one of the most significant core
package updates we have ever tried in Ubuntu, and is the result of weeks
of work.

To upgrade, you must be running the Hoary tree[0]; if you simply run
a Smart Upgrade in Synaptic, or 'sudo apt-get dist-upgrade', your system
should automatically get upgraded to X.Org.  The next time you restart
GDM (either by running 'sudo /etc/init.d/gdm restart', which will kill
your active session, or by restarting the machine), you will be running
the X.Org X server.

Please bear in mind that this represents the first public release of
these packages, and as such there will no doubt be bugs to be found.  In
particular, people using ATI chipsets may experience X server crashes
when the resolution given in the configuration file is incorrect; also,
use of Synaptic may cause a very loud error about the locale being
unknown.  Copy and paste between some GTK1 applications (e.g. emacs) is
known to be problematic.

While this release also features the Composite extension, which enables
true transparency, Exposé-like functionality, etc, this extension is
still experimental.  As such, it has been disabled by default, and we
have respected this default.  If you want to enable the Composite
extension, add the following to /etc/X11/xorg.conf:
Section "Extensions"
	Option	"Composite"	"Enabled"
EndSection

but please be aware that you may experience random crashes, and
performance using Composite is still rather sluggish at this stage.
This is not an Ubuntu-specific problem: it is an architectural problem
with the current X.Org server.

That being said, if you are confident that you can deal with any
unexpected breakage that may occur, please upgrade to X.Org and give it
all the testing it needs!  If you find a bug, please report it through
our bug tracking system[1].

Cheers!
Daniel Stone and Fabio Massimo Di Nitto, Ubuntu X maintainers

[0]: See Matt Zimmerman's announcement of hoary:
[http://lists.ubuntu.com/archives/ubuntu-announce/2004-October/000005.html](http://lists.ubuntu.com/archives/ubuntu-announce/2004-October/000005.html)
[1]: [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com)

-- 
Daniel Stone                                        <daniel.stone@canonical.com>

-- 
ubuntu-announce mailing list
[email]ubuntu-announce@lists.ubuntu.com[/email]
[http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce](http://lists.ubuntu.com/mailman/listinfo/ubuntu-announce)

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.2.5 (GNU/Linux)

iD8DBQFBkONIcPClnTztfv0RAmGCAJ9ewicu7I47U/QAaoJZIcMFwe3c/wCfY+N9
N9AR/6yyTHEjvtk05+CdlMo=
=Tj4L
-----END PGP SIGNATURE-----

---

