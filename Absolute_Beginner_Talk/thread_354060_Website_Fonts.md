---
title: "Website Fonts"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Kemik88 on 2007-02-05
Hello all,

The fonts on the websites I view on Ubuntu (via Firefox) look different to Windows versions (again in Firefox).

Here are some examples comparing:

EBuyer - Ubuntu
[[IMG]http://img389.imageshack.us/img389/3412/ebuyerubti6.th.png[/IMG]](http://img389.imageshack.us/my.php?image=ebuyerubti6.png)

EBuyer - Windows
[[IMG]http://img516.imageshack.us/img516/9527/ebuyerwinzq4.th.gif[/IMG]](http://img516.imageshack.us/my.php?image=ebuyerwinzq4.gif)

Eos Hosting - Ubuntu
[[IMG]http://img517.imageshack.us/img517/3534/eoshostingubpu8.th.png[/IMG]](http://img517.imageshack.us/my.php?image=eoshostingubpu8.png)

Eos Hosting - Windows
[[IMG]http://img506.imageshack.us/img506/4701/eoshostingwinje5.th.gif[/IMG]](http://img506.imageshack.us/my.php?image=eoshostingwinje5.gif)

WHMCS - Ubuntu
[[IMG]http://img517.imageshack.us/img517/4553/whmcsubdn4.th.png[/IMG]](http://img517.imageshack.us/my.php?image=whmcsubdn4.png)

WHMCS - Windows
[[IMG]http://img506.imageshack.us/img506/4193/whmcswinwz6.th.gif[/IMG]](http://img506.imageshack.us/my.php?image=whmcswinwz6.gif)

Does anyone know how I can match the way the websites look in Ubuntu to the way they look in Windows?

Thanks a lot.

---

### Post by RomeReactor on 2007-02-05
Hi. Look in Synaptic (System-->Administration-->Synaptic Package Manager) and search for **msttcorefonts**. I think those are the ones you need, though the font types in windows don't look as good as the ones in Ubuntu, IMO...

---

### Post by Kemik88 on 2007-02-05
Hello,

When I searched for that both the msttcorefonts and Open office shown up. I reinstalled the msttcorefonts just incase the Open Office fonts overwritten them.

I'll restart my computer and get back to you.

EDIT: No difference I'm afraid :(

---

### Post by RomeReactor on 2007-02-05
That's odd; when i was using Opera a couple of weeks ago, msttcorefonts **did** change the fonts on web pages. Sorry i can't be of more help...

---

### Post by kerry_s on 2007-02-05
So you want to make the ubuntu fonts look fugly like the windows fonts?
Just turn off the antialias and maybe hinting.

left side is the windows, right side is the ubuntu

---

### Post by Kemik88 on 2007-02-05
I'll try it out. Thanks :)

P.s. Windows fonts aren't that bad ;) I just like what I'm used to regards readability.

---

### Post by Contrid on 2007-02-05
I have to agree that Windows fonts are fugly. :)

---

### Post by neji on 2007-02-11
That's only because in the screenshots Cleartype hasn't been enabled for Windows. With Cleartype the Windows fonts are much more readable IMO

---

### Post by mjpatey on 2007-02-11
Kemik88-

Once you've installed msttcorefonts, you have to then go into Firefox's Preferences, and set the font defaults to your preferred MS fonts.

What msttcorefonts doesn't give you is Tahoma, which is used for small text in Windows UIs, etc.  Tahoma can be downloaded separately if you want it.

-Mark

---

