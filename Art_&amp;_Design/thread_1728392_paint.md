---
title: "paint"
date: 2011-04-13
forum: Art &amp; Design
---

### Post by baronn on 2011-04-13
hello. I'm looking for some app similar to Window's paint as simple and as usefull. Thank you!!

---

### Post by baronn on 2011-04-13
I've tried installing gimp, with 

"apt-get install gimp" 

but I get 

"E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? "

any suggestions?

---

### Post by matt-fender on 2011-04-13
> **baronn said:**
> I've tried installing gimp, with 

"apt-get install gimp" 

but I get 

"E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? "

any suggestions?

You must use sudo

"sudo apt-get install gimp"

:)

---

### Post by ImDougy on 2011-04-13
well gimp is more photoshop than it is paint... 

there's quite a few like Kolourpaint, GNU Paint, Tuxpaint(this one is kinda for kids but u could try lol), Inkscape, and i know there's many more. they're all in the ubuntu repos so open up ubuntu software center and try them for yourself in the graphics category. i think GNU paint or GNUpaint(not sure if it's one or 2 words) is pretty good.

---

### Post by baronn on 2011-04-13
> **matt-fender said:**
> You must use sudo

"sudo apt-get install gimp"

:)

ofc. Stupid me! :S

> **ImDougy said:**
> well gimp is more photoshop than it is paint... 

there's quite a few like Kolourpaint, GNU Paint, Tuxpaint(this one is kinda for kids but u could try lol), Inkscape, and i know there's many more. they're all in the ubuntu repos so open up ubuntu software center and try them for yourself in the graphics category. i think GNU paint or GNUpaint(not sure if it's one or 2 words) is pretty good.

hmmm. Ok. How do I install GNU paint? Via the terminal, or by downloading a file, and then installing it? I've dowloaded and extraxted a package from [here]("http://linux.softpedia.com/get/Multimedia/Graphics/GNU-Paint-28043.shtml"), but can't find an .exe (or it would be .exe in Windows - I've only recently changed.

---

### Post by cgroza on 2011-04-13
> **baronn said:**
> ofc. Stupid me! :S



hmmm. Ok. How do I install GNU paint? Via the terminal, or by downloading a file, and then installing it? I've dowloaded and extraxted a package from [here]("http://linux.softpedia.com/get/Multimedia/Graphics/GNU-Paint-28043.shtml"), but can't find an .exe (or it would be .exe in Windows - I've only recently changed.
Extract the archive, cd to the directory and do:
```

make
sudo make install

```

---

### Post by ImDougy on 2011-04-13
there is an easier way than downloading the package from a website and installing it :D that's the windows way of installing programs.

open the applications menu and click ubuntu software center and search for what you like. after searching for gnu paint just click the install button and let it install. after that it should be in the graphics menu under applications

---

### Post by baronn on 2011-04-13
> **cgroza said:**
> Extract the archive, cd to the directory and do:
```

make
sudo make install

```

:-? didn't quite understand what to do ....

> **ImDougy said:**
> there is an easier way than downloading the package from a website and installing it :D that's the windows way of installing programs.

open the applications menu and click ubuntu software center and search for what you like. after searching for gnu paint just click the install button and let it install. after that it should be in the graphics menu under applications

:lol: Got it! Cooool! \\:D/ Just what I was looking for!

Windows just keep looking more and more stupid. The only "negative" (which for more experienced users, I guess, is positive) is that you actually have to configure a lot...

---

### Post by ImDougy on 2011-04-13
lol i'm glad to help

---

