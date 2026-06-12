---
title: "[SOLVED] Looking for an Ubuntu friendly video card.  AGP + DVI, min 128 mb DDR, possi"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by icceric on 2008-01-24
Hi.  I have an extra Apple 20" Cinema Display that I would like to hook up to my old dusty PC to use with Ubuntu.  I currently have a PNY NVIDIA GeForce 5200 FX, 128mb, but only VGA outs.  So I need something new with DVI outputs to run my ACD (with ADC to DVI connector) that won't cause me a lot of fuss with Ubuntu.  I'm hoping to find something on eBay for $50 ish.  What card should I go for that will require little work if any to use full throttle?

BTW, it has to be AGP

Thank You for your expert advise!

Regards,
Eric

---

### Post by mikeyphi on 2008-01-24
Sorry - can't advise on any specific card but this site will at least tell you if your chosen card is known to work under Ubuntu!!
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

---

### Post by louieb on 2008-01-24
**nvidia 7300 gt**. I have the pci-e version - works in Ubuntu out of the box. 
Saw some agp versions on ebay  in the $50 price range.

---

### Post by andrewjoy on 2008-01-24
I can confirm that the nvidia 7950GT 256Mb GDDR3 works just fine under ubuntu my home PC is running 7.10 and that card and it works out of the box. All you have to do is enable 3rd party drivers you will get a pop up bloon on the top righthand side of the screen if you are running gnome.

---

### Post by hyper_ch on 2008-01-24
generally nVidia cards are linux friendly

but the most friendliest cards I think are from intel - however I don't know what you want to do with your card.

---

### Post by Yoke &amp; Chung on 2008-01-24
I have only used this AGP card:
nVidia FX5500 256 MB, 1 x DVI, 1 x VGA, 1 x component, works flawlessly with Feisty and Gutsy.

For $50 budget, you may want to look at the 6600 & 6800 series. Have not tried them myself, but read that they works very well with Linux too.

---

### Post by stchman on 2008-01-24
> **icceric said:**
> Hi.  I have an extra Apple 20" Cinema Display that I would like to hook up to my old dusty PC to use with Ubuntu.  I currently have a PNY NVIDIA GeForce 5200 FX, 128mb, but only VGA outs.  So I need something new with DVI outputs to run my ACD (with ADC to DVI connector) that won't cause me a lot of fuss with Ubuntu.  I'm hoping to find something on eBay for $50 ish.  What card should I go for that will require little work if any to use full throttle?

BTW, it has to be AGP

Thank You for your expert advise!

Regards,
Eric

Yes, go nvidia.  The 6800GT AGP would be a good choice.

---

### Post by Mitchlb on 2008-01-24
Most video cards are compatible on Ubuntu. It's probably harder to find one that isn't then one that is. Nvidia and Intel are always safe choices. Still, most problems with Ubuntu compatibility occur with hard drives and network cards. Most nVidia-cards work. Just install the nvidia-glx or "nvidia-glx-legacy"  package, and run this command: "sudo nvidia-glx-config enable". Kyro, Intel, Ati, Matrox and Nvidia are known to work with Nvidia.

My advice: Find a card on Ebay. Then look to see if it's compatible before you bid. It most likely is. No worries.

Good luck!

---

### Post by hyper_ch on 2008-01-24
harddisk actually don't give problems... at least I have not seen one yet... samge goes for network cards... wifi cards are different...

---

### Post by icceric on 2008-01-25
Thank You all!  I will probably stick with nVidia... been looking around eBay, but haven't won anything yet.

Thanks again!

Eric

---

### Post by hyper_ch on 2008-01-25
good luck.

---

### Post by icceric on 2008-01-27
Thanks, appreciate it.  I actually foumd an old GeForce MX4 laying around that is working great until I get paid.  Even seems to have gotten smoother effects out of it than my 5200..  ??

---

