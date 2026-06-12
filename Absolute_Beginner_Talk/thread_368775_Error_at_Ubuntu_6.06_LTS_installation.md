---
title: "Error at Ubuntu 6.06 LTS installation"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by Pedroca on 2007-02-23
Hello,
Weel, i just received my Ubuntu Cd from mail, and when I'm trying to install it, the systems loads the kernel but shows me this issue:

Uncompressing Linux... Ok, booting the kernel.
[17179571.792000]PCI: failed to allocate mem resource #6: 20000@50000000 for 0000:01:00.0

and stops ther, i already run memtest twice, without an error detection.

If you guys can help me, y pc is the following:

Intel DG965SS
Core2 Duo E6300
2 x 512 MB DDR2 533 GENERICA
HD SAMSUNG SATA 2 160Gb (2 part - C:\ Windows Xp Media Center; D:\ no OS)
GeForce 7300 GT

@ PCI there's an Creative Sound Blaster! 5.1 and a Dial-up

thanks for the helps:)

---

### Post by netkid91 on 2007-02-23
It's either a problem with your Sound Card or modem, try unplugging them one at a time and see what happens.

---

### Post by Pedroca on 2007-02-23
Thanks for your reply, i just tried that, but this prblem stand still...

do you think there's anything to do with the MoBo chipset ?


should i try higher latency for PCI ?

TKs

---

### Post by netkid91 on 2007-02-23
Odd, did you take both of them out at the same time?

---

### Post by Pedroca on 2007-02-23
yep
first I took of the sound card and tried...same error
placed the sound card back
and took off the modem...same error
removed both and the error pop out again...
=(

---

### Post by netkid91 on 2007-02-23
Well then, it's an error with one of your MoBo's integrated peripherals.  What model is you motherboard?
Edit: NM, noticed that the intel product you listed is a mobo, thought it was a chipset for a moment.
[This]("http://www.blindedbytech.com/2006/11/10/how-to-install-fedora-core-6-on-intel-dg965ss-motherboard/") will help you, I know it's fedora, but the same principles apply to Ubuntu

---

### Post by Pedroca on 2007-02-24
ok, i have just tried this

check if i did something wrong...
set my sata drivers as AHCI
when the option "install with graphic mode" came out i hitted F6 and tiped:
boot=linux all-generic-ide pci=nommconf
the screen load lots of codes
and stopped
:( :( :( 

Note:
Fedora already uses 2.6.18 kernel, that have the 965 chipset support, but my ubuntu is 6.06 LTS, with 2.6.16 kernel and the 6.10 uses the 2.6.17 kernel

Do you think there's anything else i can do ?

Tks for the patience man :)

Edit: ow, if there's a way to update the kernel after its installed it could help a lot later

---

### Post by lwc on 2007-02-24
Down "Feisty Fawn Herd 4", which is the development release, and then the SATA problem will be gone.

(To be short, the kernel of Ubuntu 6.10 does not support SATA well)

---

### Post by Pedroca on 2007-02-24
Isn't Feisty Fawn Herd @ tests phase (Alpha i believe) ?

---

### Post by hyper_ch on 2007-02-24
Well, the alpha release on ubuntu is sort of a stable release in windows :)

---

### Post by Pedroca on 2007-02-24
lol ?
well, but about drivers and programs, are they avaliable for this alpha as well for ubuntu 6.10 ?

---

### Post by hyper_ch on 2007-02-24
I tend to think feisty will support more newer hardware and less older ones... but I don't know for sure.

---

### Post by v8YKxgHe on 2007-02-24
If you are new to Linux/Ubuntu I highly suggest you do _not_ install Feisty. Feisty Fawn is the latest development version of Ubuntu to be release April (19th?) 2007. Feisty _will_ break and should only be used by those who know how to fix problems and can work their way around Linux well enough to fix problems. 

I'm not sure for certain, but you're motherboard may us the JMicon IDE/SATA controller which there is a major bug with the Linux Kernel and the controller, it makes it impossible (or very hard) to even boot/install Linux. I've seen people saying recently that the latest JMicron BIOS update fixes this bug and all should work fine.

Go to you're motherboard manufactures website and download a new BIOS from there (the website should give instructions on how to install the new BIOS).

But please ... don't use Feisty if you're new. It may be stable for now, but it could and can break.

---

### Post by Pedroca on 2007-02-24
gonna update bios in a second...


PS:  i tried ubuntu on my second pc (actually, my mother pcs) and guess what...

when i was leaving the pc she asked what i were using, i explained and she said "ow, let me see it pls..." now she doesnt want return my cd!

---

