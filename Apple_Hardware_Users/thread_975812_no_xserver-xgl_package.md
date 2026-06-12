---
title: "no xserver-xgl package"
date: 2008-11-08
forum: Apple Hardware Users
---

### Post by crapple on 2008-11-08
There is no xserver-xgl package in interpid for desktop effects..

What can you use instead.

---

### Post by bryonak on 2008-11-08
Big changes have been made with Xorg in the past months... among them a lot of automated integration of components which have been separate before.

If you want high performance, Nvidia cards are supported by the new nvidia-XXX drivers, ATI cards use the fglrx packages.
Other hardware uses various xserver-xorg-video-* drivers.

---

### Post by crapple on 2008-11-08
I have the ati radeon 7500.  I have to use the fbdev driver the ati one dose not work.  When Try to enable desktop effects it says desktop effects could not be enabled.

---

### Post by bryonak on 2008-11-09
You should always mention your card model.
Yours is too old for the fglrx driver to work with compiz...
[Here's some info]("http://ubuntuforums.org/showthread.php?t=764633&highlight=compiz+fglrx+ati") for enabling compiz with older ATI cards.

---

### Post by crapple on 2008-11-09
I have the radeon 7500.  When I try that post it gives me a white screen when I do system preferences-appearance and click on visual affects and do normal.  After the white screen it goes back to none so there are no desktop effects any other ideas.

---

### Post by bryonak on 2008-11-09
There's some fix mentioned on the first site of the thread I linked (something about skipping checks)... you also might want to skim through the whole thread. Granted, not an awesome idea, but I can't really help you there because I've stopped using ATI cards when they started affiliating with Microsoft and giving only second grade drivers to Linux (= fglrx)... was a big ATI fan before.

Maybe you want to search the laptop&hardware or desktop effects&customization forums, because this question is more about ATI cards and compiz than about apple... and open a thread in one of these (mentioning this thread here).

---

