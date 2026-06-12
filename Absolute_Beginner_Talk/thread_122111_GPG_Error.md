---
title: "GPG Error?"
date: 2006-01-26
forum: Absolute Beginner Talk
---

### Post by Mike_N on 2006-01-26
I just re-installed Ubuntu 5.10 and ran Synaptic and Automatix... Everything seems fine but i just got this error while checking for updates... Any ideas?

W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088

---

### Post by arnieboy on 2006-01-26
[QUOTE=Mike_N]I just re-installed Ubuntu 5.10 and ran Synaptic and Automatix... Everything seems fine but i just got this error while checking for updates... Any ideas?

W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088[/QUOTE]
[http://ubuntuforums.org/showpost.php?p=681703&postcount=1534](http://ubuntuforums.org/showpost.php?p=681703&postcount=1534)

---

### Post by Mike_N on 2006-01-26
WOW... That was easy... Thank you...

Now, since i'm new here, can someone explain to me what went wrong and how those commands fixed it, so i can learn from my mistake and not repeat it? Thank you... :)

---

### Post by arnieboy on 2006-01-26
[QUOTE=Mike_N]WOW... That was easy... Thank you...

Now, since i'm new here, can someone explain to me what went wrong and how those commands fixed it, so i can learn from my mistake and not repeat it? Thank you... :)[/QUOTE]
u did not do any mistake. automatix added the KDE 3.5 repos but since they are unsigned by default and u need to add the gpg keys explicitly, this trivial error occured. not a big deal and  the next version of automatix will add this key by default.

---

