---
title: "upgrading firefox to 2.0"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by mg620 on 2007-01-14
I'd like to upgrade to Firefox 2.0 from 1.503.  Synaptic shows v 1.506 as the upgrade, but I just downloaded v 2.0 (tarball).  It's in my home folder now, and when I extract it, it creates a firefox folder in my home folder and doesn't overwrite the existing firefox version.

Should I remove v 1.5 with synaptic first?  Either way, where do I put the tarball before extracting?

And out of curiosity, why would synaptic show an outdated upgrade and not the new one, even after reloading?

Thanks for the help.  I love this place.

---

### Post by Sef on 2007-01-14
> And out of curiosity, why would synaptic show an outdated upgrade and not the new one, even after reloading?

Dapper Drake, 6.06 is LTS (Long Term Stable); hence, it will have packages that will not break systems.  Therefore, it's packages will be older, but more stable and less likely to break a system.

---

### Post by NeoLithium on 2007-01-14
I'm just about to get 2 myself; so I'll let you know about the compiling; althouhg I wouldn't remove 1.5, it'll probably try to remove ubuntu-desktop because it's an integrated package; won't do any harm.  The reason it looks outdated, is that the repositories, use .deb files, which are precompiled and ready for people to just install; there just hasn't been a stable version put inside there yet.

---

### Post by mg620 on 2007-01-14
Okaaaaaayyy, now I get it.  Both of your answers make sense.  I'll just create a folder for version 2 and point the launcher to it.

Thanks for your help.

---

### Post by DJ_Peng on 2007-01-14
I moved from being a Mozilla tester on Windows to Ubuntu, and I ended up downloading Firefox 2 from Mozilla like you did. I did what you did, but with one difference. I used the -profilemanager flag at runtime to point my Fx 2 profile to my old user profile. If you've already started using Fx you can find the profile you were using and tell your new installation to use that profile without loosing any data or settings. Just remember to backup your old profile first on the off chance that something gets messed up in the process.

---

### Post by NeoLithium on 2007-01-14
I JUST installed Firefox 2.0.0.1; just untar'd it in /usr/lib; it overwrote everything but my personal settings; so now that's the only firefox on my ubuntu.

---

### Post by Frank Golden on 2007-01-14
> **mg620 said:**
> Okaaaaaayyy, now I get it.  Both of your answers make sense.  I'll just create a folder for version 2 and point the launcher to it.

Thanks for your help.Aysiu has an excelent script to automate this
see

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

See option four and download the script to your desktop. (on my browser the link shown in option 4 is brown and hard to see. It is the words [COLOR="sienna"]this script [/COLOR]as in 
4. Download [COLOR="Sienna"]this script[/COLOR] ...

Follow the directions on page and voila. FF2 with all your rxtensions and add-ons/plugins etc.

The script is interactive ie: you have to specify locale info etc.

The update feature within FF will still be greyed out but if you open FF in the terminal
```
gksudo firefox
```
The manual update feature will be available. This opens FF root.
Use this code only to manually update.
All addons etc will update automatically if you choose that option.

---

