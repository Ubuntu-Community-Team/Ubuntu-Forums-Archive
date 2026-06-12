---
title: "torcs"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by pedrom169 on 2008-01-27
i wanted to try out torcs game for linux
looks like a great game
im new to linux and need a new challenge from windows

to install i read this

```
For Linux and FreeBSD from "all-in-one" Source Package

   1. Check the dependencies
   2. Download the source package torcs-1.3.0.tar.bz2.
   3. Unpack the package with "tar xfvj torcs-1.3.0.tar.bz2".
   4. Run the following commands:

      $ cd torcs-1.3.0
      $ ./configure        # --prefix="target dir", --enable-debug or --disable-xrandr might be of interest
      $ make
      $ make install
      $ make datainstall

      Default installation directories:
          * /usr/local/bin - TORCS command (directory should be in your PATH)
          * /usr/local/lib/torcs - TORCS dynamic libs (directory MUST be in your LD_LIBRARY_PATH if you don't use the torcs shell)
          * /usr/local/share/games/torcs - TORCS data files

   5. Run the "torcs" command (default location is /usr/local/bin/torcs), you can use those command line options.
      All the configuration data, race results and players options will be saved below the $HOME/.torcs directory.

```

could someone help me install it?

cheers

Peter

---

### Post by Ub1476 on 2008-01-27
See if it's available in Add/Remove. If it's not there, extract the file so you get a folder, open the terminal and type:

```
cd NAMEOFTHEFOLDER
```

If the folder is called "torcs" it would be:

```
cd torcs
```

And just copy/paste the instructions with a $ in front of it in instructions.

If any errors, make sure you have the required [dependencies]("http://torcs.sourceforge.net/index.php?name=Sections&op=viewarticle&artid=3#dependencies").

---

### Post by oldos2er on 2008-01-27
Type  "sudo aptitude install torcs" in a terminal.

---

### Post by pedrom169 on 2008-01-27
> **oldos2er said:**
> Type  "sudo aptitude install torcs" in a terminal.

thanks that is working perfectly

---

