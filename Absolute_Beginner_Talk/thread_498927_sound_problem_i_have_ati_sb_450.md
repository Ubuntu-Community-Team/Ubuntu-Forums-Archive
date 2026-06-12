---
title: "sound problem i have ati sb 450"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by ddoong91 on 2007-07-12
i would love to get this fixed seeing as how ubuntu is a great program

ok when i googled and searched in this forum for answers they basiclly said 

type in sudo gedit /etc/modprobe.d/alsa-base
and then put this in the bottom options snd-hda-intel probe_mask=8 model=3stack
so i did that and saved and i heard thats supposed to fix it but it didnt 

so this is that link [http://ubuntuforums.org/showthread.php?t=452992&highlight=%5BSOLVED%5D+No+sound%3A+Toshiba+Satellite+a135-s2386](http://ubuntuforums.org/showthread.php?t=452992&highlight=%5BSOLVED%5D+No+sound%3A+Toshiba+Satellite+a135-s2386)

um i may need to download the newer alsamixer maybe not sure and def not sure how to if u no the code that i must put in the terminal plz do tell like the exact thing that i need to write

um not sure about anything else my computer is a sony vgc va11G

and i wish i can fix this

so plz if u guys have any clue thx

---

### Post by digital_sabotage on 2007-07-13
you're not very specific  ...just saying you have a 'sound problem'  ...is your sound card even detected? ...look under hardware info or do ```
lspci
``` ...do you see it next to 'audio device:'?

if not  ...check your bios settings on boot up ...i have seen the sound card erratically disable itself in bios for some reason on a couple of computers ...same problem in windows when on dual boot ...must be something with the boot loader

...otherwise post as much relevent info as you can and hopefully somebody can help you figure it out ...good luck with it:-)

---

### Post by expatCM on 2007-07-13
This seems to cover many bases ... you may be interested to have a look
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

---

