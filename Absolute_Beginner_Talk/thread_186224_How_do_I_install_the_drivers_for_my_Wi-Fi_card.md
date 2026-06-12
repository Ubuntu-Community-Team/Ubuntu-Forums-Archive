---
title: "How do I install the drivers for my Wi-Fi card?"
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-06-01
I'm at [this step]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto#head-ccd66d4fcaaab3a6e7a5c47162c1b7c6f52d41e5") of the wiki on how to install my Wi-Fi card, specifically, step 7. I believe I've found the proper Wi-fi driver (or at least, I've narrowed it down to 2 possible zip files).  It tells me to run some stuff from the terminal, and I'm not sure how to unpack with that, nor do I know how to put them where they need to be (the zip files are just hanging out on my desktop right now).

---

### Post by jgoguen on 2006-06-01
You don't need to worry about a "right place" to put the drivers, ndiswrapper will handle that for you.  Just unzip the ZIP package, run ndiswrapper as described, and you should be good to go.

So you have the files on your desktop, unzip and run 
```
sudo ndiswrapper -i ~/Desktop/driver_folder/driver_file.inf
```
Replace driver_folder with the name of the folder on your desktop and driver_file.inf with the name of the inf file in that directory.  Then continue on with the wiki directions.

---

### Post by Amablue on 2006-06-01
Okay, so I typed ```
sudo ndiswrapper -i ~/Desktop/80211g/bcmwl5a.inf
``` and then it asks for a password (which I assume is my logon password), then it gives me the error "command not found".

---

### Post by catlett on 2006-06-01
> Unpack the Windows driver by using the unzip, cabextract and/or unshield tools (run from the Terminal), and find the INF file (.INF or .inf extension) and the SYS file (.SYS or .sys extension). You may first need to install cabextract and unshield
Is this the part your talking about? With ubuntu you can browse to the file graphically (the file manager is called nautilus, you launch it through Places<home or places<computer) When you get to the file right click on it and choose "extract here". This will "unzip" the file for you. You can do it from the command line like the wiki says but this way is easier if not faster>

Personally I would try using  ndisgtk since it is graphical. Plus it is synaptic, which means it is easy to install. Go to the top of the screen. Hit on System then Administration and finally Synaptic Package Manager. When synaptic opens hit on the search button. Enter "ndisgtk", it will bring up the listing. Right click and choose mark for installation. Hit "apply" at the top of the window. It will then install the package. This link from your wiki should help with ndisgtk [http://lxer.com/module/newswire/view/46385/](http://lxer.com/module/newswire/view/46385/) Good Luck. If you have more problems post.

---

### Post by Amablue on 2006-06-02
That tool was a great help. I think I'm at the last step before I'm freed from the living room. This feels like this is something I'm just completely overlooking, but I can't figure out what my connection settings (Configuration, IP Address, Subnet Mask, gateway address). Where do I find these? or find information on finding them?

---

