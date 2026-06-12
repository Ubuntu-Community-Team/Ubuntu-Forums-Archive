---
title: "Asus Eeepc 1215b- support"
date: 2012-04-02
forum: Asus Ubuntu Support (CLOSED)
---

### Post by AdamFCST on 2012-04-02
Good afternoon

Yesterday I installed Ubuntu 11.10 64nit on my Asus Eeepc 1215b where is as CPU Amd C-60 and GPU Radeon HD 6290. Netbook works like swiss watches but in the right corenr of display is an image: "AMD hardware not supported". Drivers and updates of Ubuntu are up to date. So, where is  a problem?
Thank you for your answers
Adam

---

### Post by SeijiSensei on 2012-04-02
Did you install the proprietary ATI driver by using the Additional Drivers application?

---

### Post by AdamFCST on 2012-04-02
yes i did.... immediately after first run of ubuntu on netbook i did it

---

### Post by SeijiSensei on 2012-04-02
I looked briefly at the specs on this machine, and it appears to have only the ATI card.  If, however, it's got "hybrid" graphics, with both an Intel and an ATI adapter, you should read this: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics).

My daughter's HP laptop has hybrid Intel/ATI graphics.  I had to enable a BIOS setting to gain access to the ATI device.  As I recall, however, before I changed the BIOS setting, Ubuntu didn't detect the ATI card at all.  So I don't think that's the problem you're facing, but I obviously can't be sure.

You might have to ask ATI for help.  I suppose it's possible the adapter isn't supported by the proprietary driver, or there's a more recent driver on ATI's site that would work for you.

---

### Post by AdamFCST on 2012-04-02
> **SeijiSensei said:**
> I looked briefly at the specs on this machine, and it appears to have only the ATI card.  If, however, it's got "hybrid" graphics, with both an Intel and an ATI adapter, you should read this: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics).

My daughter's HP laptop has hybrid Intel/ATI graphics.  I had to enable a BIOS setting to gain access to the ATI device.  As I recall, however, before I changed the BIOS setting, Ubuntu didn't detect the ATI card at all.  So I don't think that's the problem you're facing, but I obviously can't be sure.

You might have to ask ATI for help.  I suppose it's possible the adapter isn't supported by the proprietary driver, or there's a more recent driver on ATI's site that would work for you.
i have only radeon graúhics....i look on ati web.... thank you so much for your help :)

---

### Post by AdamFCST on 2012-04-02
problem solved!!!
i am just change FGLRX driver for offcial from amd site

---

### Post by affolterzh on 2012-04-03
You might have to ask ATI for help.  I suppose it's possible the adapter  isn't supported by the proprietary driver, or there's a more recent  driver on ATI's site that would work for you.[IMG]http://**************************/g.gif[/IMG]

---

### Post by LtPitt on 2012-04-05
I am an happy owner of the "intel cousin" of your Brazos: 1215n   :)

Enjoy your netbook: with ubuntu you get blazing speed and bleeding edge applications.

I'm loving it!

---

### Post by Linuxisfast on 2012-04-06
11.10 works fine on its younger sibling namely 1015B, also 12.04 works fine as well. I have latest ATI installed.

---

### Post by Normal01 on 2012-04-07
Hey all,
I have an Asus 1215b with AMD C60, but Ubuntu recognizes the AMD C60 as an AMD C50. In fact, if I write ```
cpufreq-info
``` on the terminal, it says me that the CPU goes from 800mhz to 1ghz, instead of 1,33ghz.

Could anybody help me?

Thanks a lot :D

---

