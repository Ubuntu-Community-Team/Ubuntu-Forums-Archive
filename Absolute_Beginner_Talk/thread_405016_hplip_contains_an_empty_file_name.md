---
title: "hplip contains an empty file name"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-04-09
I can't believe with all the expertise on this forum someone can not help me here. Every time I try to install something I keep getting this error. Surely there has to be a way to fix it. I know, I screwed the file up myself but man, there's gotta be a fix somewhere.

Thanks

---

### Post by ThrobbingBrain66 on 2007-04-09
So are you saying that no matter what you try to install, you get that message and then the packages don't install?   I would suggest a purge of all the hplip files:
```
sudo apt-get remove --purge hplip hplip-data
```  Then reinstall them.  Hopefully that will get rid of your problem.

Patience young grasshopper, we'll get you sorted out. :)

---

### Post by captgadget on 2007-04-09
I tried that and it tells me package hplip is not installed, so not removed

---

### Post by ThrobbingBrain66 on 2007-04-09
Alright, try ```
sudo apt-get install -f hplip
```

I'm assuming that even if you tried to install hplip that you would get the same error as in the OP.  So, with the command above, we'll try to force it to install.

---

### Post by captgadget on 2007-04-09
Thanks, unfortunately I had to leave for work, but I will try it when I get home tonight. Thanks again and have a good day.

---

