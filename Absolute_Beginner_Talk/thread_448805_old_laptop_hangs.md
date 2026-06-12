---
title: "old laptop hangs"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by multicooker on 2007-05-19
Hi,

I've been trying to reuse an old [Toshiba]("http://reviews.cnet.com/laptops/toshiba-satellite-2060cds-k6/4507-3121_7-30000521.html?tag=nav") laptop, just for surfing the web, emails, etc. I'm using ubuntu's last version on cd, but its going nowhere. first I got an error regarding the bios ( [0.000000] ACPI: BIOS age (1999) fails cutoff(2000). acpi: force is required to enable PCI.)

- I already updated it, though the last update isn't that recent ( 2000). I tryed to install ubuntu again, but it just hangs in the end. 

For what I've seen online, maybe ( probably this isn't a longshot :) ) my specs demand a smaller linux distribuition. I've already tried DSL and Slax live cds, but they all hang in the end. Any help on this is welcome.

My specs:

 Toshiba Satellite 2060CDS - K6-2 366 MHz - 12.1" DSTN

   4 Gb drive

  * Data bus speed
   * 66 MHz

Cache Memory

    * Cache size
    * 256 KB

Storage Controller

    * Storage controller type
    * IDE


    * CD  speed
    * 24x

    * 24-bit (16.7 million colors)


    * Audio output compliant standards
    * Sound Blaster 16/Pro

---

### Post by overdrank on 2007-05-19
> **multicooker said:**
> Hi,

I've been trying to reuse an old [Toshiba]("http://reviews.cnet.com/laptops/toshiba-satellite-2060cds-k6/4507-3121_7-30000521.html?tag=nav") laptop, just for surfing the web, emails, etc. I'm using ubuntu's last version on cd, but its going nowhere. first I got an error regarding the bios ( [0.000000] ACPI: BIOS age (1999) fails cutoff(2000). acpi: force is required to enable PCI.)

- I already updated it, though the last update isn't that recent ( 2000). I tryed to install ubuntu again, but it just hangs in the end. 

For what I've seen online, maybe ( probably this isn't a longshot :) ) my specs demand a smaller linux distribuition. I've already tried DSL and Slax live cds, but they all hang in the end. Any help on this is welcome.

My specs:

 Toshiba Satellite 2060CDS - K6-2 366 MHz - 12.1" DSTN

   4 Gb drive

  * Data bus speed
   * 66 MHz

Cache Memory

    * Cache size
    * 256 KB

Storage Controller

    * Storage controller type
    * IDE


    * CD  speed
    * 24x

    * 24-bit (16.7 million colors)


    * Audio output compliant standards
    * Sound Blaster 16/Pro

Hi the biggest thing I see is not, the amount of ram. That would be my guess on that system. the required is 256mb:(

---

### Post by ugm6hr on 2007-05-19
Agree - RAM is most important.  Generally, if DSL won't run, you're in trouble.  However, it may be a hardware compatibility issue that's preventing DSL from working, which is common with laptops.  

If you've got at least 64MB RAM  - I'd recommend Litepup (which is a cut-down version of PuppLinux).  I think LitePup has a 2.14 version, but it's probably too early for the latest 2.16 to have been edited down yet.  It comes with almost no apps at all - but it's easy to get the necessary bits - recommend Opera web browser, Gxine media player, Abiword word processor...  Easy to install wireless if you've got an appropriate card too.  Check their forums - they're very friendly too.

If you've got 128MB RAM, then the full version of PuppyLinux should be fine.  In fact, the only reason I moved from Puppy to Xubuntu is that I got a new laptop, and Puppy2.14 didn't support widescreen laptops out of the box.  Might have another look with 2.16....

---

### Post by multicooker on 2007-05-20
thanks for the info,

I didn't quit yesterday, and kept looking for a solution..

I have now puppylinux running ( slowly, but way faster than w98 ),  and yes, of course the problem was with ram... I only have 32Mb. ( and I wanted ubuntu running on this, what a n00b )

I guess I'll try litepup, even so. I really just need a browser ( firefox would be great), maybe litepuppy can do the trick. 

I'm not managing to install my usb wirelless lan, I keep finding this strings of code that are suposed to be upgrades. how do I install them? get the packages in cd? copy them to disk? where do I insert the code, console?

thank you.

---

