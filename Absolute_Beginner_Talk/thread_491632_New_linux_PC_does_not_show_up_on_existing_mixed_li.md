---
title: "New linux PC does not show up on existing mixed linus windows network"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-07-03
I just installed linux onto a new ubuntu onto an old P3 and wanted to get into my existing network. I can see the other computers on my network but they cant see me.  What can I do to make this new linux comp show up on the network?

---

### Post by ajmorris on 2007-07-03
> **videocheez said:**
> I just installed linux onto a new ubuntu onto an old P3 and wanted to get into my existing network. I can see the other computers on my network but they cant see me.  What can I do to make this new linux comp show up on the network?

for the windows computers to see yours, you must install a package called samba. There are two ways to do this:

1) Go to menu>> system >>administration >> Synaptic Package Manager and find the package called samba, and mark it for installation. then install. or.....

2)Open a CLI (menu >> Programs >> Accessories >> Terminal) and type ```
sudo apt-get install samba
```

---

### Post by videocheez on 2007-07-03
thanks for the tip but I actually don't care if windows computers can see me. I really want to be able to see the other linux comp and the other 2 windows computers from the new drive.

I don't remember having this problem with the first installation of linux  onto my other computer.

---

