---
title: "need help installing cube 2 game on ubuntu"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by Mentalchicken on 2006-09-09
Hi, 
i recently installed ubuntu and im trying to teach my self how to use it.

I downloaded the sauerbraten.tar.gz and extracted it to the desktop

Here is my terminal message

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

interlan@linux1:~$ cd Desktop/sauerbraten
interlan@linux1:~/Desktop/sauerbraten$ ./sauerbraten_unix
./bin_unix/linux_client: error while loading shared libraries: libSDL_image-1.2. so.0: cannot open shared object file: No such file or directory
interlan@linux1:~/Desktop/sauerbraten$

Ok im missing a library? i think? what do i do from here?

Thx in advance

---

### Post by bluevoodoo1 on 2006-09-09
libsdl-image1.2 package maybe?

You can search [http://packages.ubuntu.com](http://packages.ubuntu.com)

[http://packages.ubuntu.com/dapper/libs/libsdl-image1.2](http://packages.ubuntu.com/dapper/libs/libsdl-image1.2)

or use synaptic package manager to search for possible candidates.

Where did you get cube 2??

---

### Post by Mentalchicken on 2006-09-09
How do i install the package if i find it? lol  

i got cube 2 from sauerbraten.org

---

### Post by bluevoodoo1 on 2006-09-09
> **Mentalchicken said:**
> How do i install the package if i find it? lol  

i got cube 2 from sauerbraten.org

Oh whoops. Try this.. [http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by Mentalchicken on 2006-09-09
Well after doing a lil reading from that site, i installed the build-essential that i needed and choose to install it manually, Here is my error after doing ./configure

It went thru alot so i left much out 

------START CODE-------
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for inline... inline
checking for a BSD-compatible install... /usr/bin/install -c
checking for sdl-config... no
checking for SDL - version >= 1.2.4... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.4 not found!
interlan@linux1:~/Desktop/SDL_image-1.2.4$
------END CODE----------

HELP! Im still attemting to install this package, so i can install cube 2

---

### Post by fakie_flip on 2007-04-19
> **Mentalchicken said:**
> Hi, 
i recently installed ubuntu and im trying to teach my self how to use it.

I downloaded the sauerbraten.tar.gz and extracted it to the desktop

Here is my terminal message

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

interlan@linux1:~$ cd Desktop/sauerbraten
interlan@linux1:~/Desktop/sauerbraten$ ./sauerbraten_unix
./bin_unix/linux_client: error while loading shared libraries: libSDL_image-1.2. so.0: cannot open shared object file: No such file or directory
interlan@linux1:~/Desktop/sauerbraten$

Ok im missing a library? i think? what do i do from here?

Thx in advance

Just do this command, and then try to start Sauerbraten again.

sudo apt-get install libsdl-image1.2

If the game still won't start, then do this commands and then try again to start the game again.

sudo apt-get install libsdl-mixer1.2

You don't need build-essential.

---

