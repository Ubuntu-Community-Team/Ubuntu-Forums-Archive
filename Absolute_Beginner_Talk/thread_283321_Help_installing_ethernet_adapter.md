---
title: "Help installing ethernet adapter"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by tchoklat on 2006-10-24
Help,

I have bought an ethernet adapter to allow connection to the satellite DSL that I am getting soon. When I put the card in the slot my dial up modem willl not work and will freeze the system when I attempt to dial up. The adapter is a TP-LINK TF-3239DL.

Any help wopuld be appreciated!

Tchoklat:confused:

---

### Post by Phosphoric on 2006-10-24
Perhaps you have an IRQ conflict.  Is it possible to shuffle your PCI cards in to different slots?

---

### Post by tchoklat on 2006-10-24
HI,

Tried that. Nothing charged. Irrespective as to which of the five slots I put either card the Dial-up will not work if the ethernet is in another slot.

](*,)
Tchoklat

---

### Post by tchoklat on 2006-10-24
HI,

Tried that. Nothing changed. Irrespective as to which of the five slots I put either card the Dial-up will not work if the ethernet is in another slot.

](*,)
Tchoklat

---

### Post by tchoklat on 2006-10-24
HI,

Tried that. Nothing changed. Irrespective as to which of the five slots I put either card the Dial-up will not work if the ethernet is in another slot.

](*,)
Tchoklat

---

### Post by Phosphoric on 2006-10-24
Try removing modem driver.  Install ethernet driver then re-install modem driver.  Modem might take control then.

---

### Post by tchoklat on 2006-10-24
> **Phosphoric said:**
> Try removing modem driver.  Install ethernet driver then re-install modem driver.  Modem might take control then.

Hi dude,

One of the iissues is that I am unsure as to how to instal the ethernet adapter software. It came with two files for Linux2.4.+ only. They are called <makefile> and <8139too.c> There are instructions as follows;
[COLOR=Red]
[/COLOR][I][COLOR=Red]Please remember to SPECIFY "NEW_INCLUDE_PATH" in Makefile according to your linux environment. 

The object file named 8139too.o should be moved to the directory  
 /lib/modules/<linux-version>/kernel/drivers/net/[/COLOR] 
[COLOR=Red]
The driver could be brought up by the following steps: 
    'insmod 8139too' 
    'ifconfig eth0 up'
[/COLOR][/I]
Firstly ububtu will not allow me to copy to the  above directory and when I enter these commands I get the followin[I]g;
[COLOR=Red]
****ubuntu:~$ insmod 8139too
insmod: can't read '8139too': No such file or directory
t****ubuntu:~$ ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device
****ubuntu:~$[/COLOR][/I]

regards and stilll unable to use the adapter!

Tchoklat :confused:

---

### Post by Phosphoric on 2006-10-25
Sorry, I'm very new at Linux myself, perhaps somebody else can help you with the correct file location.

Don't know if it makes a difference, but the file name in the instructions was 8139.too.o and in your instruction in the terminal you left off the ".o" at the end?

---

