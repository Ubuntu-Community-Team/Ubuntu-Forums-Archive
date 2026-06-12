---
title: "[help] clamav issue"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by pcandpc on 2007-06-09
Hi,

During system updates, I always see something
along the following:

libclamav2
clamav-base
clamav-freshclam

I suppose this is due to the clamav antivirus, but
I'm not running it at all.

How can I check if it's running, and if so, can I disable it?

And, besides this clamav, are there any other antivirus tools
that ubuntu supports?

Thanks.

---

### Post by milton1 on 2007-06-09
antivirus needs in linux are few to none. Clamav is good, but not necessary. Freshclam is the updater program. It will most likely run as a cron task (on startup, or something similar). the actual scanner is activated manually using the command 'clamscan'. To my knowledge, there is no on-demand scanner in clamav.

---

### Post by pcandpc on 2007-06-09
Thanks.

So, if I don't want clamav at all, how do I cleanly
remove it from the system such that I don't see
any clam related updates during system updates?

---

### Post by smoker on 2007-06-09
probably the easiest way is through 'synaptic package manager', search for clavav, and mark it for complete removal, and apply.

---

