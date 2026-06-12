---
title: "Two Problems: Network Settings &amp; Sound Server"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by kylepe on 2007-07-29
Hello, I'm a newbie

    My first problem should be a fairly simple fix. Every time I restart my computer I have to select "wired network" from the network manager applet in order to access the net. I would like it to remember my selection so that I automatically have internet access every time I log in.

    The second problem is that my sound card only works when it wants to. When I restart my computer, half the time it plays the log in sound and works fine from then on, and the other half it will not play any sounds from the get go.

    I'm using a PIII 500MHz PC with Ubuntu 7.04

Any help much appreciated.

-Thanks

---

### Post by kylepe on 2007-07-29
OK, so I fixed the first problem:

```
sudo apt-get autoremove network-manager
```

and then I went to **System >> Administration >> Network** and unchecked and then rechecked the wired connection and it works! Now every time I reboot I have instant internet access.

Can anyone help me with the second problem? It's kinda annoying when I have to restart my computer and hope the sound works the next time. Or is there a way to restart the sound server, or a way to test the sound?

-Thanks

---

