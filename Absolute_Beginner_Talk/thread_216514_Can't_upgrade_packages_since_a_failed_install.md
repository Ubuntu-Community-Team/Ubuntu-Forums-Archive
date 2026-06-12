---
title: "Can't upgrade packages since a failed install"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by Books on 2006-07-15
[SIZE="2"]I'm using Kubuntu-Breezy. I used the Adept Manager to install a music notation program called Lilypond and the installation failed. Ever since Adept won't let me install or upgrade *any* package without complaining of a lilypond package missing.

For example, I just tried to install the Kile editor, and here is the error message that Adept gave:

[INDENT][FONT="Courier New"]Preconfiguring packages ...
(Reading database ... 91226 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9~breezy1 (using .../lilypond-data_2.6.3-9~breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Selecting previously deselected package tetex-base.
Unpacking tetex-base (from .../tetex-base_2.0.2c-8_all.deb) ..
^dpkg run finished![/FONT][/INDENT]

Why would Adept have a problem with lilypond when that's not even what I'm installing?

Then it shows a pop-up message:

[INDENT][I]Could not commit changes - Adept
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.[/I][/INDENT]

Then it gives a crash error message...

[INDENT][I]Adept Manager - The KDE Crash Handler
The application Adept Manager (adept) crashed and causeed the signal 6 (SIGABRT).[/I][/INDENT]

Anyone have an idea what's going on?

Thank you!!![/SIZE]

---

### Post by dtfinch on 2006-07-15
There's a related thread here:
[http://www.ubuntuforums.org/showthread.php?t=103013](http://www.ubuntuforums.org/showthread.php?t=103013)

---

### Post by Books on 2006-07-17
> **dtfinch said:**
> There's a related thread here:
[http://www.ubuntuforums.org/showthread.php?t=103013](http://www.ubuntuforums.org/showthread.php?t=103013)

That thread was very helpful! Problem solved. Thanks!

---

