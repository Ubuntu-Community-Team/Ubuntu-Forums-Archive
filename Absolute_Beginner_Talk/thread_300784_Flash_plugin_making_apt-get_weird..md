---
title: "Flash plugin making apt-get weird."
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by bunnythebunny on 2006-11-16
Hey guys, I've just installed flash in ubuntu edgy and it was all fine. until today, i saw this in my package manager.

"E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it." 
E: Internal error opening cache (1). Please report.

I've tested it and it works, but i just want to get rid of this warning message.

i've tried to remove it through


 sudo dpkg -r flashplugin-nonfree

but then i get this 

 dpkg: error processing flashplugin-nonfree (--remove):
  Package is in a very bad inconsistent state - you should
  reinstall it before attempting a removal.
 Errors were encountered while processing:
  flashplugin-nonfree

i've tried to remove it through apt-get, and it just tells me the same:
 "E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it." 

I can't find the instructions i used to install it...  ](*,) 


So, any way i can get rid of this? and reinstall it?  

I'm using Ubuntu Edgy i386 on a AMD64 3200+ Athlon.

---

### Post by bunnythebunny on 2006-11-16
Bah, ok i think i solved it by 

sudo dpkg -i flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb 

im still curious to know what caused it though.

---

### Post by ghostrunner on 2006-11-16
Thanks for this information.  I've been having the same problem.  My question is this:  will the solution you just posted completely remove Flash?  And does that mean I'll have to reinstall it?  Or will it just solve the error message problem?

Thanks!

---

