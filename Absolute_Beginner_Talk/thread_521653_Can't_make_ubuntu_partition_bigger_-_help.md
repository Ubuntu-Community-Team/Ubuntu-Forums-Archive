---
title: "Can't make ubuntu partition bigger - help"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Keppy on 2007-08-09
I am trying to make the ubuntu ext3 partition bigger but the gnome partition editor on the live CD won't let me. As far as I know this is because the little bit of free space I have is not next to this partition, although the only partition I can make any bigger is the setup partition and not the ntfs one which is also next to it :S

Can anyone explain how I can make my ubuntu partition bigger without any formatting???

Thanks in advance.

---

### Post by oilchangeguy on 2007-08-09
i'm guessing you're running a dual boot setup. you don't define "little bit of space", but i'd leave well eonugh alone. because if this space is being used by windows, it'll need it for future growth (read, updates).

---

### Post by Keppy on 2007-08-09
Well I've got windows XP and ubuntu 6.06 dual boot, have got about 69gb for windows and 3gb for ubuntu and a 170mb swap partition in extended  (there's the system setup partition that came on my laptop too which is about 2gb) and I've run out of space on the ubuntu partition, I have freed about 500mb to add onto the ubuntu partition but I don't know how to increase the size of it as it won't just let me :(

---

### Post by louieb on 2007-08-09
You can try the [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php")  it has more features than the version on the Ubuntu live CD.

If that doesn't do it then it would help us help you if could post a screen shot of the GParted window.

---

### Post by AlexenderReez on 2007-08-09
make sure to unmount the partition before any next step.....sometime user doesn't realize this careless :)

---

### Post by K.Mandla on 2007-08-09
> **Keppy said:**
> I am trying to make the ubuntu ext3 partition bigger but the gnome partition editor on the live CD won't let me. As far as I know this is because the little bit of free space I have is not next to this partition, although the only partition I can make any bigger is the setup partition and not the ntfs one which is also next to it :S

Can anyone explain how I can make my ubuntu partition bigger without any formatting???

Thanks in advance.
If I understand you correctly, you might have to stretch the last partition to take up that free space, then scoot the start point up, to move that empty space next to Ubuntu. It could take two or three tries to get it into the right spot so you can extend Ubuntu and take up that space.

Tthe GPartEd live CD really is the best way to do this, but it might take a long time to get it all done.

---

### Post by Keppy on 2007-08-13
I have tried using the gparted live cd with the same result as the ubuntu live cd.

The only partition I can resize is the fat32 one, not the ntfs or any others :(

ideas welcome :)

[Screenshot]("http://torlordathonline.sitesled.com/Screenshot.png")

---

