---
title: "installing software"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by mfraley65 on 2006-08-01
i am new to ubuntu.  i just installed it a few hours ago.  My question is how do i install software?  I downloaded 2 games and it will download the software and then i extract it.  Then i cannot install or use it.  What do i do?

---

### Post by Tomosaur on 2006-08-01
What are you using to download games?

---

### Post by aysiu on 2006-08-01
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by mfraley65 on 2006-08-01
I just clicked the link and the download manager thing came up.  It would download the file and then open the extractor.  After clicking extract it would put the files in tmp folder.

---

### Post by Tomosaur on 2006-08-01
Go to the folder the files extracted into, tell us what's in there.

---

### Post by mfraley65 on 2006-08-01
Folders: gconfd, keyring-95Hwq4m, orbit, ssh-quGEzs4813, virtual, mapping.

---

### Post by mfraley65 on 2006-08-01
Also the files pysol and pysol-4.82-src.tar.bz2

---

### Post by Tomosaur on 2006-08-01
well, I know orbit is a game at least. Go into that directory and look for a file ending with '.deb'. If there is one, double click it if you're in gnome, or if you're in a terminal, type 'sudo dpkg -i blah.deb' replacing 'blah' with whatever it's called. If there is no .deb file, check for a README which should explain how to install the game.

---

### Post by darrenm on 2006-08-01
Aside from the 2 games you are trying to install at the moment, just use Synaptic to install any software you need, enable all the repositories in the options and you should find almost anything in there.

Welcome to Ubuntu BTW. Stick with the learning cycle of using a proper OS and you will never look back :)

---

### Post by Tomosaur on 2006-08-01
Orbit is in the repositories btw, you can get it by just searching for it and clicking it in synaptic (then clicking apply :P)

---

### Post by mfraley65 on 2006-08-01
Thanks for the help, think i got it.

---

