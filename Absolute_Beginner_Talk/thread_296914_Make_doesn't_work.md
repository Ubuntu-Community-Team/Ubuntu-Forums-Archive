---
title: "Make doesn't work"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by Exxar on 2006-11-10
I need to mound ccd images so I went to install CDemu, and the install process requires me to run "$ make" and "$ sudo make install". When I run make i get the error
```

Makefile:31: *** You'll need sources for your (at least 2.6.16) kernel.  Stop.
```

How do I get and install sources for my kernel? I think I'm running kernel-2.6.27-386, but how can I verify that? I'm running Dapper.

---

### Post by Bachstelze on 2006-11-10
```
sudo apt-get install linux-headers-$(uname -r)
```

will install the kernel headers (I don't think you need the full source) for your current running kernel. Keep in mind though that you'll have to rebuild the module whenever you upgrade your kernel.

---

### Post by ape on 2006-11-10
These steps should get you going...

1. Issue the following command:

      uname -r

   This will tell you the version of the kernel you're running.  

2. Issue the following command:

      sudo apt-get install linux-source

   This will download the version of the kernel source that matches your kernel version.  The tar file will be downloaded into the /usr/src location.

3. Change to the /usr/src location and unpack the tar file.  It will create a 'linux-source-<number>' directory.  I always create a linux symlink to this directory using the command 'sudo ln -s linux-source-<number> linux'.  I don't know if it's required or not, but it hasn't failed me yet.

Now that you have the kernel source installed, try your make command again.

Good luck. I hope I haven't forgotten anything.

--ape--

---

### Post by Exxar on 2006-11-10
Followed through your instructions, but alas...

It seems that I am using kernel 2.6.15.27, and make requires at least kernel 2.6.16.*

I suppose I have to install a newer kernel?

---

### Post by Bachstelze on 2006-11-10
Upgrade to Edgy :)

---

### Post by Exxar on 2006-11-10
Well, since I'm a complete linux n00b I'd rather stay on Dapper ;)

---

### Post by Bachstelze on 2006-11-10
Then say goodbye to CDemu because if you want a 2.6.16 kernel in Dapper, you'll have to compile it yourself, which will be much more complicated than upgrading to Edgy.

---

### Post by spinflick on 2006-11-10
HymnToLife your avatar always makes me smile :mrgreen: its as if your avatar is speaking what you are typing ;)

---

### Post by CatKiller on 2006-11-10
> **Exxar said:**
> I need to mound ccd images so I went to install CDemu

You can mount cd images with the **mount** command. You don't get pretty pictures, it's true, but it's got to be easier than compiling a new kernel from source, surely?

```
mount -o loop -t iso9660 *isoname*.iso /*mount*/*point*/*path*/
```

You can use **bchunk** if your cd image is in a freaky format - that's in the Universe repository.

---

### Post by Exxar on 2006-11-10
The problem is I need to mount ccd/cue image files, not iso images. Thanks anyway. Ill convert them to isos on my windows box.

---

### Post by CatKiller on 2006-11-10
From **man bchunk**:

>        bchunk converts a CD image in a ".bin / .cue" format (sometimes ".raw /
       .cue") to a set of .iso and .cdr tracks.
 I don't know if that's the same thing.

---

