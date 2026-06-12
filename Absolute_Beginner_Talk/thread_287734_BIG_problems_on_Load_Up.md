---
title: "BIG problems on Load Up"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-10-29
I installed Kubuntu yesterday, everything was working correctly and I configured it just the way I wanted it. This morning I typed sudo reboot into the console and it was never the same afterwards.

Now when I turn on the computer it goes through the initilisation stuff e.g. loading essential drivers       ok.

However once this has finished it loads up a new image the blue kubuntu one with an empty progress bar and just does nothing. Its as if it is trying to load all of the stuff again but nothing comes up on screen it just halts at that image. If I go near the shutdown button on my case it loads the bootdown procedure e.g. stopping all processes etc...



Please help, I was just starting to love linux and thinking I would never need to go back to windows..

---

### Post by tommy1987 on 2006-10-29
Just managed to sort it, it turns out it didnt like my recent install of nvidia graphics card.. I just changed the xorg.conf back from saying nvidia to nv.

---

