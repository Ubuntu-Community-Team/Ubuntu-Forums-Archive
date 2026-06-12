---
title: "XCircuit installation"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by Irid on 2007-03-04
Hi,
I wish to install a certain program named XCircuit. I can find it in Synaptic Package Manager (universe) and install it. However, it doesn't appear anywhere in my Applications menu. I tried to use "Search for files" without success. It isn't in /etc/ folder either (or its name has nothing to do with circuits). Luckily I'm able to type "xcircuit" in the terminal and it starts running, but sadly it crashes very often for stupid reasons, like saving your work.
I wonder if I can find in which folder it is located, and maybe there's a more convenient way to run it besides terminal, which hopefully would make it stop crashing.
Thanks.

---

### Post by bikeboy on 2007-03-04
I somehow don't think running it another way will reduce crashes. Unfortunately I have no solution for you one that. I don't know why it isn't in the menu either, have you logged out and back in? That usually resolves issues with new apps not appearing.

What I can help you with is some of the other q's. Once way to locate executables is using the "which" command.
```
which xcircuit
```

Something else you should know is that all executables are almost always in one of 2 locations, /bin and /usr/bin. They stand for binary I think, as in binary executable. So if you're ever looking for software that isn't in the menu or isn't a GUI app, look in those places 1st.

---

### Post by Irid on 2007-03-04
Incredible! Not only I found it in /usr/bin/, but also it recovered my last file that crashed. Now since it isn't in Applications, how may I put a shortcut in there?

---

### Post by Irid on 2007-03-04
OK, now I got another problem. It doesn't crash anymore, but it won't save files either. I wish to save my drawings to a .ps file, but when I click File->Write XCircuit PS->Write File I get a message "Can't open PS file" and I can't find my file anywhere. If I try to import a .ps file, XCircuit says it can't find it. It can load a New Library, though. How do I fix this?

---

### Post by Irid on 2007-03-04
I just figured it out myself. One must first create a blank .ps file, then load it to XCircuit, draw, and write to that file to see results. I somehow thought that since I can draw, the file is already automatically created...
No help needed anymore

---

