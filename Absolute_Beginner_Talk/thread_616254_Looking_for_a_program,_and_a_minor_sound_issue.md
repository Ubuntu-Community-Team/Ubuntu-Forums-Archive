---
title: "Looking for a program, and a minor sound issue"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Simimi on 2007-11-18
I am looking for a program to do a specific function for me. I want to be able to take a *.pdf file and convert the pages to images, so that I can read them with my pda when I am on the go (which does not support .pdf) Or on my Ds with comicbook Ds, which also supports reading zipped image files. Does anyone know a way to do this? I know of using convert (from imagemagic) to pull images from a pdf, but I need the page itself as an image, with text and all.

Any ideas?

Also, before I had Gutsy installed on my notebook, x86 edition. I had no sound. So, I went to /boot/grub/menu.lst and added "noacpi" on the kernel boot parameters line. I had sound again!

Now I have reinstalled to Gutsy x86-64 edition, and the same noacpi thing does not give me sound. I have tried a few fixes I have found about but nothing seems to wok... Here is what I believe to be the needed info to help me out.

```

(lshw -C sound)
*-multimedia            
       description: Audio device
       product: MCP51 High Definition Audio
       vendor: nVidia Corporation
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

```

Many thanks for the help once again all!

---

### Post by jken146 on 2007-11-18
I don't know of a program that will convert pdf pages to images, but you could always press [Print Screen] to get a screenshot.

---

### Post by Simimi on 2007-11-19
You know, I never thought of that... Thanks!

And, apparently, if I boot my notebook with it not plugged in, I have sound... so much for the noacpi on the kernel line...

---

