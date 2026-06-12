---
title: "netowrking problems FOR A BEGINER"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by TrIde2188 on 2006-08-31
right i posted this in the wireless apart..seems to ahve gone dead =/

seeing as im a beginner(meiang i know a fair few commands but thas about my limit) at linux and coding and sutff i thoughtid give it a try in this section

ive got a dwl-G650 C3 rev wireless netwrok card...one light comeso n and stayson... ive got it (fdue toa friend who uses linux) so that when the card plugs in it laods the appropriate driuver.s.it does load them i sused lspci ( i think) to find that out.. BUT its just not detecting the card in ifconfig whatsoever =/

any help would be lvoed... seeing as ive had this problem for a week now being on here and having ppl trying to help over msn =/and its starting to bug my patience :P


--TrIde

---

### Post by kidders on 2006-08-31
Hi there,

Have you tried lsmod to check for the loaded driver? (Strictly, lspci only tells you the kernel knows the name of the card, not that it can actually work it.) The other thing you can check is your dmesg content ... when the kernel notices your card, you should see some messages, and when it loads the driver for it, you should see another set.

Assuming you get that far, try using "ifconfig -a" instead of "ifconfig". It'll force *all* your network adapters to display, even if they're broken or not set up.

If you've already checked all this, sorry ... but there's plenty more to try, once we know what kinds of error messages you're getting :)

One thing to bear in mind is that the driver the kernel is loading might be *slightly* incompatible with your card ... which card/driver combination are you using? Wireless cards can be **HELL** to set up in Linux btw ... if your problem's not an obvious one, the next couple of days could be very unpleasant!!

---

### Post by TrIde2188 on 2006-08-31
Thanks alot for the reply

i knew it was ls somehting lol

lsmod shows the loaded driver whihc lately me and my friend are positvie atrethe drivers for it are

ath_pci
ath_rate_sample
wlan
ath_hal

onne needs the others etc ..

well if itake out my card put it back in..nothign happens it isnt recognized.. so i take it out put it back in it is..its only recognized eveyr second time
but nayway
i tpyed in dmesg

after replugging in my device (twice)and thsi was added on the end

PCI: Enabling deice 0000:06:00.0 (0000 -> 0002)
ACPO: PCI Interupt 0000:06:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
ath_attach:unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
ACPI: PCI interupt for device 0000:06:00.0 disabled

and the light is back on on the wireless card only showing power =/

ifconfig -a

only shows hte same as ifconfig

lo
and
sit0

---

### Post by kidders on 2006-08-31
Oh hell.

I may be **way** off base, but it almost looks as though your hardware might be too new for the driver you're using. (I'm assuming it's a generic kernel module.) Either that, or you've fallen victim to a bug.

One of the things you'll find about drivers in the kernel tree is that they don't tend to get upgraded terribly often, which is why I tend to try to avoid them. ALSA is a good example, where (on my Gentoo Linux box, at least) I deliberately disable my sound card driver and use the (more frequently updated) one from the ALSA website instead. This means I can benefit from upgrades & bugfixes *before* they make it into the kernel proper. I wonder if a similar approach would solve your networking problem?

I'm gonna look into it for you ... I'll post back if I find anything!

---

### Post by TrIde2188 on 2006-09-01
Hmm okay thanks for the help i kinda half get what you mean lol
Ah okay cheers dude =) 
and again thanks for helping me out!!

--TrIde

---

### Post by kidders on 2006-09-01
No problem :)

Basically, I'm looking for a way you could substitute the driver you're currently using for one that's updated more frequently than the one in your kernel.

I *may* have struck gold ...

First, check that the bus ID of your device is 168c:0013. If it is, the following will **definitely** work for you, If not, this is worth trying anyhow though.

Take a look @ [http://madwifi.org/](http://madwifi.org/) and download their latest driver. It doesn't seem to be available in a format that's suitable for Ubuntu beginners out of the box though, so let me know if you need me to walk you through the installation. I can't seem to find it in Ubuntu's package database either :(

If you *do* get it installed though, be sure and remove *absolutely* all wireless card drivers you've installed up to now, so they don't cause conflicts.

---

### Post by TrIde2188 on 2006-09-01
Ah right ok

first how do i find the bus ID?

andi downloaded the madwifi driver... put it on my usbpen... then plugged it into my laptop but it seemed to be the source code =/ (according to my friend the linux using lodger lol) 
and i didnt know how to open it as it was a tar.gz =/

just lookign at the download site now
do i wnat the 

tar.gz
or the tar.bz2?

=/

---

### Post by TrIde2188 on 2006-09-01
ok so far ive managed to get make clean and make to work ish..

it turns out theres another error in make =/
ive installed gcc-3.4 and all dependciesit works fine....

erm

bascially im not usre what the error is :S it jsut says ..error lol

erm the lodger friend has helped a bit but hes stuck for choices and thinks its something not in the compiling but in the configuring he thinks =/

erm apart from that i have no idea what to do next =/

the make tho did go further than before (coz i have gcc-3.4) so tahts a gd sign at least

---

### Post by TrIde2188 on 2006-09-01
is everyone dead then eh? =[

---

### Post by kidders on 2006-09-02
Hmmmm. you're probably missing a dependency. For the madwifi daily snapshots ...```
apt-get install build-essential bin86 gcc-3.4 linux-headers-$(uname -r);
cp /boot/config-$(uname -r) /usr/src/linux-headers-$(uname -r)
```should pull in anything that's required. The second line is just in case your kernel config isn't where it's supposed to be.

---

### Post by TrIde2188 on 2006-09-02
apt-get dont work no internet ;) lol

---

### Post by TrIde2188 on 2006-09-03
nudge nudge

---

### Post by kidders on 2006-09-04
You can download the required packages someplace else and **apt-get install** them that way.

---

