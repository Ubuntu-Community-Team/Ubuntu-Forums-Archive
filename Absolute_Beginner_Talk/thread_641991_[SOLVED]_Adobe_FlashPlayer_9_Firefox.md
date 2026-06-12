---
title: "[SOLVED] Adobe FlashPlayer 9 Firefox"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by ShiningWolf on 2007-12-16
I downloaded Adobe Flashplayer 9 and untarred it. The installer now asks for the installation path for Mozilla. e.g. /usr/lib/mozilla.  I run kubuntu and this directory does not exits.

1) What is the right directory?
2) How could I have used the Add/Remove utility to do this, as Adobe is not listed?

Thanks!

---

### Post by Sef on 2007-12-16
> 2) How could I have used the Add/Remove utility to do this, as Adobe is not listed?

It is in Add/Remove; however, you need to set the top right box to "All Available Applications" because Adobe Flash is proprietary, and proprietary software is in the multiverse repository.  Once you do that, you will have the option to install Flash via Add/Remove.

---

### Post by erfahren on 2007-12-16
for the path: look in /usr/lib/firefox/plugins

Flash in the repositories is called "flashplugin-nonfree". You may need to enable extra repositories to be able to find it. see: [How to add extra repositories - Manual method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)

- that's for Ubuntu Gutsy, if it doesn't work for Kubuntu I'm sure there's an equivalent wiki for it.

(The Flash 9 in the repos currently has a bug for Ubuntu Gutsy, so I would just go ahead and use Adobe's installer).

---

### Post by ShiningWolf on 2007-12-16
Thanks. It worked.

PS: The right directory is /usr/lib/firefox

---

### Post by jfank on 2007-12-16
> **ShiningWolf said:**
> Thanks. It worked.

PS: The right directory is /usr/lib/firefox

That is awesome that you got it fixed and working correctly.  Just something for newbies though if you go to a website that requires flash media player to be installed just go to like xbox.com and it will give you the link to automatically install the newest version, and it should work in thunderbird as well.  This is another option for others that have the problem or may not know how to untar a downloaded program.

---

### Post by philinux on 2007-12-16
> **jfank said:**
> That is awesome that you got it fixed and working correctly.  Just something for newbies though if you go to a website that requires flash media player to be installed just go to like xbox.com and it will give you the link to automatically install the newest version, and it should work in thunderbird as well.  This is another option for others that have the problem or may not know how to untar a downloaded program.

Why bother downloading and untar (unzip) when the program is available in add/remove or synaptic. Much simpler.

---

### Post by jfank on 2007-12-16
Not the one you download and untar, when I had to install flash on my system it automatically installed it.  I didn't have to do anything except slick the missing plug-in and click accept and it installed it for me.

---

### Post by coolbrook on 2007-12-16
> **philinux said:**
> Why bother downloading and untar (unzip) when the program is available in add/remove or synaptic. Much simpler.

yet this is a recurring thread topic on here.  The direct download from Adobe seems to be the foolproof solution.

---

