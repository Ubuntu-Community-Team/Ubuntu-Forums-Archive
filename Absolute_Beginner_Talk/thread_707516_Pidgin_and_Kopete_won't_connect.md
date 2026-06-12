---
title: "Pidgin and Kopete won't connect"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by jano_rajmond on 2008-02-25
The problem is the following:

I tried Pidgin and Kopete and none of them run as the should under Ubuntu 7.10 (Gutsy Gibbon).

They both sign me in (I appear online to my friends) but my buddy list remains empty and at the bottom of the screen I get "Connecting..." message.

Whatever anyone writes to me I do not get.

I tried changing my listening ports to a few other values (as suggested in some threads) but nothing worked. Any ideeas anyone? :confused: :( :confused:

---

### Post by jano_rajmond on 2008-02-25
FYI> Internet connection (Mozilla and apt-get) work fine.

---

### Post by Peter09 on 2008-03-03
I am getting this problem to. If I go to accounts and disable my account and then enable it - Pidgin works. Pidgin used to work ok, do not know whats changed.

---

### Post by Hylian7 on 2008-03-03
I am also having this problem. The disable and then re-enable idea did not work for me. I imagine this is some kind of bug as it worked fine in Feisty for me, but did not in Gutsy.

---

### Post by Glaxed on 2008-03-03
You guys should either try an older version of Pidgin, or try compiling it from source.
The problem is not with Ubuntu here.
(mine works fine...)

---

### Post by Oldsoldier2003 on 2008-03-03
> **Glaxed said:**
> You guys should either try an older version of Pidgin, or try compiling it from source.
The problem is not with Ubuntu here.
(mine works fine...)
running 2.4.0 here and its acting no better or worse than before, you dont have to compile the newest version, you can get it at [http://www.getdeb.net/](http://www.getdeb.net/)  i usually just compile it myself though...

---

### Post by seventhc on 2008-03-03
same here, using 2.4.0 from getdeb, never had any problems with any version including this one. Also use kopete and no problems.

Try running them from the terminal and see if it gives any errors open a terminal and type pidgin then enter. whats the output?

---

### Post by pythonusr on 2008-03-08
Same problem, no error messages, just won't connect. It worked THIS morning, too.

---

### Post by lswest on 2008-03-08
double-check the proxy settings, maybe something is mis-configured there.  (often found under preferences and the connection tab)

---

### Post by pythonusr on 2008-03-08
I just had to run:

chmod -x /usr/sbin/NetworkManager

Apparently, networkmanager is buggy.

---

### Post by jano_rajmond on 2008-03-09
I will try these solutions maybe later, when I reinstall Gutsy Gibbon.

For now I was so disappointed that I could not make things work that I abandoned Linux for about a week and then reinstalled Feisty where things work perfectly.

Thanks for all your help guys and galls ;)

---

### Post by yorick on 2008-03-19
Hi. 

This happened to me too today. Yesterday it worked fine.

I have a direct connection to the internet, no proxy.

The solutions posted before did not work...

Anyone has another suggestion?

Thanks

---

### Post by Glaxed on 2008-03-20
So you tried the chmod?
Someone mentioned Feisty did the trick, why not upgrade to hardy kernel?

---

### Post by jano_rajmond on 2008-03-20
On Feisty both  WOK FINE, Hardy IS the problem...

---

