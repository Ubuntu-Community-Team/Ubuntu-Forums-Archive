---
title: "Ubuntu 7.10 on a SSD"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Mike_H on 2007-10-31
I'm going to be installing Ubuntu on a SSD, and I'd like some help and suggestions as to how to optimize Ubuntu to extend the life of the SSD.

Ideas I have so far are:

-No swap
-Using EXT2
-Disabling error logs/log messages

I've also seen someone suggest adding "noatime" to fstab. Can anyone explain what this does?  Also, can anyone tell me how you'd go about disabling superfluous/unnecessary log messages/error logs?

---

### Post by zakeen on 2007-10-31
Ive got an SSD drive and I just did a normal install and didnt really worry about anything. The stuff I have read that SSD drives are not as bad as people say they are, regarding there life span. I also read :

Current SSDs have a block write capability of 100,000 times. That value is increasing. but it's still a finite number. However, "write endurance" is actually less of a problem than it could be. All manufacturers of SSDs currently embed management software into the firmware of the SSD. One aspect of this software is that it "scores" how many times a block of memory has been written to and then reallocates "over-written" blocks to different locations dynamically. Some manufacturers go even further. SiliconSystems has a patented algorithm which practically doubles the lifetime of an SSD over simple wear leveling. Adtron actually adds a bit of spare flash blocks to be used the case where a block will no longer be usable. All of this happens in firmware and is invisible to both the operating system and the end user and, since the firmware locks out blocks at the point where they would probably fail (instead of waiting for a failure), you never actually lose the data in those blocks. Also, since it is writing that causes the problem, even when a drive locks has no space left to store data due to block lockout, you can still copy the contents to a new, usable drive.

---

### Post by zakeen on 2007-10-31
Also by the time it dies I will upgrade it to a 96gb:)

---

### Post by h4mx0r on 2008-01-26
hmm I'm just wondering about the drm aspects of hidden closed source drive firmware and how it has potential to go against any sort of encrypted mechanism. Have you ever tried running truecrypt or some other app on a regular flash drive? it doesn't work... maybe its just my noob sense tingling again :(

---

