---
title: "youtube videos in konqueror and opera?"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-11-01
how do i get youtube videos to play in konqueror? i can play them in epiphany and firefox.

---

### Post by vixenk on 2006-11-01
You have to install a package that allows non-Mozilla browsers to use the Mozilla plugins.

Close out of any open browsers and type this in terminal:
> sudo apt-get install mozplugger

After that your plugins should work. :)

---

### Post by Jucato on 2006-11-01
If you installed the package "flashplugin-nonfree" to get Flash on Firefox and Opera, all you need to do is go to Konqueror Settings menu -> Configure Konqueror -> Plugins, and click on Scan for new plugins. It will automatically detect Flash.

---

### Post by fuscia on 2006-11-01
i used automatix to install flash. nothing seems to have worked. no big deal. i just dumped kde, *again*, for now (i'll probably reinstall it after lunch. who knows?). thanks for the responses.

---

### Post by arnieboy on 2006-11-01
> **fuscia said:**
> i used automatix to install flash. nothing seems to have worked. no big deal. i just dumped kde, *again*, for now (i'll probably reinstall it after lunch. who knows?). thanks for the responses.

currently AX2 installs flash only for Firefox and Swiftfox. We plan to add support for opera and konqueror in the future.

---

