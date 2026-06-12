---
title: "Need Help with GBDK compiler for gameboy installation"
date: 2013-04-17
forum: Any Other OS
---

### Post by Zowskaz on 2013-04-17
Hi, I currently have been trying to install GBDK in linux mint. I'm a sort of a beginner and I can't figure out how to install it. I've read the insturctions inside the README and the website but they're kind of vauge.
Any help would be highly appreciated. (GBDK is a C compiler for the gameboy and gameboy color)

---

### Post by Perfect Storm on 2013-04-18
Moved to Other OS/Distro Support.

---

### Post by MadmanRB on 2013-04-18
Why complile when there are plenty of emulators with binaries?
Unless you want to make your own gameboy games or something

---

### Post by Zowskaz on 2013-04-18
That's the whole reason I'm trying to install a gameboy game compiler, so I can make games for the gameboy.

---

### Post by steeldriver on 2013-04-18
Well.

You don't provide much info, but the only GBDK I can find is this one --> [http://sourceforge.net/projects/gbdk/files/](http://sourceforge.net/projects/gbdk/files/) <-- which is **over 10 years old**, however fwiw I was able to unzip and make the examples as instructed in the README in a Mint VM

```
* Extract the archive somewhere (normally /opt/gbdk)
* Set GBDKDIR to where you installed with a trailing /
    e.g. export GBDKDIR=/home/michaelh/gbdk/
* Try compiling the examples as above

```

Is that what you want to do - if so where exactly are you getting stuck?

---

### Post by Zowskaz on 2013-04-18
I know it's 10 years old which is a pain. But it's the only C compiler for gameboy. So far I have tried unpacking the file, then cd'ing into the folder in the terminal and running the "make" and "make install" commands. But it gives me an error when I try to do these commands. I really suck when it comes to using terminal and I have not famillier or comfortable with compilers that you run through the terminal.

Just to clarify what I want to do. I want to install and setup the compiler so I can write programs in C for the gameboy. I heard that the GBDK is based of off lcc. In the end your supposed to be able to run a command in a terminal that compiles your source code.

---

### Post by steeldriver on 2013-04-18
```

steeldriver@mint-vm ~ $ tar xzf Downloads/gbdk-2.96a-i586-pc-linux2.2.tar.gz -C $HOME
steeldriver@mint-vm ~ $ export GBDKDIR=$HOME/gbdk/
steeldriver@mint-vm ~ $ cd ~/gbdk/examples/gb
steeldriver@mint-vm ~/gbdk/examples/gb $ make

```

The 'make' command should produce the following output in your terminal:

```
../../bin/lcc -Wa-l -Wl-m -Wl-j -c -o galaxy.o galaxy.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -o galaxy.gb galaxy.o
../../bin/lcc -Wa-l -Wl-m -Wl-j -c -o space.o space.s
../../bin/lcc -Wa-l -Wl-m -Wl-j -o space.gb space.o
../../bin/lcc -Wa-l -Wl-m -Wl-j -c -o paint.o paint.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -o paint.gb paint.o
../../bin/lcc -Wa-l -Wl-m -Wl-j -c -o rpn.o rpn.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -o rpn.gb rpn.o
../../bin/lcc -Wa-l -Wl-m -Wl-j -c -o rand.o rand.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -o rand.gb rand.o
../../bin/lcc -Wa-l -Wl-m -Wl-j -c -o comm.o comm.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -o comm.gb comm.o
../../bin/lcc -Wa-l -Wl-m -Wl-j -c -o irq.o irq.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -o irq.gb irq.o
../../bin/lcc -Wa-l -Wl-m -Wl-j -c -o filltest.o filltest.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -o filltest.gb filltest.o
../../bin/lcc -Wa-l -Wl-m -Wl-j -c -o ram_fn.o ram_fn.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -Wl-g_inc_ram=0xD000 -Wl-g_inc_hiram=0xFFA0 -o ram_fn.gb ram_fn.o
../../bin/lcc -Wa-l -Wl-m -Wl-j -c -o fonts.o fonts.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -o fonts.gb fonts.o
../../bin/lcc -Wa-l -Wl-m -Wl-j -c -o samptest.o samptest.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -o samptest.gb samptest.o
../../bin/lcc -Wa-l -Wl-m -Wl-j -c -o banks.o banks.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -Wf-ba0 -c -o bank_0.o bank_0.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -Wf-bo1 -Wf-ba1 -c -o bank_1.o bank_1.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -Wf-bo2 -Wf-ba2 -c -o bank_2.o bank_2.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -Wf-bo3 -Wf-ba3 -c -o bank_3.o bank_3.c
../../bin/lcc -Wa-l -Wl-m -Wl-j -Wl-yt2 -Wl-yo4 -Wl-ya4 -o banks.gb banks.o bank_0.o bank_1.o bank_2.o bank_3.o
rm filltest.o comm.o rand.o rpn.o samptest.o paint.o space.o fonts.o irq.o galaxy.o
```

Hope this gets you started

---

### Post by Zowskaz on 2013-04-19
steeldriver@mint-vm ~ $ tar xzf Downloads/gbdk-2.96a-i586-pc-linux2.2.tar.gz -C $HOMEsteeldriver@mint-vm ~ $ export GBDKDIR=$HOME/gbdk/steeldriver@mint-vm ~ $ cd ~/gbdk/examples/gbsteeldriver@mint-vm ~/gbdk/examples/gb $ make 

Is where I get stuck, sorry I'm a complete newcomer when it comes to terminal commands. Could you explain that a little bit so I know what to do?

---

