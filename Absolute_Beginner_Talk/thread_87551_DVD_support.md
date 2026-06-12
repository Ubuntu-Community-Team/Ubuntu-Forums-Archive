---
title: "DVD support"
date: 2005-11-08
forum: Absolute Beginner Talk
---

### Post by buncas on 2005-11-08
I just installed Ubuntu on my pc at home just to take alook at it to see what linux is like..Is there any immediat support to play dvd on ubuntu.  Totem movie player does not recognize the dvd...Do not remember the exact error, just know that it does not work.

:confused:

---

### Post by Who on 2005-11-08
Firsty, it is sensible to search the forums and google before asking your question - this one has been answered a number of times before!

For the quick answer look here

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Some of the files required to decrypt DVDs are not able to be included in Ubuntu (or any Linux distro that is downloadable for free) becuase they are illegal in some countries (Because the encrypion had to be broken/reverse engineered). Sooo, you need to get those files from the Internet (providing they are legal in your country).

Ultimately, the file you need is called libdvdcss2 and can be got from Synaptic (System-->Administration...Synaptic Package Manager) after all the extra repositories have been added. 

[http://ubuntuguide.org/](http://ubuntuguide.org/) has information for 5.04 that is likely to apply to 5.10

Hope that helps
Who

---

### Post by buncas on 2005-11-08
WHO, thanks for the response.  Not too familar with the forums as yet,  will do a search next time.  

Thanks again for the quick response, Buncas.

:)

---

### Post by jasay on 2005-11-08
You might also need to enable dma on your dvd drive if the video plays choppy.

[http://help.ubuntu.com/starterguide/C/ch04.html#id2532307]("http://help.ubuntu.com/starterguide/C/ch04.html#id2532307")

---

### Post by jeffreyvergara.NET on 2005-11-08
i have to CD/DVD Rom drives

cdrom0 - (cdrw) & cdrom1 - (dvdrw)

do i also have to add something like this?
> 
#/dev/cdroms/cdrom1 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

i only have this, enabled DMA
> #/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

---

