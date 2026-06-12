---
title: "Funky wine"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by haveacigar on 2007-01-22
Hey, i have installed wine so that I could install editplus and everything went great, so i decided to install guitar pro and see what would happen... now the text is all funky. I have tried to re-install and uninstall reinstall but neither will work, it still has the funky text..

Please help!

Ciggy

---

### Post by Shatrat on 2007-01-22
Here is the wine appdb entry for guitar pro.
[http://appdb.winehq.org/appview.php?iAppId=246](http://appdb.winehq.org/appview.php?iAppId=246)
If you look under your version maybe someone else has had this problem and knows a workaround.  It might be as simple as installing a font or changing a few lines in the programs config or winecfg.

Good luck.

---

### Post by rocknrolf77 on 2007-01-22
I think maybe you need the ms fonts or something like that. Can't remember but I think you can get them and many others with automatix.

Maybe try these : ```
sudo aptitude install msttcorefonts
```

---

### Post by haveacigar on 2007-01-22
Thanks, but unfortunately that didnt work. Isnt there anyway to just remove everything and start fresh?

---

### Post by rocknrolf77 on 2007-01-22
If you are talking about configuring wine all over. You can delete the folder called ".wine" in your /home directory. Since it's an hidden directory you hit "ctrl - H" and you see the hidden files and folders. Remember that you will loose everything setup in wine. Then you have to do another ```
winecfg
```

---

### Post by haveacigar on 2007-01-22
Great :)

That was fine, i have only installed one program so far

Cheers

---

