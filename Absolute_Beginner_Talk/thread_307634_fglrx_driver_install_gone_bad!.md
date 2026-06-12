---
title: "fglrx driver install gone bad!"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by DanFromWinterpeg on 2006-11-26
[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

Hi again,

Thanks to those helpful souls out there that save Linux newbies like myself from ourselves. [http://ubuntuforums.org/images/smilies/icon_mrgreen.gif](http://ubuntuforums.org/images/smilies/icon_mrgreen.gif)  Thanks to some people here I fixed my Synaptic Package Manager.

This time I tried installing the ATI xorg fglrx driver from the instructions for Dapper (which I am currently running) which were posted on this forum earlier, and well I restarted X and well now my video is toast.  I am just getting a black screen after the Ubuntu load screen.

I am running the vanilla i386 version of Dapper on my system.  

My hardware specs are as follows

AMD A64 3800 X2 dual core.
Sapphire 1600 Pro 512 MB
1 GB of dual channel OCZ RAM
Two Maxtor 100 GB hdd, one IDE, and one SATA
Asrock K8 Combo z Motherboard

I thought I followed the instructions correctly, but well now I have a black screen and have to run off the Live CD to use the computer at all.
Does anyone know what I did wrong?

I also have a few other questions.  The i386 version of Ubuntu I am currently running only detects one CPU core. How can I fix this?  The A64 version I have detected both just fine, but I could not run most of the software in Add/Remove Programs or in Synaptic Package Manager so I switch and now I can run more software, but this is an unexpected trade off.


I will be quiet now.

Thanks

Dan

---

### Post by 56phil on 2006-11-26
Can you give us a link to the instructions you used? BTW, nice system.

---

### Post by DanFromWinterpeg on 2006-11-26
I can't seem to find the exact link right now, but this is what I did

n a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

and then either startx if you are in console
or Ctl+Alt+Backspace if in virtual terminal.
Reply With Quote](*,) ](*,) ](*,)

---

### Post by 56phil on 2006-11-26
The last line has a typo. Try ```
sudo aticonfig --overlay-type[COLOR="Red"]=[/COLOR]Xv

```

---

### Post by DanFromWinterpeg on 2006-11-26
Thanks,

Can I put this into a terminal off the live CD to restore my video?  I cannot access the Hdd install, because I screwed up my video driver.
](*,)

---

### Post by DanFromWinterpeg on 2006-11-26
I guess this is what I get for Copy and Pasting commands into a terminal with only a vague idea of what the commands are for.

---

### Post by nickstatus on 2006-11-26
so, being kinda a "n00b" myself, maybe you shouldn't listen, because I might only make it worse, but maybe you should try to boot into a command line... maybe intervine at the grub screen and press "c" although I dont know if that  command line will accept the same commands... like i said, im a n00b

---

### Post by drphilngood on 2006-11-26
See [here]("http://www.psychocats.net/ubuntu/nox").

edit:
As for only detecting one CPU core, see [here]("http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel+picking") and pay close attention to the smp kernels.

> smp &#8211; This kernel is NEEDED to use both CPUs in a multi-CPU setting. The kernel is also required to &#8220;enable&#8221; hyperthreading in modern Pentium 4 CPUs. Also needed for dual core processors (the letters stand for Symmetric Multiprocessing). Very important to install this, as it WILL improve performance. Sorry to bold it but I think this one is the most important.


---

