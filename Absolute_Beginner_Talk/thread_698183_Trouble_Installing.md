---
title: "Trouble Installing"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by onthefence on 2008-02-16
I'm trying to install thunderbird and am running into an apparent problem with the graphical install utility through "Add/Remove" option.

When I go to select thunderbird i get a dialog(See attached image.) When I click to refresh the list of applications it tries to download something, then goes back to square one.

I tried rebooting, I can't find it in Synaptics. I tried downloading the tarball but no instructions to manually install. 

Someone can probably give me the apt-get command for thunderbord but then I'm still left with my Add/Remove programs problem. What gives?

Thanks

---

### Post by perce on 2008-02-16
Go to Synaptic > Settings > repositories and make sure that all repositories are checked, with the exception of source code. Then press reload, and try again installing thunderbird.

---

### Post by Presto123 on 2008-02-16
First off, check in System/Administration/Software Sources and in the first tab marked "Ubuntu Software" make sure that all but "Source Code" are checked. Let it reload and try again...if that doesn't work...use:

```
sudo apt-get update
sudo apt-get install thunderbird
```

*LOL you beat me too. Everyone beats me...maybe I need to type faster! :P **

---

### Post by onthefence on 2008-02-16
Thanks i forgot about adding the extra repositories, i'll get the hang of it one day.

you guys are the best

---

