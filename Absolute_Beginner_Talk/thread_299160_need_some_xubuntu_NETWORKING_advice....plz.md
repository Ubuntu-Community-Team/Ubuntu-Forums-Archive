---
title: "need some xubuntu NETWORKING advice....plz"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by cclampblues on 2006-11-13
gurus,

Ok, I have installed xubuntu (Edgy Elf, or something) and im trying to get my network card working. Its a xircom ethernet 10/100 plus modem 56. --rem56g-100  - laptop modem ethernet combo. It is installed in a (smokin hot) dell latitude cpi laptop. 266mhz pII i believe. its hooked to a dsl connection.

Ok now that you know all that. I am new to linux in general. I do not have to configure (drivers?) the hardware. I am usually pretty good at figuring this stuff out but i dont know where to start. Ive looked through the wiki stuff and couldnt find an answer there so i thought id ask here. Thanks in advance.

-cclampblues

---

### Post by dbbolton on 2006-11-13
do you have ndiswrapper, and is it a static ip ?

---

### Post by cclampblues on 2006-11-13
not sure if i have ndsiwrapper. Only if it came with xubuntu install cd.

non static ip.

---

### Post by dbbolton on 2006-11-13
run synaptics and install "ndiswrapper-utils"

there's a really detailed thread somewhere about how to use it. what i had to do for mine (broadcom) was save the drivers from my windows partition onto a flash drive, then upload thm to the ubuntu partition, and use ndiswrapper to configure them for linux use.

i'm really not sure if your xircom card requires ndiswrapper or not, but it's probably worth a try.

---

### Post by cclampblues on 2006-11-14
well i got it figured out. i didnt have to use ndiswrapper-utils -- it doesnt sound fun. as it turns out my network card was bunk. i debunked it and now i am using it to post this. thanks for the advice anyway - plugnplay saves the day. 

word up,
cclampblues

---

### Post by K.Mandla on 2006-11-14
Good deal. I was going to mention that I have almost the exact same setup on a Dell Latitude CPi -- the 300Mhz version (yowza!) -- with a Xircom RealPort PCMCIA card. Ubuntu recognizes and installs it automatically.

I can't speak for the modem side because I don't use them, but the network jack is flawless and gets ~800Kbps on a good day. Cheers!

---

