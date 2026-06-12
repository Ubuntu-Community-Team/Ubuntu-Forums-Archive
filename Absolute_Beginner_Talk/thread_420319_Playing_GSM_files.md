---
title: "Playing GSM files"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by arya6000 on 2007-04-23
Hello

Are there any programs for Ubuntu that can play GSM files? It would be even better if it gives me the ability to edit them too


Thanks

---

### Post by Atomic Dog on 2007-07-02
> **arya6000 said:**
> Hello

Are there any programs for Ubuntu that can play GSM files? It would be even better if it gives me the ability to edit them too


Thanks

I'm going to bump this up as I have a need for this too.  Anybody know of a player that will handle .gsm files?

---

### Post by Atomic Dog on 2007-07-04
I can only play them with SoX installed, but of course it's a command line "play filename.gsm."  A gui based application would really be nice but so far I have not found a gui app that can handle .gsm files.

---

### Post by pocketman on 2008-05-08
Not exactly what you were looking for, but one step above typing 'play mylongfilenamehere.gsm' over and over...

Go to your home folder, show hidden files, open .gnome2 folder, open nautilus-scripts, create a new file called 'play sound with sox', make sure it's executable and paste the following in:


 #!/bin/sh
    ### play this soundfile
    play $*

bingo...right click on any sound file or multiple sound files, look under the scripts menu and choose 'play sound with sox'.  Make sure you have all the required sox codecs by typing: 

sudo apt-get install libsox-fmt-*



Good luck and happy listening. :)

---

