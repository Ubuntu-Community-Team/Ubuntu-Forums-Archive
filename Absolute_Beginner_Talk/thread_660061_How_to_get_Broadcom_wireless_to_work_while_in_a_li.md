---
title: "How to get Broadcom wireless to work while in a liveCD environment..."
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2008-01-06
I always end up just plugging my laptop directly in to the router when I want to try a new Linux distro. Then I tried using a Fedora liveCD and I thought I would be clever and copy files from my Ubuntu /lib/firmware folder to the /lib/firmware folder for the liveCD. I had some permission problems and couldn't quite type the command correctly and since I wasn't sure it would work, I just gave up.

Should that method work? If I do that, would I have to DO something with bcm43xx-fwcutter? Like "refresh" it so it sees the new firmware files in there. As far as I know, all distros seem to have the bcm43xx driver. Is that because it's included in the kernel? (I don't even know what the kernel really does, except that it's "TEH CORE" of Linux.

---

### Post by barrack on 2008-01-06
When I was working to get my wireless to work, it required a reboot. In the case of a livecd, the reboot would lose any saved changes.

---

