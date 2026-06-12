---
title: "Need help installing firefox"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by fortmac on 2006-03-23
I just installed breezy 5.10 on my powerbook and was upset to find firefox 1.0.7 on my system.  In attempting to upgrade that to 1.5 I used this tutorial:

[http://ubuntuforums.org/showthread.php?t=137243&highlight=installing+firefox](http://ubuntuforums.org/showthread.php?t=137243&highlight=installing+firefox)

but all that led to was not being able to run firefox from the applications > internet folder or the quick launch icon.  currently to launch firefox i go to gaim's "get help online" and work from there.  

i'm painfully new to linux and any pointers you could give would be greatly appreciated.

---

### Post by _simon_ on 2006-03-23
The easiest way is to run automatix as this will install it for you.

If you haven't already got automatix then:

[http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix)

You can install a fair bit with it.

```

wget http://beerorkid.com/automatix/automatix_5.7-2_i386.deb
sudo dpkg -i automatix_5.7-2_i386.deb

```

---

### Post by kadymae on 2006-03-23
Hi, I'm taking a look at this page
[http://www.mozilla.com/firefox/all.html](http://www.mozilla.com/firefox/all.html)

And I don't see Firefox 1.5.1 for PPC listed at all

You *cannot* run the i686 linux package, not without grabbing the source code and doing a compile to PPC.

---
Actually, looking at the Firefox site, I don't see a single PPC Linux distro supported.  I think the only reason we have 1.0.7 at all on our systems is that Cannonical compiled it for us.

---

And, as an aside {soapbox} it's situations like this that make me support Opera.  They *always* have a PPC compile.  {/soapbox}

---

### Post by kadymae on 2006-03-23
Simon, I think the big problem here is he's got an Mac Powerbook, not a MacBookPro.

an i386.deb will not run on it at all.  Not without a recompile of source code.

---

### Post by John.Michael.Kane on 2006-03-23
Heres something that may help PPC user's [http://www.tygier.co.uk/linux/firefox.html](http://www.tygier.co.uk/linux/firefox.html)

New link posted. Thanks ssam.

---

### Post by _simon_ on 2006-03-23
[QUOTE=kadymae]Simon, I think the big problem here is he's got an Mac Powerbook, not a MacBookPro.

an i386.deb will not run on it at all.  Not without a recompile of source code.[/QUOTE]

ah sorry! :(

---

### Post by kadymae on 2006-03-23
> ah sorry!

Dood -- "pobody's nurfect"  ;)

---

### Post by ssam on 2006-03-23
[QUOTE=SD-Plissken]
New link posted. Thanks ssam.[/QUOTE]

thanks SD-Plissken

fortmac let me know if you have any problems with the packages on my site.

---

