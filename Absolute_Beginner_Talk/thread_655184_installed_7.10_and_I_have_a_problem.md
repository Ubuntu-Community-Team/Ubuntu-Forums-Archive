---
title: "installed 7.10 and I have a problem"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Blahman2 on 2008-01-01
I just installed 7.10 with the cd I got throught the live cd, and when I try to boot it I get nothing but a black screen. Live CD works fine but trying to run it without the cd it gives a problem, what have I done wrong?

---

### Post by Sef on 2008-01-01
1) Does the BIOS come up at all or just blank from the start?

2) system specs?

3) graphics card?

---

### Post by alienexplorers on 2008-01-01
Try booting into recovery mode, login, and enter the following code at the prompt.
> sudo dpkg-reconfigure xserver-xorg
Select the best answers to the questions and see if it helps.

---

### Post by hyper_ch on 2008-01-01
in the recovery mode you don't need the "sudo".

---

### Post by BL00dFox on 2008-01-01
Too Many people have had their X SERVER crash and have had to reconfigure. The developers, IMO, seriously have to do something about that, by making it more stable, etc...

---

### Post by hyper_ch on 2008-01-01
xserver has never crashed for me...

How do you come to your conclusion?

---

### Post by BL00dFox on 2008-01-01
> **hyper_ch said:**
> xserver has never crashed for me...

How do you come to your conclusion?

Look around in the forums... You'll know what I mean. XServer crashed for me randomly when I was trying to install ATI drivers, but then now I have nvidia, its doesnt happen anymore =]

---

### Post by hyper_ch on 2008-01-01
well, it's a support forum. Do you think people come here and tell "hey, I just installed my ubuntu and the xserver did not crash"? It may appear as many people have problems with xserver (because of ati drivers) but compared to the total number of installations it's not that many I tend to think.

---

### Post by Blahman2 on 2008-01-01
not so sure on the specs, Its a laptop with a ati radeon pentium 4 with a 2.4 512mb ram. Whats the password and user name I use for recovery mode?

---

### Post by jken146 on 2008-01-01
> **Blahman2 said:**
> Whats the password and user name I use for recovery mode?

You don't need one.  It automatically logs you in as root.

---

### Post by Blahman2 on 2008-01-01
ok... well figured out the problem... For some reason I need to hit ctrl+alt+f1 to get it to fully boot up, why is that?

---

### Post by Blahman2 on 2008-01-02
any help?

---

### Post by jken146 on 2008-01-02
Did you try ```
dpkg-reconfigure xserver-xorg
```?

---

### Post by iansane on 2008-01-02
> **hyper_ch said:**
> well, it's a support forum. Do you think people come here and tell "hey, I just installed my ubuntu and the xserver did not crash"? It may appear as many people have problems with xserver (because of ati drivers) but compared to the total number of installations it's not that many I tend to think.

Hey I just installed and my xserver did not crash!!! LOL 

I keep hearing from people with laptops and ati video crashing or having trouble getting the right drivers. That and wireless drivers. Too bad I can't just strap my gateway desktop on my back and carry it around. I dred getting a laptop and trying to get ubuntu on it.  Oh well... would still be better than Vista

---

### Post by hyper_ch on 2008-01-02
Well, the problem lies with ATi and not with ubuntu as ATi is not willing/capable to write correct drivers or opensource them... pretty much the same goes for the broadcom wifi chip.

---

### Post by Coppper on 2008-01-02
I have that problem (i mean the black screen when booting ) , and my laptop  uses ATI .. Any solutions to that ?? 
I have a dual boot Vista - Gutsy Gibbon

---

### Post by stalkingwolf on 2008-01-02
I have fiesty on my Toshiba Tecra.  One little tweak in the wifi configuration and no problems.  I even have a choice of 3 different ways to connect wirelessly.  2 different USB sticks and my PCMCIA card.

---

### Post by Enginirical on 2008-01-02
Yup I too got to experience the hell that is getting ATi drivers to work in ubuntu, BUT Gutsy had no such issues - worked first time! I think all these issues people are talking about here are more for older distro's.

BUT I too now get a black screen when booting, no biggie though, it still boots, I just don't get to see what is going on behind the scenes until the splash screen comes up. A while ago it would'nt boot at all, but I found booting in safe mode didn't give a blank screen and soon found the problem and the simple solution in these awesome ubuntu forums!

---

### Post by Blahman2 on 2008-01-02
> **jken146 said:**
> Did you try ```
dpkg-reconfigure xserver-xorg
```?

just did.... says it must be run as root???

---

### Post by hyper_ch on 2008-01-03
yes, its a system-wide configuration, hence you need to run it as root -->

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

