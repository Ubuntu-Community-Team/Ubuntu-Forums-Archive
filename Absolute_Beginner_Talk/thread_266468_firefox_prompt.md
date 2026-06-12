---
title: "firefox prompt"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by chajuram on 2006-09-27
Hi,

Firefox used to prompt me what to do when I clicked on a particular file type (pdf, I don't use acrobat plugin). But at some point of time I might have checked the "do this everytime" button. I would like FF to promt me again. Where should I look? I tried looking in preferences without success.

Thanks,

Chajuram.

---

### Post by Metacarpal on 2006-09-27
In preferences, go to the Downloads tab.  There is a section marked "Download Actions".  Click the "View and Edit Actions" button.

This will produce a list of file types that Firefox has been set to automatically open, and the associated program.  Locate the file type you want to select manually (in this case, PDF), highlight it, then click "Remove Action"

---

### Post by chajuram on 2006-09-27
Thanks for you reply.

I tried doing that but there is no pdf in the list. It automatically saves pdf files. There must be a place which stores what file types are saved automatically, but I cant find them.

I also tried playing with about:config 
the three options

browser.helperApps.alwaysAsk.force (set to true)
browser.helperApps.neverAsk.openFile (pdf)
browser.helperApps.neverAsk.saveToDisk

but could not get it to work.

Chajuram.

---

### Post by mitch.c on 2006-09-27
> **chajuram said:**
> Thanks for you reply.
I also tried playing with about:config 
the three options

browser.helperApps.alwaysAsk.force (set to true)
browser.helperApps.neverAsk.openFile (pdf)
browser.helperApps.neverAsk.saveToDisk

but could not get it to work.

Chajuram.

I looked at my about:config and the description in preferential. I think what you want is:
```
browser.helperApps.alwaysAsk.force "true"
browser.helperApps.neverAsk.openFile "" # empty string
browser.helperApps.neverAsk.saveTo "" #empty string
```

---

### Post by chajuram on 2006-09-27
> **mitch.c said:**
> I looked at my about:config and the description in preferential. I think what you want is:
```
browser.helperApps.alwaysAsk.force "true"
browser.helperApps.neverAsk.openFile "" # empty string
browser.helperApps.neverAsk.saveTo "" #empty string
```

Hi,

My prefs.js file is exactly as above. still the thing does not work. I wonder where the information that "pdf" files shouldbe saved directly is stored on the computer. It should be under the advanced tab but is not.

Chajuram.

---

### Post by chajuram on 2006-10-11
All my above efforts did not work, so finally I deleted my profile (after saving the bookmarks) and restarted firefox. I still don't find pdf under prefs > downloads > advanced

but I will live with it.

Chajuram.

---

### Post by aysiu on 2006-10-11
This sort of an awkward workaround, but there's an extension called [PDF Download](https://addons.mozilla.org/firefox/636/) that allows you to configure PDF behavior--one of the options is to always prompt you for what to do.

---

