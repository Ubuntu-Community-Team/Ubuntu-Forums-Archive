---
title: "Help building installs from source."
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by ceduriki on 2008-03-31
I've really had no problems with gutsy except one thing:
installs from  source packages. Thank God the programs I wanted were available through Synaptic, but it's kind of starting to get annoying. At first I realized I just didn't have the compiler tools (which were default on Fiesty) so I installed them, and still no go. What could be wrong?

---

### Post by kellemes on 2008-03-31
Please tell us what you're doing to install a source package.. so we know what you're doing wrong.

How to install anything in Ubuntu..
[http://cutlersoftware.com/ubuntuinstall/]("http://cutlersoftware.com/ubuntuinstall/")

---

### Post by ceduriki on 2008-03-31
I've read the guide.

I just do it the way I usually do:
decompress the folder
cd to the folder
./configure
make
then sudo checkinstall which doesn't work so i try
make install which also gives me abort errors.

---

### Post by kevdog on 2008-03-31
Did you get any errors during the configure or make process?  What errors are you getting now?

---

### Post by ceduriki on 2008-03-31
Well, right now I'm trying to install Brightside from source, and it's telling me there's no makefile. I checked and it's there.

---

