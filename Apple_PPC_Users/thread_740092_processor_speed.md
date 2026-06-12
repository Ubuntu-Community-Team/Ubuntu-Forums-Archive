---
title: "processor speed?"
date: 2008-03-30
forum: Apple PPC Users
---

### Post by LaSelvaBeach on 2008-03-30
Hey Everybody,

I'm currently running Xubuntu 7.04 on my slot-loading iMac G3 400 Mhz with 1024 Mb of RAM that I found in somebody's garbage on my way home.  I checked about and all the forums that I read seemed to indicate that Xubuntu 7.04 would be the best option.  Now that I've been using it for awhile, I'm noticing that most people are recommending 7.04 due to the RAM of the computer in question, which tends to be 64-328 Mb in most cases.  

My question is this: does processor speed matter much in the choosing of which version of Ubuntu?

Thanks!

---

### Post by peterbrewer on 2008-03-30
Not hugely though will make a difference.  Its the ram which affects performance the most.

---

### Post by prshah on 2008-03-30
> **LaSelvaBeach said:**
> 
My question is this: does processor speed matter much in the choosing of which version of Ubuntu?


RAM is the most important and you have plenty of that; but I personally run Xubuntu with FluxBox on systems with slower Cyrix/AMD/Intel Celeron processors (<450 Mhz). I find it snappier and the system load indicator doesn't keep jumping all the way up.

---

### Post by LaSelvaBeach on 2008-03-30
thanks!  and, err, what is FluxBox?

---

### Post by stream303 on 2008-03-30
> **LaSelvaBeach said:**
> I'm currently running Xubuntu 7.04 on my slot-loading iMac G3 400 Mhz with 1024 Mb of RAM that I found in somebody's garbage on my way home.

That's great!  One less lump of plastic and silicon saved from the landfill and turned into something useful.

> I checked about and all the forums that I read seemed to indicate that Xubuntu 7.04 would be the best option.  Now that I've been using it for awhile, I'm noticing that most people are recommending 7.04 due to the RAM of the computer in question, which tends to be 64-328 Mb in most cases.

Sounds like you lucked out.  I checked on your hardware at
[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

and it does appear that your Mac will accept 1gb max memory unofficially.  Sounds like the previous owner did you a favor and performed a firmware upgrade and ram upgrade.

To doublecheck, I'd run this in a terminal and see if that additional ram is truly getting addressed:
```

free -m
```

and look at the total amount of ram in the first column.
 
> My question is this: does processor speed matter much in the choosing of which version of Ubuntu?

Like the other posts, ram is more important the raw cpu speed.  Remember that for the G3's and I think the G4's, a rough comparison can be made to X86 boxes running at twice the speed, therefore your 400mhz ppc is in the neighborhood of an X86 box running at 800mhz.

You've got plenty of ram, so Xubuntu should fly, but then again regular Ubuntu and Kubuntu should do just as well with their Gnome and KDE desktop environments respectively, should you want more desktop features.

You could try these desktop environment out without reinstalling by downloading either ubuntu-desktop, or kubuntu-desktop and then picking which to run at the login screen, although you'll pick up all their associated desktop programs and utilities.

One thing to keep in mind is that even though you may pick a lighter-weight desktop like Xubuntu, your applications won't run any faster.  That is heavyweights like OpenOffice or Gimp will be faster to click on and run, but the program itself will take just as much time to run once it starts.

Sounds like you've got a great ppc box ready for many more years of usage!

---

### Post by ElTimo on 2008-03-30
One thing you might try (though I'm not sure how smart this is) would be to do```
sudo apt-get install preload
```It makes things a bit faster for me. again, though, i'm not even sure how frequently updated preload is. good luck! thats one hell of a find!

---

