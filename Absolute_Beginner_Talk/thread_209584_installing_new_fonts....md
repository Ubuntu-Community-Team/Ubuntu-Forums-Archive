---
title: "installing new fonts..."
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by jclmusic on 2006-07-05
i've got the hang of the 'gksudo nautilus' command, but, which folder do i copy them into?

---

### Post by jclmusic on 2006-07-05
don't worry, just found out!

---

### Post by ciscosurfer on 2006-07-05
First, make sure that Defoma (Debian Font Manager) is configured to manage your fonts:```

sudo dpkg-reconfigure defoma
``` If Defoma is not currently set to manage fonts, you will be asked if you want to use it; answer Yes.   If your system has ended up in an unclean state with some manually installed fonts or apps that can't see some fonts, you can force Defoma to toally rebuild its configuration:```

sudo defoma-reconfigure
``` Lastly, on your desktop or in a file-browser, type CTRL-L to access the Open Location window; then type **fonts:/// **then click Open.  You will then get a list of all the fonts you currently have access to on your system.  Drag your new fonts from wherever they are located into the font-list window, and they will be automatically installed and made available to Defoma the next time they start up.

Aside: the **fonts:///** location is actually a virtual view of the fonts installed on your system.  When you access this folder, your fonts are actually stored inside a hidden folder called **.fonts** inside your home directory.  For example:```
cd ~/.fonts    #changes to your home directory and enters the hidden folder ".fonts"
ls -a    #to see your hidden files
```if you can't see your fonts, don't worry...trust me, they're there.  Just remember **fonts:///** and you'll be fine! :D

---

### Post by ricardisimo on 2007-01-12
Can I drag a whole "Fonts" folder into fonts:///, even if it has all sorts of sub-folders and zip files in it? Or do I have to drag and drop each TTF into the window? Thanks in advance.

---

