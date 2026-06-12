---
title: "Install AWM through Synaptic?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by Bart_D on 2007-08-25
Hello, I am trying to install AWM desktop manager (the dock) and I would like to know if I can do this using Synaptic.  I would prefer to use Synaptic so I can uninstall if it crashes my system.

Please let me know if this (Synaptic version) is a stable version and if there are some other setps I should be aware of before I try to install.

---

### Post by PriceChild on 2007-08-25
AWN isn't in the Ubuntu repositories sorry.

---

### Post by Bart_D on 2007-08-25
What would be the easiest way to install it correctly?

---

### Post by Steveway on 2007-08-25
Trevino has it in his Repositorys.
Use Google to find out how to add his Repo.

---

### Post by Bart_D on 2007-08-25
Actually, in the process of installing Compiz Fusion, I did this:

```
gksudo "gedit /etc/apt/sources.list"
``` 

I added:

# compiz-fusion by Treviño's Ubuntu feisty EyeCandy Repository
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

Does this mean that I have his repositories enabled?

---

### Post by isaacj87 on 2007-08-25
Don't use that version it's really old and out of date.

Use reacocard's repo

The best way is to download the src and compile...

I'll check reacocard's repo and tell you how to add it. Or you could google it. :)

---

### Post by Steveway on 2007-08-25
I think.
Try this:
sudo apt-get install avant-window-navigator

EDIT: Old? His Version is: 0.1.2+svn20070822~3v1ubuntu0
That is 3 days.

---

### Post by isaacj87 on 2007-08-25
****I fixed the instructions****
Here's how to do it:

Just go to terminal and type:

```

gksudo gedit /etc/apt/sources.list

```

Copy and paste this at the bottom

```

deb http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 feisty avant-window-navigator

```

Add the key:
```

wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -

```

Save and close...
Update..

```

sudo apt-get update

```

And go back into synaptic...search for avant and install the** bzr** version...Not the SVN (that's trevino's)

All done! :)

---

### Post by isaacj87 on 2007-08-25
> **Steveway said:**
> I think.
Try this:
sudo apt-get install avant-window-navigator

EDIT: Old? His Version is: 0.1.2+svn20070822~3v1ubuntu0
That is 3 days.

Hmm...I don't know actually. It's strange he's still calling it svn, because they abandoned it for bzr? I'd use Reacocard's version anyways, he's always on the AWN forum following the development closely.

---

### Post by amadeus266 on 2007-08-25
No GPG key. Do you have it?

---

### Post by isaacj87 on 2007-08-25
**SORRY!**

I goofed up....here it is...

```

wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -

```

Try that.

---

