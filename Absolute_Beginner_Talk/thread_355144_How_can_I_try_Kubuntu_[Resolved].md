---
title: "How can I try Kubuntu? [Resolved]"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by mitchbones on 2007-02-06
I have been using gnome for about 3 months know and I want to try out KDE. I tried doing ```

sudo aptitude install kubuntu-desktop

Need to get 101MB of archives. After unpacking 307MB will be used.
The following packages have unmet dependencies:
  openoffice.org-common: Conflicts: openoffice.org-mimelnk but 1.1.5-0ubuntu1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gwenview [Not Installed]
kipi-plugins [Not Installed]
koffice-data [Not Installed]
koffice-libs [Not Installed]
krita [Not Installed]
kubuntu-desktop [Not Installed]
openoffice.org-mimelnk [Not Installed]

Score is 53

Accept this solution? [Y/n/q/?]   

```
I am unsure about this part, I said to quit then it came up with a window in the terminal that asked a bunch of questions that the guide I was using didn't mention. I hit exit  and now I can't get it to work :( Any ideas on how I can get this to work?

Thanks.

---

### Post by aysiu on 2007-02-06
Dependency problems usually stem from conflicting repositories.

Get a fresh set of repositories by following these instructions:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try again: ```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

---

### Post by mitchbones on 2007-02-06
It worked! Thanks alot aysiu

---

