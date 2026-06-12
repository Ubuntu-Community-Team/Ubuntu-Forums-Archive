---
title: "Please help with alsa update"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by Autumn_Glitch on 2007-12-23
I'm on a Toshiba satellite laptop running Ubuntu studio 7.10 and have yet to be able to get my computer to make any sound what so ever. I also do not even get a volume control window. When I click on the volume control icon once I get a

 ***"the volume control did not find any elements and/or devices to control. this means either that you don't have the right gstreamer plug ins installed or you don't have a sound card configured"***

 and I'm reasonably sure I have installed the right gstreamer plugins.  From what I can gather from other post on about similar issues its because my current alsa drivers don't support my sound card(intel 82801G (ich7 family) high definition audio controller rev 02). so now I am trying to install the new alsa drivers that supposedly support my card using this how to thingy

* [I][B][http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel#Setting_up_modprobe_and_kmod_suppor](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel#Setting_up_modprobe_and_kmod_suppor) *
[/B][/I]
 but when I get to this step

**[B]* "./configure --with-cards=hda-intel --with-sequencer=yes ; make ; make install"***[/B]

 I get this back from the terminal

[I] "tumn@ubuntunavi3:/usr/src/alsa/alsa-driver-1.0.15$ 
./configure --with-cards=hda-intel --with-sequencer=yes ; make ; make install
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.15
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... 
[B]checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15'

Please, run the configure script as first...

if [ -L /include/sound ]; then \
                rm -f /include/sound; \
                ln -sf /usr/src/alsa/alsa-driver-1.0.15/include/sound /include/sound; \
        else \
                rm -rf /include/sound; \
                install -d -m 755 -g root -o root /include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /include/sound; \
                done \
        fi
install: cannot create directory `/include': Permission denied
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1[/B]"[/I]

 So I googled linux/version.h just to see if i would get lucky and came up with a page that said to do this 

[B] [I]"If you get an "linux/version.h no such file or directory" message when compiling the driver, you either have not installed the kernel source code, or you haven't run

	cd /usr/src/linux; make include/linux/version.h"
[/I][/B]
 and doing that gives me this error message in the terminal 

[I]"autumn@ubuntunavi3:/usr/src/alsa/alsa-driver-1.0.15$ cd /usr/linux; make include linux.version.h
[B]bash: cd: /usr/linux: No such file or directory
make: Nothing to be done for `include'.
make: *** No rule to make target `Linux.version.h'.  Stop.[/B]"
[/I]
 I admit I don't know what I'm doing and I apologize but  if some one could even point me in the direction that i need to be going or tell me if Im wasting my time with installing new alsa drivers to get my sound to work that would be awesome ^_^.

---

### Post by adam.tropics on 2007-12-23
from terminal

```
 sudo apt-get install linux-source
```

then have another go!

---

### Post by High Camp on 2007-12-23
Hi There

Unfortunately I can't be of any help but I know the most recent Ubuntu (7.10) has problems with Toshiba sound cards. My girlfriends lapy won't play sound any more. If it's an option and sound is important I would recommend running a livecd of 7.6 (or whatever Edgy was) and see if that will play sound. I bet it will and then you can just install that version and you'll be good to go. If you must have the latest version, do what I'm doing with the other laptop and wait for it to be fixed. I have found some long winded solutions on the forums here but I'm too lazy and it's not high priority.

Hope that helps somewhat,

---

### Post by Autumn_Glitch on 2007-12-23
> **adam.tropics said:**
> from terminal

```
 sudo apt-get install linux-source
```

then have another go!

Thanks so much for helping. ok so i got the linux source file unpacked it to the correct directory did 

***cd /usr/src/linux; make include/linux/version.h  ***
then I did
*** ./configure --with-cards=hda-intel --with-sequencer=yes ; make ; make install***
and got a new error. the exact same error as before only instead of me not having 
***linux/version.h***
i didn't have
_**/linux/autoconf.h**_
so i made the file (took a few steps i cant remember the exact code and my terminal will not scroll up that far.) and eventually did 
***./configure --with-cards=hda-intel --with-sequencer=yes ; make ; make install***
again and now I'm getting this error
[I][B]checking for which soundcards to compile driver for... configure: error: Unsupported soundcard hda-intel
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.15'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.15'[/B][/I]
lol.

---

