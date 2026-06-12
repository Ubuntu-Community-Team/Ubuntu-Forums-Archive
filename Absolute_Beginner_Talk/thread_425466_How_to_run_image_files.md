---
title: "How to run image files?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by the_axiom on 2007-04-27
Hi!
I wonder if there's any possibility of running image files such as .bin and .iso.
In MS this would be daemon tools.

Anyone got any idea?

James

---

### Post by taurus on 2007-04-27
You can mount .iso as

```
sudo mkdir /media/iso
sudo mount -t iso9660 filename.iso /media/iso -o loop
```
You can use bchunk to mount .bin or bin2iso to convert .bin to .iso and mount as as above.

---

### Post by Compyx on 2007-04-27
You can mount .iso files by using something like this:
```

sudo mount -o loop <image_file> /media/cdrom

```

I don't know about .bin files, but there are tools to convert .bin files to .iso.

You can also browse .iso files with file-roller (the default archive-handler in Ubuntu).

---

### Post by bashologist on 2007-04-27
sudo mount -o loop "/path/to/image.iso" "/path/to/empty/directory/"

---

### Post by the_axiom on 2007-04-27
Is it necessary to convert a bin file?
I've installed bchunk, how do I run it? (alt+f2? -didnt work...)

---

### Post by bashologist on 2007-04-27
Copy and paste this to run a bin file:
```
printf '#!/bin/bash\necho "Running bin file..."; read' > file.bin; sudo chmod +x file.bin; ./file.bin
```

---

### Post by the_axiom on 2007-04-27
> **bashologist said:**
> Copy and paste this to run a bin file:
```
printf '#!/bin/bash\necho "Running bin file..."; read' > file.bin; sudo chmod +x file.bin; ./file.bin
```

I renamed my bin file to file.bin (to save some time =D).
And I typed as you told me in terminal, and got the response:
"Running bin file..."
But what know...? How do I see the files ? :/

---

### Post by Josey on 2007-04-27
there is a gui for this in add/remove programs if you like that kind of thing.

as people above stated though it can simply be done with terminal.

the gui program is called gmount-iso

the first option is the .iso file... the second is where to mount to.

---

### Post by whee on 2007-04-27
> **taurus said:**
> You can mount .iso as

```
sudo mkdir /media/iso
sudo mount -t iso9660 filename.iso /media/iso -o loop
```
You can use bchunk to mount .bin or bin2iso to convert .bin to .iso and mount as as above.

That's just an awesome feature, i didn't know about that one yet.

---

### Post by bashologist on 2007-04-27
> **the_axiom said:**
> I renamed my bin file to file.bin (to save some time =D).
And I typed as you told me in terminal, and got the response:
"Running bin file..."
But what know...? How do I see the files ? :/

You renamed it file.bin?!!! That's not good... It was meant as a joke. ](*,)

---

### Post by the_axiom on 2007-04-27
> **bashologist said:**
> You renamed it file.bin?!!! That's not good... It was meant as a joke. ](*,)
I cannot in any way figure out how you consider that as a joke? Was the whole code a joke or only the "file.bin"? Why is that not good? I could easily rename it back again as well.
In case you wanted me to replace the "file.bin" with my bin's filename, I saved time by renaming my bin file instead....

---

### Post by mckryptyk on 2007-05-10
bchunk /path/to/name.bin /pat/to/name.cue /path/to/name.iso

man bchunk

'nuff said :)

---

