---
title: "Shortyland05 is thinkin bout converting!"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Shortyland05 on 2007-02-15
Hi, Im Shortyland05 and I have just joined these forums, downloaded ubuntu (both ordinary and 64bit), and just done a live demonstration. Im just asking a couple of things...

1. How much different is ubuntu from Windows?

2. Do I need to know the 'Code' in order to install things?

3. any tips on Wine (cause I still like my games!), actual installing of Ubuntu, and the basics :D

4.edit: one more question, would it be a good idea to grab the linux versions of my sound/motherboard/graphics/etc drivers?

Thank you very much!

---

### Post by rai4shu2 on 2007-02-15
1. It takes a week or two to adjust, for most people. Depends on how good your Google-fu is. :)
2. No. Just look up Synaptic in the wiki or search for other specific things in the forums here.
3. If you use Wine in 64-bit, make sure you read the wiki entry on that first.
4. You should rely on Synaptic or apt-get for most of your drivers. I've noticed that people using Envy for nVidia drivers, for example, tend to have a lot of problems later on. You would be better off I think to just install "nvidia-glx" from the standard repo if you have an nVidia card.

---

### Post by igknighted on 2007-02-15
> **Shortyland05 said:**
> Hi, Im Shortyland05 and I have just joined these forums, downloaded ubuntu (both ordinary and 64bit), and just done a live demonstration. Im just asking a couple of things...

1. How much different is ubuntu from Windows?
...
4.edit: one more question, would it be a good idea to grab the linux versions of my sound/motherboard/graphics/etc drivers?

Thank you very much!

1) Do not, whatever you do, try ubuntu while thinking about it in relation to windows.  It is something new, treat it as though you are learning something brand new.  If you don't, you will have a lot of problems.

4) As for the graphics drivers, I will digress from the previous poster.  All drivers should be available in synaptic, but do be cautious with the graphics drivers if you have NVIDIA.  If you have an nvidia card and a dual core processor, be aware that the kernel it will want to install my limit you to one core (if it asks you to install the i386 kernel this is only single core supported I believe).  If this is the case, download the envy script or just go to the NVIDIA page and download the .bin file.  Read their instructions carefully, they are strange if you are new, but straight forward.

---

