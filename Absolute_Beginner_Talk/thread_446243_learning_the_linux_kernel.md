---
title: "learning the linux kernel"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by rbprogrammer on 2007-05-16
not sure if this is the place to put this thread, but i really want to learn this..

i downloaded [FONT="Courier New"]linux-0.01.tar.bz2[/FONT] and [FONT="Courier New"]linux-1.0.tar.bz2[/FONT] from [http://www.kernel.org/pub/]("http://www.kernel.org/pub/") and i want to compile this to put it on a little USB drive so that when i boot it up i can see exactly how it works.  then modify it so that i can get a feel for how an operating system really works.  not sure which one to use, i would prefer the first kernel i mentioned since it is smaller.  i assume i just open a terminal at the directory and run [FONT="Courier New"]make[/FONT]. but when i do i get this error:
```
$ make
gas -c -o boot/head.o boot/head.s
make: gas: Command not found
make: *** [boot/head.o] Error 127

```

or if i try to change the assembly compiler to "as" instead of "gas" i get:
```
$ make
as -c -o boot/head.o boot/head.s
as: unrecognized option `-c'
make: *** [boot/head.o] Error 1

```

where do i get gas? :lolflag: 

and also, am i going about this the right way?  i just want a really basic linux kernel (basic as in just a command line interface, nothing extravagant) to learn from.  also, will it boot?  because i'm concerned that my computer is too "new" for this old kernel.  all i need is the keyboard to work with the monitor.

any help is greatly appreciated.

---

### Post by machoo02 on 2007-05-16
Out of curiousity, why do you want to use such an early kernel version?  It probably lacks several important things, such as USB support (but don't quote me on that).

Why don't you check out [this book]("http://www.kroah.com/lkn/") that was written by one of the main kernel developers.

---

### Post by rbprogrammer on 2007-05-17
i want to work with an early kernel because it does not have a lot to it.  i want to learn how an operating system really works, and i think the best way (for me at least) to do that is to use one of the older version that does not have a lot of code to it.  then i would be able to find its flaws and try to improve on it.  my philosophy is that the best way to understand something is to throw it away and build your own.  experience is the greatest teacher..

and on the note that USB support may not be available, do you think i could then just use a floppy disk?  would that be better?

---

### Post by Cypher on 2007-05-17
Wow..Kernel 1.0? Interesting.

GAS is part of "binutils". If ever you can't find a particular application, go to the handy [http://packages.ubuntu.com](http://packages.ubuntu.com) and search for it.

I can appreciate your thinking of starting with the earlier Kernel with less code and learning about it, but realize that going too early might mean that the Kernel might not even work.

Rather than falling all the way back to the 1.0 Kernel, you'll have much better luck with the 2.4 tree. The 2.6 tree, especially in recent releases, has added a LOT of interesting and complicated features. The 2.4 tree is less complicated...comparatively..:)

But also realize that all professional Linux work is largely done on the 2.6 Kernel, so the knowledge you gain from the 2.4 Kernel will have to be augmented by the differences in the 2.4 and 2.6 Kernel to be truly complete.

---

### Post by FuturePast on 2007-05-17
I'm not sure you're going about this the right way.

The kernel (at least these days) has a complicated build system which has its own configuration system.
You would at least need to run ./configure.
And certainly kernel-0.01 will not have a command-line interface. A kernel is just that; a core.

I think you will do much better if you take a look at something like [Linux from Scratch]("http://www.linuxfromscratch.org/").

---

### Post by rbprogrammer on 2007-05-18
all i really want is a really simple kernel that has a command line interface... i guess that old kernel was just a start ( obviously i tried to start too easy ).  what version should do you guys think i should start with?  it sounds like what Cypher is saying is that the version 2.4 tree would be simple enough but with the support of some hardware.  and as far as what FuturePast said:
> And certainly kernel-0.01 will not have a command-line interface. A kernel is just that; a core.
does that mean that the 2.4 linux tree will not have a CLI?

i want something small so that i can look at the code and mess around with it.

---

