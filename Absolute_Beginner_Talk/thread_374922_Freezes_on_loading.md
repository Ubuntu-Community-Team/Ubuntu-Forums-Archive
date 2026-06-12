---
title: "Freezes on loading"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by thunta on 2007-03-03
hii,

sorry for the lame title but i dont exactly know how to put it into words.

ok, i downloaded ubuntu 6.10 and burned it. I put it into cd drive and press "boot from cd". It goes to the menu. Then I click install or boot from cd (the first option). Then the orange bar starts moving from side to side for about 5 minutes. Then a black screen with the cursor for the rest of the time. What is my problem and how do i fix it???

btw: do i need to create a linux partition before booting from cd? if so, wat linux partition?

PC Specs: 
Dell Dimension 5100
P4 3.00Ghz
512mb DDR Ram
64mb onboard graphics
80gb hdd

pls help

thanks,

---

### Post by hackle577 on 2007-03-03
This happened to me once and it turned out it was just some sort of screensaver-type thing. If moving the mouse doesn't cause the screen to come up, you may have some sort of problem. A bad disk myabe. I'm by no means an expert, but I'm sure someone will be along very shortly to help you out.

No, you do not need to create a Linux partition to boot to the CD. This is the beauty of LiveCDs, you don't need to do anything and they don't change your computer at all!

---

### Post by thunta on 2007-03-03
thanks

but no, there is nothing wrong with the cd because it worked perfectly with my friends computer.

---

### Post by Kobalt on 2007-03-03
Do you get a LiveCD session or is the crash happeing before you can access the session ? As I understand it, you don't access the LiveCD session... 
One thing you could try : it seems your config. is the one of a laptop. Many laptops need a couple of tricks to start a LiveCD of Ubuntu (mine does actually). 
When you boot your computer with the CD inside your drive, you get the menu "Boot from CD, etc." : press F6 to get boot options and simply add at the end of the line *noapic nolapic* then press Enter. 
If this still does not work, then my guess would be a problem around your graphic card... but we'll see after the trick.

---

### Post by thunta on 2007-03-03
no luck =[ i typed them but still the black screen with the cursor stayed there =[.
just wondering, do u need a space before u write *noapic nolapic*??

I thought it mite be my graphics card (nvidia geforce 6800), thats why i took it out and tryed with the onboard one, but still no luck =[

pls help me, im keep to learn linux :)

thx

---

### Post by Kobalt on 2007-03-03
nVidia graphic card are generally linux-friendly hardware, it shouldn't be this... 
Yes, there must be a space before *noapic nolapic*...

---

### Post by thunta on 2007-03-03
OMG, never knew what a little space would mean :P.

It works!!! I've been running the live cd bcus still, so lets see how to the installation process will go ;)

Any advice about any problems you guys know about installing ubuntu??? I also have windows xp, and xp media center installed.

Thanks ppls and THANK YOU very much Kobalt,

---

