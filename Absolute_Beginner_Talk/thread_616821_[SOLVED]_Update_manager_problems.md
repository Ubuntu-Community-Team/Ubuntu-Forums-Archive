---
title: "[SOLVED] Update manager problems"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by teryowen on 2007-11-18
I installed Ubuntu 7.10 no problems, when i turned it on it updated it everything went fine.

But when I installed Ubuntu 7.10 on my PC i forgot to connect to the network so that during installation it could download some security updates, and it gave me a warning saying it wont download but will do it later or something along those lines.

now though unlike my laptop when i start up the update manager never prompts me and when i go to turn it on there are no updates, but the first time i turned on my laptop i had like 50mb worth of updates maybe more.

Does anyone know the problem thats causing this

My internet works fine and so does my hard drive.

---

### Post by Beaucephus on 2007-11-18
The default for the update manager is to run once a week.  To start it manually try this from a console```
gksudo update-manager
```

---

### Post by teryowen on 2007-11-18
Doesn't work, i keep getting an error telling me to reload and it keeps trying to download the same 6 files but doesnt say it fails. some sort of error, i cant even use my add/remove utitlity.

EDIT: I figured it out!

I just had to go to Add/Remove and go to preferences and check mark the boxes for downloading from the net. Thanks! for the help anyways though.

---

