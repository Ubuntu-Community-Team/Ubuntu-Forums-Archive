---
title: "Compiling software"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by deuchar1 on 2007-03-30
Hi guys,

Ok this has probably been answered a gajillion times on here but I'm not having much luck and I partly know what my problem is.

I have a few games (FreeDroidRPG/BOS Wars) that I have downloaded as .tar.gz files.

I am running Ubuntu 6.10 and know I need to compile them before I can play them. 

However, when I follow instructions the "make" command fails - and I am led to believe I am missing the build constructor stuff. (Technical name for it :P). What will I need, and can I get it through Add/Remove or Synaptic?

Once that's out the way, what do I need to do to compile. And what will compiling do? Make a .deb file that I can run to install? Or just make the game playable in its extracted folder?

Thanks,
G

---

### Post by trent dillman on 2007-03-30
sudo apt-get install build-essential

---

### Post by Arby on 2007-03-30
you need to install the package build-essential. You can do this through synaptic or from the command line with ```
sudo aptitude install build-essential
```
Once you have that installed then the usual way to compile software is like this at the commandline. ```
tar -xzvf package.tar.gz
cd package
./configure
make
sudo make install
```

With a bit of luck that should be enough. If that doesn't work out and you start getting errors after running make it probably means you are missing some libraries. Do a bit of googling to see which library provides whatever is missing. If you are compiling stuff you frequently need the development libraries instead of the runtime ones. These are usually labelled library-dev in synaptic.

Once you have compiled the program that's it. It's installed on your system  and ready to go. Some programs create their own entries in the main applications menu, some don't. In which case you'll need to find out where it was installed to and make one. This info should be in the documentation that comes with the program. If you can't find it then /usr/bin or /usr/local/bin are good places to start looking for the executable you just compiled.

Hope that helps.

Arby

---

### Post by deuchar1 on 2007-03-30
Thank you!  I'll give it a whirl over the weekend.
How do packages end up in Synaptic? Does someone package the compiled program and submit it to someone who places it in a repository? Just a curiosity question - not planning on trying that! One step at a time :)

---

### Post by BarfBag on 2007-03-30
> **deuchar1 said:**
> Does someone package the compiled program and submit it to someone who places it in a repository?

That is correct.

Here's a tip.  When you compile something, it's usually pretty hard to get rid of it.  I recommend installing checkinstall.  It adds the .deb it builds to Synaptic, so you can easily uninstall the package.

> sudo apt-get install checkinstall

That command will install it.  To use it, just replace "sudo make install" with "sudo checkinstall" (no quotes, of course).

---

### Post by sirkism on 2007-03-30
So if you install packages and just drag and drop the folder from the desktop to say the bin folder, does the package handlers know these? or will I have to manually remove these programs if i wanted them off the system?

---

### Post by Arby on 2007-03-30
> **BarfBag said:**
> That is correct.

Here's a tip.  When you compile something, it's usually pretty hard to get rid of it.  I recommend installing checkinstall.  It adds the .deb it builds to Synaptic, so you can easily uninstall the package.



That command will install it.  To use it, just replace "sudo make install" with "sudo checkinstall" (no quotes, of course).
 Not come across that before. Handy.

---

### Post by deuchar1 on 2007-04-01
Ok when I run ./config it runs ok but with the following at the end.....

checking for X... no
configure: Checking for compulsory SDL libraries:
checking for sdl-config... no
checking for SDL - version >= 1.2.3... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.3 not found!

Then when I run sudo checkinstall it seems to run ok but once I've gone through all the setting description/licence type steps it exits fine but nothing seems to happen.

Make and Sudo make install throw up errors about sdl-config and SDL-1.2.3 missing. Where will I get all the necessary stuff for these?

---

### Post by Arby on 2007-04-01
This would be one of those missing libraries that I mentioned earlier. It looks like you're missing the SDL development libraries. Having looked in the repositories my best guess is that you need libsdl1.2-dev. You can install this using Synaptic or with the following command in a terminal. ```
sudo apt-get install libsdl1.2-dev
``` try installing that package and then running everything from ./configure onwards again.

---

