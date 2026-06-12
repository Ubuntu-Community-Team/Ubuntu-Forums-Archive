---
title: "link for g streamer plugins"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by saurabhgupta on 2008-03-23
hi
from where can i get the link for downloading g streamer extra plugins...
kindly post the link...
i am quite amateur in ubuntu...

---

### Post by qamelian on 2008-03-23
Do a search in the Synaptic Package Manager for 'gstreamer'. The results will include all the available plugins.

---

### Post by billgoldberg on 2008-03-23
Just open up a terminal and copy/paste

```
sudo apt-get install ubuntu-restricted-extras
```

That will install most codecs.

Some won't be included, for those you need to add the medibuntu repo and then type:

[LINK]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/")

```
sudo apt-get install non-free-codecs
```

Note: you don't need to go on the internet and download installers like you did in windows. In ubuntu you can install 99% of the programs using add/remove or synaptic (and the command line).

---

