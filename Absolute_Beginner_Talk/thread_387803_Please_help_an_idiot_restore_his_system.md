---
title: "Please help an idiot restore his system"
date: 2007-03-18
forum: Absolute Beginner Talk
---

### Post by toddhd on 2007-03-18
I did something dumb. I was trying to get my network to autostart, and made some changes to my /etc/network/interfaces file which I guess weren't kosher, and now my computer goes into an infinite loop when it hits that file, and I can't seem to break out of it.

I figured it would be easy enough to boot the ubuntu live cd, and then just access the file interfaces file and remove the changes, right? The problem is, I can't seem to find the hard drive. When I navigate to /etc/network/interfaces, it is referring to the in memory (or CD, I'm not sure) copy, but certainly not the hard drive. I looked in the /mnt and /media folders, but I don't see hda5 listed anywhere.

Can anyone tell me how to access the hard drive from the boot CD (via terminal, because I'll need to sudo the file to edit it) so I can edit my file and get back in business?

Thanks

---

### Post by toddhd on 2007-03-18
Never mind, I was able to boot up a copy of DSL and fix it.

---

### Post by crispy_420 on 2007-03-18
As a side note, you couldn't see it if it was not mounted. The way around it is create a directory and tell the OS that is where the disc can be found.

But you solved your problem and that is all that matters.

---

