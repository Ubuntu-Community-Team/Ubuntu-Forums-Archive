---
title: "Installing drivers for Nostromo N52?"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Knightsky on 2007-09-20
Hello again everyone.

I have another question, this time concerning the drivers I found on [http://sourceforge.net/projects/nostromodriver/](http://sourceforge.net/projects/nostromodriver/) - designed for use with the Nostromo N50-N52 Speedpads.

I downloaded the two .tar.gz files on their website, and tried to run them, but couldn't figure out what to do once I'd downloaded the FTLC (I think that's the name...not at my home computer at the moment) compiler. Is there one that's precompiled out there in the internet's depths that I've missed (would make my life much easier...) or can someone walk me through how to install this specific piece of software?

---

### Post by Maestro23 on 2007-09-20
> **Knightsky said:**
> Hello again everyone.

I have another question, this time concerning the drivers I found on [http://sourceforge.net/projects/nostromodriver/](http://sourceforge.net/projects/nostromodriver/) - designed for use with the Nostromo N50-N52 Speedpads.

I downloaded the two .tar.gz files on their website, and tried to run them, but couldn't figure out what to do once I'd downloaded the FTLC (I think that's the name...not at my home computer at the moment) compiler. Is there one that's precompiled out there in the internet's depths that I've missed (would make my life much easier...) or can someone walk me through how to install this specific piece of software?

From the nostromo.html doc inside the extracted folder:

> Installation:

# just type these commands right into the shell.
# make a shell script out of this, if you wanna go crazy.
# you can run either the plain, silent version (nostromo)
#  or the opengl version with 3d display(glnostromo).
##########################################################
su
modprobe evdev
chmod a+rw /dev/input/event1

tar xvfz nostromo_driver-0.1.3.tar.gz
cd nostromo

make
    - or -
make gl
    - or -
make algl




Also, you will need to install "build-essential" from the Ubuntu repos.  Check this section out in the Feisty Starter's Guide "Compiling from source": [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_a_program_from_source_code](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_a_program_from_source_code)

---

### Post by Knightsky on 2007-09-20
> **Maestro23 said:**
> From the nostromo.html doc inside the extracted folder:



Also, you will need to install "build-essential" from the Ubuntu repos.  Check this section out in the Feisty Starter's Guide "Compiling from source": [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_a_program_from_source_code](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_compile_a_program_from_source_code)

I did the first part...typing make in a terminal wasn't so hard to do. The second part is good information though. I'll definitely read up on that. Thank you.

---

### Post by Knightsky on 2007-09-21
ok, so I got the first file working, (I used make and make install in su and that worked) but the one marked nostromo_n50-1.3 gives me the following error during ./configure

checking pkg-config is at least version 0.9.0... yes
checking for NOSTROMO_CFLAGS... 
checking for NOSTROMO_LIBS... 
configure: error: Package requirements (gtk+-2.0 libxml-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the NOSTROMO_CFLAGS and NOSTROMO_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.

I looked for them both, but I couldn't find either in Add/Remove Applications or in Synaptic. Closest I got was a 'theme engine' for xfce, and just in case, I've installed that. But that one is apparently not what I need, because the error still persists.

---

### Post by MrHippocampus on 2007-09-21
Installing libgtk2.0-dev and libxml2-dev from synaptic/apt should solve those dependancy problems.

---

### Post by Knightsky on 2007-09-21
Aha, ok, thank you. I'll install those when I get home tonight.

---

