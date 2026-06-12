---
title: "Internet Install"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by beejay54 on 2007-07-13
Hi All,

I have a used 1U Dell Poweredge that I'm keen to make into a Ubuntu LAMP server, however the CD-ROM is a little flaky and doing a traditional Ubuntu CD-ROM install has resulted in numerous failures about half way through. I've tried multiple cd's, different ISO's, no luck. Replacing the CD-ROM is not really an option for me right now either. (strangely enough I could install Win XP on this CD-ROM with no issues)

I gave up on Ubuntu after a while and was excited to see that I could do an internet install of SUSE (eg. have it install the packages directly from my local univerity's HTTP server). All I had to do was download a small ISO to burn to a CD and the Dell's CD-ROM held out long enough to get me through the install. SUSE seems to do the job, but it seems a little bloaty.

I'm still keen on trying Ubuntu on this box. I've been hearing nothing but great things!

**Is it possible to download a small ISO to a CD-ROM and do an Internet install of Ubuntu? **

Note I don't want to do a network install (you know via TFTP) but rather an internet install where I'm connecting to a public server with ISO's on it.

Any help you guys could provide would be much appreciated!

---

### Post by Vially on 2007-07-13
Last time I installed Ubuntu (yesterday) I booted the PC via LAN and then launched an Ubuntu internet installer.  Maybe you can try it like this ? [https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)

I know that you said you don't want to install via TFTP, but the solution I recommended above is only using TFTP to boot, the rest is done from an internet repository and it's the best way to install IMHO.

Good luck.

---

### Post by beejay54 on 2007-07-13
So it sounds like it's possible. Is there a CD-ISO that I can download to boot into the Ubuntu installer and select internet install? This was what I did on SUSE and it worked well.

---

