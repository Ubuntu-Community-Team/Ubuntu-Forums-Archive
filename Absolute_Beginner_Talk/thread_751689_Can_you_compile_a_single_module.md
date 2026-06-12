---
title: "Can you compile a single module?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Jason2gs on 2008-04-10
I've recompiled the Linux kernel several times, and my only complaint is that it takes so long to make the debs.

I'd like to do some testing with the bcm43xx driver (Trying out different patches, etc.), but the only way to update the kernel is to recompile it as a whole.

I just want to recompile the bcm43xx module.

Is this possible?

Thanks,

-Mike

---

### Post by Jason2gs on 2008-04-10
Two page rule!

---

### Post by Jason2gs on 2008-04-10
Two page rule :)

Please answer?

---

### Post by Tyke91 on 2008-04-10
please don't bump your own thread more frequently than once every 24 hours, there are people who are dedicated to checking older unanswered posts, so it's no big deal if you get off of the front page.

I know it's possible to do this with Gentoo, but I have no experience compiling in ubuntu, srry.

---

### Post by pytheas22 on 2008-04-10
If you had access to the bcm43xx code, I don't see why you couldn't just recompile that module and reinsert it.  The bcm43xx source should be under drivers/net/wireless/bcm43xx inside the kernel tarball.  Pull that into a directory and make, make install.  I'm not positive this would work, but it seems plausible.

By the way, why are you worried about recompiling bcm43xx in the first place?

---

### Post by Whiffle on 2008-04-10
Its entirely possible.  All you need is the source and the stuff to build it with.

---

### Post by Jason2gs on 2008-04-10
Tyke,

Ah, my apologizes. I didn't know. I was under the impression that once your thread gets down a ways, all hope is lost ^_^ Either recover it from the depths soon, or make a new one. *Shrugs*

Pytheas and Whiffle,

Either I'm misunderstanding you, or you're misunderstanding me.

The only thing I've been able to find documentation for, is recompiling the entire kernel, and replacing the current one with it. Not recompiling a single module.

Unless I'm wrong, a module is one part of the Linux kernel, correct?

I'm very new to Linux, so I'm not very knowledgable on this subject :(

---

### Post by mc4man on 2008-04-10
Maybe something like this
[http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html)

---

### Post by pytheas22 on 2008-04-10
I can give you step-by-step instructions for compiling the bcm43xx module, but before I do that, please tell me your ultimate goal is.  If you don't have much experience with Linux, I'm afraid you might be trying to do something much more complicated than you really need.  If you're having trouble with a Broadcom wireless card, this is not the first thing to try.  But as I said, if you really want to recompile the module, I can give directions, so let us know please.

---

### Post by Jason2gs on 2008-04-10
The card is working fine. I'd just like an easier way to compile a module, than compiling/reinstalling the whole kernel.

Mc4man,

Thank you for this page :) I'll take a look at it tomorrow. Gotta go right now.

---

### Post by pytheas22 on 2008-04-11
> The card is working fine. I'd just like an easier way to compile a module, than compiling/reinstalling the whole kernel.

Alright, thanks for the clarification.  In general, these are the steps needed to compile modules:

1. make sure you have a compiler, kernel headers and so on installed on your system, as these are necessary for building modules.  You can get these with the command:
```

sudo apt-get install build-essential
```

2. then you change to the directory in which the source code for the module is stored.  Chances are that you downloaded the module as a tarball (.tar.gz file, like .zip in Windows), so you would need to extract it first.

3. after that, you type "make" to build the binaries, and it will follow instructions in a file called the Makefile to compile the module.  If it doesn't give you any errors, the module gets compiled successfully.  After make completes, type "sudo make install" to copy the new module and any associated files to the proper directories in your system (the instructions to tell the system how to do this also in the Makefile).

Usually, that's how it works.  In some cases there are other steps required, or if the Makefile is poorly written, you may need to tweak it for compilation to work.  But any popular, well-written module should follow the steps above; if not, the procedure is usually explained in a file called README that gets distributed with the source code.

After modules get compiled, they need to be "inserted" with the insmod or modprobe -l commands.  Read more about this stuff if you're interested in understanding how modules work in Linux.

The source code of bcm43xx is merged with the kernel and the developers no longer make the code available as a separate download.  If you want to experiment compiling modules, you could grab the source for one of the Ralink wireless card drivers from [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads) , which compile using the instructions above.  Or, if you want to play with bcm43xx, you could extract the tarball of the kernel source and, as I mentioned earlier, remove from it the files related just to bcm43xx, which are kept together in their own subdirectory, and compile them with make.  But you shouldn't do this on your own system if your Broadcom wireless is already working, as you'll risk breaking it.

---

### Post by Jason2gs on 2008-04-11
Wow, thank you, Pytheas :)

That you for informing me about the bcm43xx lack of available source code ^_^

I extracted it and ran 'make', and it gave this:

```
mike@Juankubariz:~/Desktop/bcm43xx$ make
make: *** No targets.  Stop.

```

Why is this?

And is the .ko file, in current compiled kernel, the module?

Edit: About your warning at the end of your post... What if I backup the file/module bcm43xx? Then will I be able to move it right back if something screws up?

---

### Post by pytheas22 on 2008-04-11
The module doesn't build because the Makefile doesn't contain all of the instructions needed.  I think this is because the bcm43xx module is intended to be compiled with the rest of the kernel, so it's different than the Makefile you'd get if you were compiling just this one module.  Unfortunately, I don't know enough about Makefiles to figure out what to do.  Maybe someone else can help?
> 
About your warning at the end of your post... What if I backup the file/module bcm43xx? Then will I be able to move it right back if something screws up?

Yes, the .ko file is the module.  In principle I think it would work to back it up like this, but I've never tried so don't take my word for it.  It's possible that there are other files needed by bcm43xx.ko (kernel modules have dependencies, just like debian packages) that would also be replaced, so you'd want to back them up as well I imagine.

---

