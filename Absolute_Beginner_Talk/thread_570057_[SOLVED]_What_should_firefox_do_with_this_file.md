---
title: "[SOLVED] What should firefox do with this file?"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by apauloisdead on 2007-10-07
I want deluge to be the default program to open torrent files with, but it's not in the drop down box in firefox, and when i click to browse, i have no idea where i would find deluge in the hd. Heck i don't even no what file extension the program would be.

So where are linux programs installed?

...and specificity where is deluge installed?

---

### Post by deadgobby on 2007-10-07
Deluge will be found in 7.04 Ubie under Applications>Internet. Deluge may open be default when you DL the bittorrent file. Like going to [http://thepiratebay.org/](http://thepiratebay.org/) 
 Deluge will open up and ask you where to save the file at. Like save it to desk top for easy access. To where firefox to save DL stuff. In firefox it will be edit>preferences
 Most of the programs you installed can be found Places>Home Folder>Files System>usr

Gobby

---

### Post by HokeyFry on 2007-10-07
most executables are stored in the /usr/bin folder of the hard drive. if its not there, check /bin. the name of the file you want will be whatever you type into a terminal to execute it.

---

### Post by wormser on 2007-10-07
Use the **whereis** command to find an executable.  Applications> Accessories> Terminal:

```
whereis deluge
```

To make torrent files associated with deluge.  Download and right click the torrent file.  Properties> Open With tab and select deluge.  If you never save the file then just do what you are trying to with Firefox.

---

### Post by apauloisdead on 2007-10-08
Thanks guys, everything really helped.

...and since this question isn't too off topic i figure ill just ask it here...

I just recently installed awn, but i noticed it installs to my home folder. Is there away to move that to the default "program files" directory (sorry, it's the windows in me), and then change where the "shortcuts" point?

---

### Post by Dr Small on 2007-10-08
All of the configuration files neccessary for some of your applications to run, create a *.programname* folder in you Home folder. The . hides the folder, but the program looks for the configuration file in that folder.

Most applications install to /usr/share or similar places.

Dr Small

---

### Post by apauloisdead on 2007-10-08
so should i just put a "." in the folder name? Because it's not hidden.

..and if i do this will all my shortcuts still work?

---

### Post by billybag on 2008-03-07
[http://kb.mozillazine.org/Changing_media_handling_behaviour#Changing_download_actions](http://kb.mozillazine.org/Changing_media_handling_behaviour#Changing_download_actions)

---

