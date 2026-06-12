---
title: "Stuck with my new wireless stick"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by camz on 2007-09-07
Ok so I managed to get my old Belkin F5D7050 working a few months ago on Edgy, [this]("http://opensource.bureau-cornavin.com/belkin/index.html") thread showed me everything I need (thanks to whoever gave me that link), and I can put an F5D7050 in now and do the following:
> 
iwconfig rausb0 essid networkname

iwconfig rausb0 enc ####-####-## open

dhclient rausb0

And it connects to my Internet. I've used 3 different adapters of the same kind and it always recognised.

Yesterday I bought a new wireless adapter, the upgraded (G+) version, a Belkin F5D7051, which visually looks identical. When I put it in and do the usuals, it does not recognise it. So I'm wondering how I can basically do what I did last time over again to get this thing working on Edgy :)

Note: I'd rather not use ndiswrapper, I found it very problematic later on in use :)

---

### Post by dca on 2007-09-07
I'm thinking it uses an updated & different chipset requiring you to use 'ndiswrapper' and the new Windows driver.  Unfortunately this really doesn't help:
 
[http://www.belkin.com/support/product/?lid=en&pid=F5D7051&scid=221](http://www.belkin.com/support/product/?lid=en&pid=F5D7051&scid=221)

---

### Post by dca on 2007-09-07
Nevermind, it's a Broadcom 4320 chipset...
 
[http://www.linuxquestions.org/hcl/showproduct.php/product/3721/sl/f](http://www.linuxquestions.org/hcl/showproduct.php/product/3721/sl/f)
 
Also, try putting in the chipset or Belkin model# in Ubuntu forums search, you should get a few hits...

---

### Post by camz on 2007-09-07
Well I said I'd _prefer_ not to use ndiswrapper, but if it is the ONLY way to get it to work, then a little guide would be useful :) I'm 13 years old and am pretty much trying to get everything done on Linux rather than use Windows. Good training for the future :P

---

### Post by camz on 2007-09-07
Just checking that out now. That review didn't look very promising :S

---

