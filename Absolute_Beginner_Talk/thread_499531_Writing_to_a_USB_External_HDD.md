---
title: "Writing to a USB External HDD"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by HoldenBurn1000 on 2007-07-12
Hi Guys,

Please be kind! im brand new to this yesterday!

 I now have pretty much most things working ok apart form my USB drive.

I have read some of the other posts on the matter but am still getting nowhere.

I have enabled the ntfs-config in the package mnager and ran the ntfs manager in system tools, I then get the below screen

[img]http://img528.imageshack.us/img528/5025/screenshotntfsconfigol4.png[/img]

I chose I write enable and click "ok", then nothing?

Still cant write and no further screens/options.


Any ideas?

---

### Post by Al3xK3aton on 2007-07-12
What error message is it giving you?

---

### Post by Jimmyfj on 2007-07-12
I'm not sure for the NTFS partitions but on my USB drive I had to run this command in a terminal:

sudo chown -R USERNAME:USERNAME /media/USB

---

### Post by GMachine_24 on 2007-07-12
Hi:

So, call me slow... but:


1. Can you see your USB hard drive listed in your /dev folder? (hdx or sdx) perhaps the device is numbered as well (as in hda1 or sda1).

2. Is your external hard drive NTFS formatted? I'm assuming you want it to be but I don't think you specify. Why do you want to attach a drive with the nt file system to your Linux computer?

I guess I'm not sure what you want to do so it's kind of difficult to offer more advice.

gm

---

### Post by Jimmyfj on 2007-07-12
Just came to mind that you could also try:

sudo apt-get install autofs

And when the install finishes you could simply write:

automount /dev/sdb (which should be your external USB drive assuming that your internal disk is SATA)

This has worked for me on several occasions.

---

### Post by Mostlyharmless42 on 2007-07-12
ok, i think i just fixed the same problem you have on my computer.  The problem i had was that the hard drive came from a windows machine and wasn't "safely removed".  The drive is then marked as "unhealthy" by linux and it won't let you make it read write.  All i had to do to fix this was first install the ntfs-config file and then plug it into a windows machine and safely remove it and then plug it back into my linux machine.  I hope this helps you.

---

