---
title: "Azureus and jre1.6.0_05"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Lourie2 on 2008-04-19
I tried to install Azureus, it would not work and I needed to install Java Runtime Environment.  I downloaded the file and tried to install it.  It ended up on the desktop as a folder re1.6.0_05.  The strange thing is, above the folder, to the right, there is a ".  I also tried to delete the folder, but could not.  Needless to say, Azureus still does not work!

---

### Post by oldos2er on 2008-04-19
Type "sudo aptitude install sun-java6-jre" in a termnal.

---

### Post by Lourie2 on 2008-04-19
Thank you, I have now successfully installed Java RE.  This was necessary for Azureus to run.  Unfortunately, Azureus still only opens for a second or two and disappears.  I have tried advice to re-install Java, but to no avail!

---

### Post by prshah on 2008-04-19
> **Lourie2 said:**
> Thank you, I have now successfully installed Java RE.  This was necessary for Azureus to run.  Unfortunately, Azureus still only opens for a second or two and disappears.  I have tried advice to re-install Java, but to no avail!

This happen when the azureus settings are corrupted. Unfortunately it happens a lot. The fix is to delete the .azureus directory in your /home/username directory. eg ```
rm -rf ~/.azureus
```

Unfortunately this means that it removes your personalized settings for azureus. 

I had switched to Deluge (And am very happy with it) after facing these problems, but now have no idea if these problems are now fixed or not. maybe rather than delete the directory, you can try renaming it ```
mv ~/.azureus ~/azur-bak
``` and then see if azureus works.

---

### Post by Lourie2 on 2008-04-19
Thanks, PRShah, I removed the application and re-installed it and, VOILA!  It works!

---

