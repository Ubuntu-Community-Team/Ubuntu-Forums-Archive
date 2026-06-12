---
title: "Amarok update"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Daisymorrigan on 2007-03-29
I am trying to update my son's Amarok, but since automatix has been down, everything else I have tried isn't working so far.

He has ubuntu 6.06 on his computer. I went to the Amarok site and tried entering the command into terminal to get an update, and the terminal says I already have the latest version. His computer has version 1.3.9, and I want to update it to 1.4.5. Any suggestions?

Thanks!
Daisy:) :KS

---

### Post by Pelekophori on 2007-03-29
You will also need to edit /etc/apt/sources.list and add the repository given in the amarok instructions, namely: > deb [http://kubuntu.org/packages/amarok-145](http://kubuntu.org/packages/amarok-145) edgy mainSee also [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/Repositories/Kubuntu")

That said, I don't know if the amarok from that repository, which is intended for Edgy Eft, will work on Dapper.  So use at your own risk.  

The alternative is to try the latest source from  [[COLOR="Red"]here[/COLOR]]("http://amarok.kde.org/wiki/Download:Source")


Edit: ignore the fact that part of the quoted text above appears to be a link.  The forum software insists on turning it into a link despite my efforts to persuade it otherwise.  It's meant to be a single line of text.

---

### Post by groggyboy on 2007-03-29
the amarok website's kubuntu download page: [http://amarok.kde.org/wiki/Download:Kubuntu](http://amarok.kde.org/wiki/Download:Kubuntu)

according to the site, the latest dapper repository contains amarok 1.4.3.  i would recommend settling for that version, as using an edgy repo (as Pelekophori mentioned) in dapper is NOT a great idea.  otherwise, if you must have the latest and greatest, compiling from source would be the way to go.

---

### Post by Daisymorrigan on 2007-03-29
Ok, so I don't understand what compiling from source means. This is all very confusing to me, but I am willing to learn. Can you explain the steps I need to take to update the amarok player to the best version for my os?

---

