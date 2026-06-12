---
title: "Download and Compile"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-26
1)  How do I compile and install a patch when all I have is the source code in a text file?

2)  Can I download directly from the repositories without using synaptic or apt-get?

Thanks,
Buck

---

### Post by diepruis on 2006-12-26
> **Buck2348 said:**
> 1)  How do I compile and install a patch when all I have is the source code in a text file?

One text file? What program is this?

> 2)  Can I download directly from the repositories without using synaptic or apt-get? Thanks,
Buck

I think you can, but why?

---

### Post by MkfIbK7a on 2006-12-26
> 2) Can I download directly from the repositories without using synaptic or apt-get?
yes but there is really no point

sorry i cant answer your first question:frown:

---

### Post by Buck2348 on 2006-12-26
> **diepruis said:**
> One text file? What program is this?
It's a patch for a bug in edgy.  I can find the patch text [here]("https://launchpad.net/distros/ubuntu/edgy/+source/gnome-vfs2/+bug/60277"), but haven't been able to find the package.

> **diepruis said:**
> I think you can, but why?
So I can browse the depositories for a package for which I don't know the exact name.

Buck

---

### Post by taurus on 2006-12-26
All you need is type a few letters in the Search field in synaptic and it will give you a list of programs that you can install!!!

---

### Post by halitech on 2006-12-26
why browse the repo? just open synaptic and do a search on what you think the name is

---

### Post by diepruis on 2006-12-26
> **Buck2348 said:**
> It's a patch for a bug in edgy.  I can find the patch text [here]("https://launchpad.net/distros/ubuntu/edgy/+source/gnome-vfs2/+bug/60277"), but haven't been able to find the package.

That is probably what is known as a diff file. It lists differences between source versions. You'd probably need to download the samba source and apply that patch, then compile samba. Have a look at the "patch" command for that.

Or, you can wait for that patch to be incorporated into the source of samba, download the source and compile that.

Or, you can wait for the a new version of the samba package and just upgrade to that using aptitude / apt / synaptic - if the bug is not that bad.

> **Buck2348 said:**
> So I can browse the depositories for a package for which I don't know the exact name.

Just use synaptic's search function. Alternatively, apt-get has such a function, as well as aptitude, like so:

```

aptitude search pattern

```

---

### Post by soundguy24 on 2006-12-26
You can search for your specific package and then download the .debs on [packages.ubuntu.com]("http://packages.ubuntu.com/").

---

### Post by lamego on 2006-12-26
If you never compiled a program from source, patching is not a good process to start with...

---

### Post by Buck2348 on 2006-12-26
> **diepruis said:**
> That is probably what is known as a diff file. It lists differences between source versions. You'd probably need to download the samba source and apply that patch, then compile samba. Have a look at the "patch" command for that.
The bug is in Gnome, not Samba, according to the web page I'm looking at.  They have a link to the patch which leads to a longish bit of text.  Of course I have no idea what to do with that, and as lamego notes, compiling and installing it is beyond me, though I would have a go at it if I could find a package and some googled help.

Thanks all for your replies.

Buck

---

