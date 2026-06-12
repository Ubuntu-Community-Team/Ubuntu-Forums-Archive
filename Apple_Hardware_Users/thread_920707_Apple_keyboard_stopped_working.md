---
title: "Apple keyboard stopped working"
date: 2008-09-15
forum: Apple Hardware Users
---

### Post by alwiap on 2008-09-15
Hello,

I bought an Apple keyboard (wired), and it stopped working (I run Linux Mint on a PC).  It was working fine when I just plugged it in, and I went to change the keyboard layout to "Apple", and now only a few keys work and it's mostly numbers.  I assume something happened with the xorg.conf, so I went into it but saw nothing out of the ordinary.  What could have happened?  When I plugged my old keyboard into the computer it worked fine, and the Apple keyboard was working when I initially started using it.  

The Apple keyboard works fine from Windows (from where I'm posting now), and oddly enough, when I restart the X server, to login, the Apple keyboard works fine as well.  But after I login, the keyboard stops working correctly.  

Thanks for your help!

---

### Post by darkmatter21 on 2008-09-15
Do you have a backup of your old xorg.conf you could compare to your new one?
I found an xorg.conf file I used on my G3 iBook, but it came from a G4 iBook which evidently has a slightly different keyboard and it screwed up the key mappings a bit. So I just copied the old settings for the keyboard from my backup.

What happens if you change the keyboard layout back to the original value? I'd guess that the apple layout is for some ancient dinosaur keyboard, rather than a newer USB, but I honestly wouldn't know.

---

### Post by cyberdork33 on 2008-09-15
you turned on numlock... hit F6 a couple of times and it will turn it back off. This problem should be fixed in newer kernels. There are a few bug reports in launchpad.

---

