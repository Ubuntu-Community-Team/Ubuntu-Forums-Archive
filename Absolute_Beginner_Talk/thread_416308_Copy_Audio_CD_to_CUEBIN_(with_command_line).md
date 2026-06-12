---
title: "Copy Audio CD to CUE/BIN (with command line)"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-04-21
How would I go about copying an audio CD to CUE/BIN via the command line?

---

### Post by guysmiley25 on 2007-04-21
Bump

---

### Post by guysmiley25 on 2007-04-21
Bump

---

### Post by guysmiley25 on 2007-04-21
I think I found it, I trying it now. Ie been searching for day&#347; for this. Turns out I should have been asking howto copy Playsation games lol.

[http://linuxreviews.org/howtos/cdrecording/#toc11]("http://linuxreviews.org/howtos/cdrecording/#toc11")

---

### Post by guysmiley25 on 2007-04-21
And it&#347; still going. I think what I really after is a wav/cue?

---

### Post by guysmiley25 on 2007-04-21
Ok this is really buggin me. I thought that this would be a simple task!

---

### Post by guysmiley25 on 2007-04-23
bump

---

### Post by annda on 2007-04-23
i don't think there is a linux utility for this. i looked for something similar some time ago but found nothing.

---

### Post by guysmiley25 on 2007-04-23
That is really sad!

But can we not write bin/cue, wav/cue to cd? This is strange. Maybe we need a linux verstion of .

What would be the best way to copy an audio cd if this was is not possible?

---

### Post by annda on 2007-04-23
> But can we not write bin/cue, wav/cue to cd?

you can use mp3splt utility to split an mp3 according to a cuesheet. i don't know about wav, but is should be possible too.

as for copying an audio cd, you can copy it directly or create a burnable image substituting hdc for your cdrom drive:

dd if=/dev/hdc of=image.iso

---

### Post by Journeyman on 2007-04-23
does it have to be cue/bin? if you just want to make an image of the CD you can do

# dd if=/dev/cdrom of=/file/cdimg.iso

I believe you have to unmount the cdrom before you can do that 

# umount /dev/cdrom

---

### Post by guysmiley25 on 2007-04-24
I thought that doing that would not work because audio CD has multiple tracks?

That is why I thought that a bin/cue or cue/bin would be the only way.

Only if there was a linux version of CDRWIN.

---

### Post by guysmiley25 on 2007-04-24
However I just discovered that CDRWIN has a dos version!

Now I thinking if there was a utility to mount a nfs share, or mount a ext3 file systems from dos. Then I could create a boot disc with CDRWIN.

Boot to CDRWIN boot disc. Rip my CD. then restart and boot back into Ubuntu.

I really do not want to install windows on my machine to complete this task as I really really hate it, and I would be shared of catching something off it.

However DOS a I have always got on quite well. And the best part is I do not have to install it! I can boot to the disc.

This is not the ideal solution, but one I could live with!

So has anyone got any ideas on how to access nfs or ext3 from dos?

---

### Post by guysmiley25 on 2007-06-01
I came across this, [http://www.extreme-alternative.org/CueCreator.html]("http://www.extreme-alternative.org/CueCreator.html"). And it looks really good.

However when I goto download, I get a 500 Internal Error, damn! Anyone heard of this and know where else I can get it?

---

