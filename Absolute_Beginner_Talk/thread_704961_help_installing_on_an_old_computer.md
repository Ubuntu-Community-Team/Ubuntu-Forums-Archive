---
title: "help installing on an old computer"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by ispy on 2008-02-22
i have an old computer, older than me (16), and i can't get it to boot from the CD drive. i tried a Debian exe method, but that didn't work. couldn't get past grub... so i'm looking for an alternative... i have an active internet connection, just need a medium to get linux on and the chains off...

---

### Post by freebeer on 2008-02-22
Posting the machine's specs would help.  CPU, Memory, etc.

---

### Post by santiagoward2000 on 2008-02-22
> **ispy said:**
> i have an old computer, older than me (16), and i can't get it to boot from the CD drive. i tried a Debian exe method, but that didn't work. couldn't get past grub... so i'm looking for an alternative... i have an active internet connection, just need a medium to get linux on and the chains off...

Hi!
Could you post your pc's specs? If it's too old, you may want to try with an AlternateCD to install Ubuntu, but I can't guarantee it'll run once it's installed.
Perhaps you should try an lighter distro, like Puppy or DSL.
Cheers!

---

### Post by Presto123 on 2008-02-22
One thing I can see from a computer of that age is that it will NOT have enough RAM or CPU strength. I wouldn't even know for sure what kind of other distro would work on that thing, really...POSSIBLY Puppy Linux.

---

### Post by TravMan63 on 2008-02-22
Try DSL - with a boot floppy

As stated: machine specs?

---

### Post by ispy on 2008-02-22
it's had a couple upgrades, runs win2k fine now, so i think it might handle Xubuntu, but i can't seem to get it to install from a disk. I can't get into the BIOS. so the distro isn't a problem, it's the fact that i can't install anything from CD.

---

### Post by monte48lowes on 2008-02-22
Have you tried the CD case smoosh?

When the BIOS splash screen comes up, press down all of the F keys at once using a CD case.

Mike

---

### Post by paultag on 2008-02-22
> **monte48lowes said:**
> Have you tried the CD case smoosh?

When the BIOS splash screen comes up, press down all of the F keys at once using a CD case.

Mike

What? This will do nothing!
I can see F1, etc -- just look for what F Key it is!! (also might be del, or F6-F12)

---

### Post by Joeb454 on 2008-02-22
**monte48lowes** what are you talking about?

The keyboard buffer would overflow and your computer would beep. What good is that?

---

### Post by ispy on 2008-02-22
can i just hold them down? i think i'm getting a BIOS screen, but it's only for half a second at most. every time i try to hit it, i'm too late...

Edit: I know it's f10. but my timing is bad, and it takes ten minutes just to get to the bios splash.

---

### Post by santiagoward2000 on 2008-02-22
> **ispy said:**
> it's had a couple upgrades, runs win2k fine now, so i think it might handle Xubuntu, but i can't seem to get it to install from a disk. I can't get into the BIOS. so the distro isn't a problem, it's the fact that i can't install anything from CD.

Ah... You need to edit your BIOS setup. When you are booting, you shold see a message that says something like:
> Press F2 for BIOS setup
The key may be another, like del for example. Press it. Once you enter, look for boot options and put your CD drive first in the boot order. Then save, exit, and try again.
Tell us how that goes.
Good luck!

---

### Post by Joeb454 on 2008-02-22
If the key to enter BIOS is F10, then when you boot up just keep hitting F10 :)

---

### Post by ispy on 2008-02-22
thanks for the reply, but what i'm wondering is, because i'm curious, i heard about [this]("http://goodbye-microsoft.com/") and tried it. but now it won't boot into Linux, but it will boot into window$. so if there's something else out there similar that i can use, then by all means, tell me about it. i'm always open to new things. this is my 4th old machine in my room, so i'm looking to try something different...

but thanks for your responses. i'll look into it.

---

### Post by Joeb454 on 2008-02-22
I have no idea what that is. As far as I know, Debian has never distributed .exe files

Be wary of it :)

---

### Post by Presto123 on 2008-02-22
I talked to my brother about computers of this age (he has messed with computers for a long time) and he suggested that you should look on your mobo for a holographic sticker (Used to single-out the bios) get the numbers or any information it lists and attempt to Google it to find the actual key.

Oye...you got yourself a fun little project. :lolflag:

---

### Post by ispy on 2008-02-22
thanks. found a cool site, uses Wubi and a torrent file to install without a CD. i don't particularly care about this computer, so i'm just gonna do it. experiment, you know?

---

### Post by monte48lowes on 2008-02-23
I have actually used the CD case smoosh before. Not all BIOS splash screens give information on which key to press. It does work if it's one of the F keys. 

Mike

---

