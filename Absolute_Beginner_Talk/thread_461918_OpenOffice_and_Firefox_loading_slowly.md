---
title: "OpenOffice and Firefox loading slowly"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by O-pos on 2007-06-02
Hello, I have following question:

when I start Ubuntu, and then start OpenOffice or Firefox for the first time it takes always long time and next time they are being loaded faster. So my question would be that how can I do so that al these libraries or whatever-it-is could be loaded while Ubuntu is being loading and then get rid of the long waiting periods after ubuntu has started.

Any ideas?

Thanks in advance

---

### Post by forestpixie on 2007-06-02
I might be wrong here- but I think that once you've run a program part of it stays resident in memory, so if you run it again it'll come up quicker.

Also I think I read in a thread that the os puts stuff in memory that it thinks you're going to need, could be wrong though.

To get them to start with Ubuntu you can System>Preferences>Sessions and add the programs you want to the startup programs tab - but I assume it'll just mean startup takes a bit longer to get them loaded.

 :) Hope I'm not leading you up the garden path!

---

### Post by happy-and-lost on 2007-06-02
*sudo apt-get install prelink preload*

Preload needs no further configuration. To set up prelink:
[I]
sudo gedit /etc/default/prelink[/I]

and make sure it contains the line **PRELINKING=yes**

then run *cd /etc/cron.daily*
and *sudo ./prelink*

to build the initial prelink database.

Then you can leave them both alone and forget about them. App startup times should be improved.

---

