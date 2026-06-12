---
title: "Feisty Update -- Error During Update"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by Stunt Double on 2007-05-29
I tried to update to Feisty from Edgy by using the update manager . 
It returns a message: ERROR DURING UPDATE
     A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch: [http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.gz)
and
Failed to fetch: [http://us.archive.ubuntu,com/ubuntu/dists/edgy/multiverse/source/Sources.gz](http://us.archive.ubuntu,com/ubuntu/dists/edgy/multiverse/source/Sources.gz)

 I regularly update everything else with no problem. Firefox, Thunderbird, Evolution, and Synaptic all seem to work well.
Is there a solution?
  Edit: It isn't showing the complete information. 
....com/ubuntu/dists/edgy/main/source/Sources...
....com/ubuntu/dists/edgy/multiverse/source/Sources...

---

### Post by dbbolton on 2007-05-29
open /etc/apt/sources.list with gedit, then find & replace "edgy" to "feisty". run Synaptic and click "mark all upgrades" then "apply".

---

