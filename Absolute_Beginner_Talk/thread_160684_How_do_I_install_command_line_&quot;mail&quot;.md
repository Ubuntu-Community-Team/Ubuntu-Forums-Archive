---
title: "How do I install command line &quot;mail&quot;"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by Thunderbird750 on 2006-04-15
Unfortunately, when I search for "mail" in Synaptic,  get a huge list back.  Would someone tell me what the minimum package is to install "mail" as a effective command line tool?

---

### Post by 5-HT on 2006-04-15
Should be 'mailx' for the traditional mail user agent.

```
sudo aptitude update
sudo aptitude install mailx

OR

sudo apt-get update
sudo apt-get install mailx 
``` The package depends on postfix, but if you install a different mail transport agent prior to installing mailx, you can get around this.

This thread (esp. latter posts) may be of help: [How To Install the right mail server for your needs ]("http://ubuntuforums.org/showthread.php?t=132398")

HTH

---

### Post by Thunderbird750 on 2006-04-15
[QUOTE=5-HT]
The package depends on postfix, but if you install a different mail transport agent prior to installing mailx, you can get around this.

This thread (esp. latter posts) may be of help: [How To Install the right mail server for your needs ]("http://ubuntuforums.org/showthread.php?t=132398")

HTH[/QUOTE]
Thanks much, I'm sure I would have struggled with postfix.  Based on the refered Howto, I installed esmtp-run, then mailx.

Did some searching, and found this to be a nice "quick config" for esmtp-run:
[http://ubuntuforums.org/showthread.php?t=56077&highlight=esmtp-run](http://ubuntuforums.org/showthread.php?t=56077&highlight=esmtp-run)

Thanks HTH!

---

