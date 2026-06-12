---
title: "[SOLVED] Flash stopped working after update (x64)"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by dinostabOMG on 2008-02-06
I updated flash after seeing the latest update today. I've uninstalled and reinstalled both flashplugin-nonfree and gnash. I *knew* I should have gone with "if it ain't broke, don't fix it." Argh!!

Any ideas? If I go to a site that uses it, [www.pandora.com](www.pandora.com) for example, I get "click here to download plugin." When I do that, it says no suitable plugins were found, but I can click the Manual install button. If I do, I get a download page from Adobe with a .tar.gz file - I don't know what to do with this. But reinstalling from synaptic doesn't help, neither with flashplugin-nonfree nor with gnash.

---

### Post by ptn107 on 2008-02-06
It's breaking for everybody, but here's a quick fix.  Copy and paste (all one command)

```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree -y
```

I.E. just a quick uninstall-purge and reinstall.

---

### Post by Mguel on 2008-02-06
thanks, it worked

---

### Post by dinostabOMG on 2008-02-06
Cool, thank you. Out of curiosity, why is this different from what I did?

---

### Post by studo77 on 2008-02-07
It is --purge that does it. It is a Complete removal. Which is what you can choose in Synaptic.

You only did a reinstall, without removing it, or only a normal uninstall. which does not remove everything.

---

### Post by amazingtaters on 2008-02-07
Thanks for the fix

---

### Post by dca on 2008-02-07
This is how I install it but I DON'T recommend it unless you know what you're doing:
 
1) Download latest Flash for Linux (tarball) from Adobe's website.
2) right-click and extract to same location (your Desktop).
3) at CLI type:  gksudo nautilus &   (which opens nautilus window as root)
4) navigate to extracted directory and copy 'libflashplayer.so' file.
5) navigate and paste into: /usr/lib/mozilla/plugins AND /usr/lib/firefox/plugins
 
This way all user(s) have access to flash when logged in...

---

