---
title: "Can't view DVD movie in color"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Aholiab on 2007-12-22
I just watched The Lion, the Witch, and the Wardrobe, and Totem wouldn't play it at all. MPlayer and VLC would both play it, but neither showed the color.

Can someone help?

I'm in Gutsy, and I think it's up to date.

---

### Post by djchandler on 2007-12-22
> **Aholiab said:**
> I just watched The Lion, the Witch, and the Wardrobe, and Totem wouldn't play it at all. MPlayer and VLC would both play it, but neither showed the color.

Can someone help?

I'm in Gutsy, and I think it's up to date.

What video card do you have, and which driver are you using?

---

### Post by Aholiab on 2007-12-22
All I know about the graphics card is this: Intel® Graphics Media Accelerator 900;  128MB Dynamically Shared (RAM/Video) Memory

I can't tell you the driver, except it probably is the default Gutsy driver: I didn't select anything.

Is this helpful? Should I hunt for more information?

---

### Post by p_quarles on 2007-12-22
Did you install the DVD codecs from Medibuntu?

---

### Post by Aholiab on 2007-12-22
I can't promise that I didn't install them from Medibuntu, but I don't think so. I don't think I've installed anything from there.

---

### Post by p_quarles on 2007-12-22
> **Aholiab said:**
> I can't promise that I didn't install them from Medibuntu, but I don't think so. I don't think I've installed anything from there.
That could be the problem, then. Some DVD codecs are not installed by default because of patent questions. This guide will explain the issue, as well as give you step-by-step instructions for installing the codecs:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Hope that resolves it for you. If not, let us know.

---

### Post by Aholiab on 2007-12-22
Thank-you. It's solved now. I added the Medibuntu repository and my system automatically updated, and now VLC plays it in color.

MPlayer still doesn't work, and Totem doesn't work, either. Should I/could I uninstall them? VLC seems to do what I need.

---

### Post by p_quarles on 2007-12-22
> **Aholiab said:**
> Thank-you. It's solved now. I added the Medibuntu repository and my system automatically updated, and now VLC plays it in color.

MPlayer still doesn't work, and Totem doesn't work, either. Should I/could I uninstall them? VLC seems to do what I need.
Yes, you can uninstall those. I'm sure you could get them to work, but if you're happy with VLC, there's no point in extra work, right?

Just go to the Synaptic Package Manager in your system menu, search for those packages, and mark them for removal. 

Also, if you remove Totem, Synaptic will tell you that it's also removing the package called "ubuntu-desktop." This sounds much scarier than it actually is -- ubuntu-desktop isn't actually a program, it's just a text file that has a number of dependencies, including Totem. It makes the installation process easier, and that's all it does. Removing it won't do anything. Of course, if you'd rather not, there's no harm in just leaving Totem on the system.

---

### Post by Aholiab on 2007-12-23
Could you or someone point me to a way to get Totem to do this? Or should I just use VLC? Totem seems to be the distro standard.

---

