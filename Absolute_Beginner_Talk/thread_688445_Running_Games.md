---
title: "Running Games"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by markbusu on 2008-02-05
Hi,

So i managed to get my system up and running, now i would like to try and run my first game and dont know how to got about it...

I am trying to run a game which requires a CD Emulation... (Not sure if you are famiiar with DEamon tools for Windows)

Do you know of any software i can use which will allow me to get a Virtual Drive and run an ISO / BST / IMG File?

Also, once that is complete,,, you can run the .exe to launch the application... How do i go about that?

Thanks for the info!

---

### Post by bumanie on 2008-02-05
Sorry, I can't answer your question precisely, but most users wishing to play .exe games either use wine (available from synaptic package manager) or pay for cedega ($5 per month, I have read) or set up a virtual environment such as vmware or virtualbox.

---

### Post by wolfen69 on 2008-02-05
with vmware or virtualbox, you will not be able to run 3D games. :-( cedega or wine are your best bets.

---

### Post by PeterJS on 2008-02-05
To mount an iso you can use:
```

sudo mount -o loop /some/path/some_iso.iso /mnt/where/you/want/it

```

Don't know about the other image formats.

And as said above, you're going to need wine to run windows software, and even then it's not %100. You might want to take a look at the app DB before wrestling with an impossible task.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

