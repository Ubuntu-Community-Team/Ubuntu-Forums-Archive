---
title: "GNUCash and Grisbi are ugly"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by Zoolook on 2006-09-01
Ekk...

I am not using either of those.  I think I am going to miss MS Money.  Anyone using MS Money under WINE?

Any alternatives?  Seems strange there isn't a decent personal finance package for Ubuntu or GNU/Linux.

---

### Post by szf on 2006-09-01
GNUCash is 2.0+ now - although it hasn't hit the Ubuntu backports AFAICT. I tried Grisbi briefly, but the euro-ness turned me off ( e.g. dates in format ddmmyyyy) and I failed to find option to configure.

After some initial time spent in GNUCash - it can track home finance very well.

---

### Post by msak007 on 2006-09-01
> **Zoolook said:**
> Ekk...

I am not using either of those.  I think I am going to miss MS Money.  Anyone using MS Money under WINE?

Any alternatives?  Seems strange there isn't a decent personal finance package for Ubuntu or GNU/Linux.

Last time I tried Money 2005, it froze when loading - install was fine (albeit buttons were missing text and I was clicking "Next" blindly) but the app wouldn't load. [WineHQ's rating]("http://appdb.winehq.org/appview.php?iAppId=79") for that version was "Garbage" (go figure), and the best rating it ever got is "Silver" (2003 & 2004), but for the most part overall it's not going to work well. Seems from that page nobody has tried using Money 2006 so if you have that version give it a shot. Money is one of the only reasons I can't switch my dad to Ubuntu. I use KMyMoney and for me it suits its purposes (plus it's a KDE app so it looks nice), but for his business unfortunately he relies on MS Money.

---

### Post by bodhi.zazen on 2006-09-01
I have not tried Money in wine, but by report it does not run well.

Check with wineHQ: [http://appdb.winehq.org/appview.php?iAppId=79](http://appdb.winehq.org/appview.php?iAppId=79)

I have been looking at kmymoney.

[http://kmymoney2.sourceforge.net/index2.html](http://kmymoney2.sourceforge.net/index2.html)

---

### Post by Zoolook on 2006-09-01
I am using Gnome, not KDE.  Any chance of KMyMoney working under Gnome?

---

### Post by bodhi.zazen on 2006-09-01
> **Zoolook said:**
> I am using Gnome, not KDE.  Any chance of KMyMoney working under Gnome?

Yes. you can run kmymoney in gnome, xfce, fluxbox, etc no problem.

When you install kmymoney from apt-get or synaptic it will install a bunch of depencencies.

---

### Post by msak007 on 2006-09-01
> **Zoolook said:**
> I am using Gnome, not KDE.  Any chance of KMyMoney working under Gnome?

You said you tried GnuCash, did you try the new version 2.0? KMyMoney will install fine as it's in the repos, so installing it will install all its dependencies (although it won't be the newest version). GnuCash is supposed to be more Gnome-ish, so in terms of looks KMyMoney will stand out a little on your system. I was just stating what my personal preference is. One thing I should also mention is that if you're in the US and your bank supports online banking (DirectConnect OFX), the KMyMoney in the repos was not compiled with this option enabled so I had to compile from source to get this feature which was the most important for me. When I first switched, I tried MoneyDance for a while because I could use it in Windows and Linux. It's kind of like Money (including online banking support), but it's a commercial app and was built using Java so it was very slow and ugly so I wouldn't recommend it. I don't use it anymore for those reasons and because I don't use Windows anymore. There are a lot of little personal finance projects / apps for Linux, but when it comes down to it I think your major choices are GnuCash, KMyMoney, or MoneyDance. There's also one called Kapital which is also a KDE app, but it's a commercial app.

---

### Post by Zoolook on 2006-09-01
I'll try and get GNuCash 2.0 working

As for converting my money file, I guess I have to convert each account to a QIF one at a time?

---

### Post by bodhi.zazen on 2006-09-01
> **Zoolook said:**
> I'll try and get GNuCash 2.0 working

As for converting my money file, I guess I have to convert each account to a QIF one at a time?

gnucash works as well. I had a lot of trouble trying to convert my money data to gnucash or kmymoney, If you find an easy way let me know please. I figured it would be easier to configure wine or just start (gnuchsh/kmymoney) from scratch (imports do not go so smooth).

---

### Post by msak007 on 2006-09-01
That would be the best thing to do. Install both apps and get a feel for them and their usability, see which one has the features you're looking for and which one looks better to you. Recommendations go a long way, but nothing is as good as getting first-hand experience. As far as importing files, yea that's the only way I know of - exporting accounts individually to QIF in Money, then importing them one at a time.

---

