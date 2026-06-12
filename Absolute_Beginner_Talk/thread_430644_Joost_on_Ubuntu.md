---
title: "Joost on Ubuntu???"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by wiebers10 on 2007-05-02
I was wondering if anyone has got Joost working with Ubuntu either in Wine or in some other way?  If anyone has can they please let me know how.  I have Joost on my Vista Partition and it rocks however I'd like it on my Ubuntu partition because it is what i use now unless I want to use Joost basically.  Also I was also thinking maybe using VMware or something to set up a virtual windows and then installing it in there.  If that would also be possible please let me know.  Thank you.

---

### Post by starcraft.man on 2007-05-02
Far as I know all attempts by people to Joost under Wine failed. I think theres a development project by their joost team for a linux version though I don't know how long its gonna take. 

As for the virtual question, I don't see any reason why you couldn't set up XP or Vista in a virtual machine. Do remember Vista isn't so good in VM, Aero will not run and other features that rely on Aero for interface will be disabled. It might just be best for you to keep dual booting but the choice is yours.

Check my sig for Ubuntu Guide and your version, will have more details on installing and setting up VMware.

---

### Post by wiebers10 on 2007-05-02
Thank you very much.  I will try the vm with XP and see if that works after I'm done with my finals.

---

### Post by wiebers10 on 2007-05-02
I just read on the Joost forums that they are planning on a Linux release however they haven't released on yet and it does not work in any virtualazation software.

---

### Post by nosami on 2007-05-08
I haven't tried this yet (installed Joost on Windows and wasn't impressed) but I spotted this on the Gentoo forums today.

[http://forums.gentoo.org/viewtopic-t-558046.html](http://forums.gentoo.org/viewtopic-t-558046.html)

---

### Post by BoneyOne on 2007-05-09
Right now the only way to get it to work in any flavor of Linux is with the wine cvs or maybe the "special wine" listed in the above gentoo thread.

VM will not work for it as currently no VM will run with the 3d which apparently is needed.

---

### Post by jkeyes0 on 2007-05-09
I managed to get video working using the wine-cvs version talked about on the winehq appdb ([http://appdb.winehq.org/appview.php?iVersionId=7770)](http://appdb.winehq.org/appview.php?iVersionId=7770)). I went to Phil's repo ([http://paldo.org/~amnon/repo/sources/wine-cvs/](http://paldo.org/~amnon/repo/sources/wine-cvs/)) and built wine from the sources there with the patch included. It's not pretty, and sound doesn't work.... so not a solution, but a stepping stone.

I'll try the gentoo method mentioned when I get home and post results.

---

### Post by jkeyes0 on 2007-05-09
Update: I tried the Gentoo install mentioned earlier, and I managed to get Joost running, but I didn't get as far as I had gotten with the Wine CVS version, but it's a start.

---

### Post by Mets on 2007-05-09
Appearently you can get it to work under wine.  Here is a tutorial for Ubuntu

[http://ubuntuforums.org/showthread.php?t=438543&highlight=joost](http://ubuntuforums.org/showthread.php?t=438543&highlight=joost)

Haven't tried yet, but I'll give it a go next week when I finish final exams :/

---

### Post by mattyh on 2007-05-09
How do you get an into Joost? I heard it had "launched", but is it still invite only?

---

### Post by jkeyes0 on 2007-05-10
> **mattyh said:**
> How do you get an into Joost? I heard it had "launched", but is it still invite only?

self invite here: [https://joost.com/presents/gigaom-newteevee/](https://joost.com/presents/gigaom-newteevee/)

---

### Post by nidelius on 2007-12-06
For running joost in vmware have a look at : [http://ubuntuforums.org/showthread.php?t=623223](http://ubuntuforums.org/showthread.php?t=623223)

---

