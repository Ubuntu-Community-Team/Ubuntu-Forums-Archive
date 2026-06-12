---
title: "Ubuntu Server doesn't boot"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by gloomer on 2006-11-30
I've never had a problem burning Linux Iso's before.

So I don't understand what's up here.

Ubuntu desktop iso boots and prompts me to install. I don't. It was  just a test. 

Now I insert the Ubuntu Server and reboot. It's searching for a boot cd-rom. 

Nothing found.

I don't understand.

the only other linux distro that hasn't booted for me was slackware.

Do you guys understand what's going on?

It doesn't recognize ANYTHING. It just boots normally to windows 98. It is an older computer. But it's worked fine on most distro's

---

### Post by nickburns on 2006-11-30
Make sure you do a checksum on the file, and make sure that you didn't just copy the ISO file to the cd, rather than burn the image to the cd.

---

### Post by K.Mandla on 2006-11-30
> **gloomer said:**
> It is an older computer. But it's worked fine on most distro's
How old is old? If you're using Edgy, it defaults to the 686 kernel, and that can cause havoc on an older, older machine. I tried using it on a Pentium desktop once, and it just re-cycled through the boot sequence continually.

> **gloomer said:**
> Now I insert the Ubuntu Server and reboot. It's searching for a boot cd-rom. Nothing found.
Give it a second chance. Sometimes CDROMs won't respond when it's searching for the drive, but for some reason will pick up on a second attempt. It's hardware related, somehow.

Don't forget you can install a command-line system (a server) from the alternate (installation) CD too. So if you think the server CD is somehow confusing your machine, you can get the same thing done on the alternate version.

---

### Post by gloomer on 2006-12-01
"How old is old? If you're using Edgy, it defaults to the 686 kernel, and that can cause havoc on an older, older machine. I tried using it on a Pentium desktop once, and it just re-cycled through the boot sequence continually."


Huh. I think that's what happened on the desktop Ubuntu.

It started installation. And the CD drive was making these weird clunking noises etc. I let it go for a while but then I just stopped it.

that's unfortunate :(

So it's not the Processor, no the graphics card, not the RAM, it's the kernel. 

ARGHHHH.

All I'm looking for is a nice CLI based server that has LAMP and supports Webmin.

I know it's probably not the best thing to post here in a Ubuntu forum, but would you guys have any suggestions?

---

