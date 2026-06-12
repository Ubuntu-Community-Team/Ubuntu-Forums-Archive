---
title: "Greasemonkey scripts won't install"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by supertheman on 2007-04-05
I installed Greasemonkey a few days ago, into Firefox/2.0.0.3 on a G3 Powerbook, Mac OS version 10.4.9. When I try to install a script, the install button does nothing. I can press "cancel", I can click on "Show Script Source", but no install. Firefox just auto-upgraded Greasemonkey to the latest version (0.6.8.20070314.0). WHAT is going on?! 

Is there a way that I can manually load scripts? Can I copy the source and pop it into BBedit and then put it in some folder? Any help is appreciated. Thanks.

---

### Post by kittyhawk63 on 2007-06-08
Bumped for help. I have the same problem. :confused:

---

### Post by garyedwardjohnston on 2008-01-24
I have this problem too!!

---

### Post by wsl3 on 2008-02-05
I am having a problem where, having removed firefox and greasemonkey, with --purge, I reinstall and cannot get scripts to install once I have reinstalled firefox and greasemonkey. Every script I try to install give me an install box, clicking the install button does nothing. It doesn't matter what script, or what the source of the script is. It just won't do anything at all when I click the install button. Anyone else see this?

---

### Post by y-lee on 2008-02-05
Ok all your greasemonkey scripts should be kept in your** /.mozilla/firefox/** folder in your *username *home. Something like the below: 

```
/home/username/.mozilla/firefox/57wj47mm.default/gm_scripts
```

Only the  ** 7wj47mm.default** part will most likely be different, just look for the .default part.

Two questions 

[LIST]
[*]Are you the owner of that  folder: **gm_scripts**

[*]Do you have read write and execute permissions on that folders contents
[/LIST]

To see open your file manager and go there and right click and choose properties,

If either you are not the owner or you do not have the right permissions the extensions will not install!

> **supertheman said:**
>  Can I copy the source and pop it into BBedit and then put it in some folder? Any help is appreciated. Thanks.

Probably, maybe ...  never tried. If you do try might be a good idea to make sure firefox is not running.

---

### Post by mscir on 2008-05-26
"/home/username/.mozilla/firefox/57wj47mm.default/gm_scripts"

Thanks for the tip, that was just what I was looking for.

---

### Post by somecallmechief on 2008-06-19
That fixed it for me as well.  I did a

sudo chown -R username:users /home/username/.mozilla/firefox/profilejunknumlet/gm_scripts

and all was well.  I also noticed that all of the scripts I attempted to install were created, but did not appear in Greasemonkey.  I deleted the contents of the gm_scripts folder, and reinstalled my scripts.  Everything now works.

---

