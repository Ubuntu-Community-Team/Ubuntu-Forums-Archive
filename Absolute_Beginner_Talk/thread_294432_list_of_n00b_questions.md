---
title: "list of n00b questions"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by deleopario on 2006-11-06
So probably most of this could be searched for to find the answer to this, and I apologize, but right now I don't have the right video drivers installed on my computer and every time I load a page it takes about five minutes for the screen to actually refresh. Just retrieving my password on here and logging in look me probably about half and hour, so searching through fifty threads to find what I need would take me a few years.

Anyway, as mentioned, my first priority is getting my video fixed. I have an nVidia gforce 6500. What repositories do I add to download the commercial drivers and where do I go to set them up?
Also how do I switch what the little volume button controls? Right now it's on analog center, but analog front is the one that actually changes my volume.
And also, I noticed Ubuntu doesn't have the artwork control panel thing like the last gnome distro I used did. Is there some way I can get that?
And finally (for the moment), is it safe to install xfce in addition to gnome? I really want to try it out.

---

### Post by ReaderRat on 2006-11-06
[**Installing Nvidia Drivers**](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
I can't help with the other questions.

---

### Post by pbaehr on 2006-11-06
Regarding the install for XFCE:

Yes, it's safe. You can install it alongside Gnome and if you install it using the method I'll link to below, it's easy to remove if you decide you don't want it.

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by limitedmage on 2006-11-06
To install XFCE, type in the terminal:

```

sudo aptitude install xubuntu-desktop

```

---

### Post by deleopario on 2006-11-06
Ah, working video. I feel like I can breathe again, thank you.

And thank you for the xfce info, I'm going to install that in just a minute now that my computer is useable again.

---

### Post by CatKiller on 2006-11-06
> **deleopario said:**
> 
And also, I noticed Ubuntu doesn't have the artwork control panel thing like the last gnome distro I used did. Is there some way I can get that?

The gnome-art package is in the [Universe repository]("https://help.ubuntu.com/community/Repositories"). See [here]("https://help.ubuntu.com/community/Repositories/Ubuntu") for information on how to enable this repository.

Welcome to the community.

---

