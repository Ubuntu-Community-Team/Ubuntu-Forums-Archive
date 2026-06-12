---
title: "HP Photosmart 8750 Black and White printing"
date: 2007-11-09
forum: Art &amp; Design
---

### Post by TimGS on 2007-11-09
I have HPLIP and the HP8750.

Is there a way of forcing printing to be from the Grey Photo cartridge only?

If not, my photo-processing is likely to stay in Windoze :mad:

-- Tim.

---

### Post by jcornuz on 2007-11-10
Hi there,

I have an HP7660 which I use for color and b/w photography printing. The result is excellent with HPLIP. To switch from color to b/w, I simply change the cartridge  :-P (that is the sandard on the 7660).

Did you install hplip-toolbox? that gives you access to more configuration of your printer. I think there should be a "high-quality photographic borderless black and white A4" option or something like that - sorry I don't have the software before my eyes right now.

Take care,

Joel

---

### Post by TimGS on 2007-11-10
Hi Joel,

Thanks for the reply.

The 8750 has three cartridges, each with three inks - one of them being black plus 2 greys (the 'photo grey' cartridge as HP calls it). The 8450 was the same (they only differ in maxiimum paper size). They are printers very definitely geared towards B&W photography (although the six colour inks give very good results also).

The Windoze XP driver has an option to print in greyscale which forces ink to only come from this cartridge - ensuring that you will get a neutral print, and just as important, it will stay neutral. HPLIP toolbox has some greyscale options, but the description is '600[or whatever] dpi, greyscale, black + color cartridge' implying its the usual fake greyscale option that is just made up of equal(ish) intensities of cyan, magenta and yellow. Also, the 'Photo' options (1200dpi) don't have this option at all.

On the subject of dpi, the Windows Driver seems to output photo quality prints at 600dpi (its 'best' option, although there is a maximum of 4800dpi, which is implied in the manual to be unneccesssary and in practice this appears to be the case). However, the 600dpi options on HPLIP are definitely not photo quality. HPLIP's 1200dpi is very good but seems to take a while even by the 8750's standards (its a very good printer, as long as you are not in a rush).

Maybe I need to see if HP Image Zone will run under Wine.

-- Tim.

---

### Post by jcornuz on 2007-11-11
Hi Tim,

I guess your printer must be one (or two) generations better than mine. Is that an A3? Well, even if my way to switch from color to b&w is a bit more... primitive, I don't mind for now :)

Don't bother trying wine: it will not work with an external (usb) device...

Agreed, 1200 dpi is what we are looking for here. Did you try converting an image to black and white and sending it (well a small format) to 1200dpi photo full bleed + color cartridge? Even without the mention of "greyscale" maybe it does the right thing?

Otherwise, try checking out the[ hplip mailing lists]("http://hplip.sourceforge.net/mailing_lists.html").

Hope you get a good solution. It took me a while to figure out color management and margins, but now printing on an HP in Linux is a joy - so there must be hope for you :)

Take care,

Joel

---

### Post by TimGS on 2007-11-12
A solution may well be on its way...

[https://answers.launchpad.net/hplip/+question/17586](https://answers.launchpad.net/hplip/+question/17586)

Thanks for the HPLIP mailing list suggestion - that led me indirectly to Launchpad (am still new to linux - it probably shows...)

-- Tim.

PS. Yes its A3. It had a little brother the HP8450. Sadly thats discontinued now. If I didn't have ambitions to sell prints the HP8450 would have been the better choice (there's only so many A3 pictures you find room for at home, and the HP8450 was less than half the price!). Also, its even bigger than its A3 capability would suggest - not an ideal size in a 2-up, 2-down Yorkshire weaver's cottage. Good pics though.

---

### Post by 11hjpphty76lkjj on 2007-11-13
Hey guys,

Just wanted to let you know that we're working on a solution and it should be in the next release of hplip.

A

---

