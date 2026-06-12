---
title: "No Java and NO flash"
date: 2006-06-07
forum: Apple PPC Users
---

### Post by jakestah7 on 2006-06-07
-on breezy-

I installed Ubuntu(breezy) on an old Imac G3 333 mh cpu 128mb ram and 6 gig HD

I have tried to install java and flash through easyubuntu and then through automatix code. (I am new to this so . . . ). It will not work. I just recently reinstalled the OS because I junked it up with a lot of stuff. Can anyone help me, I will monitor this thread (so that I can answer questions smart people ask me about the problem).
I read somewhere that flash particularly doesn't work on powerpc's.

P.S.
I need advice, should I upgrade to dapper or will this make it slower(it is already a little on the slow side). Also, will this improve compatibility?

---

### Post by davygravy on 2006-06-07
I installed GIJ for java (can be done through Synaptic).

For flash content, I compiled and installed Gnash.  

I just used Synaptic to make sure I had automake 1.9 installed (and removed all lower versions of automake). then I wen to the gnash website and downloaded the tarball. extracted to desktop. in a terminal, cd the directory (folder) of the source. then I used Engla's suggestion of

./configure --enable-mp3 --enable-png --enable-jpeg

This did not work at first. But the error messages gave a clear picture of what dev packages and other stuff (some libs, IIRC) I still had to install.

Once the command listed above completed w/ no errors, I just did

make

and then

sudo make install

Sound doesn't work in the browswer plugin (at least it didn't for me). I haven't tried it as a standalone yet.

Good luck.

---

### Post by Rxke on 2006-06-08
Upgrading to Dapper might make stuff faster, actually.

---

### Post by kellogs on 2006-06-08
The problem with Gnash is that if you dont have opengl enabled for whatever reason, firefox plugin won't work. And ATM the development of Gnash is oriented to make it less buggy, so no non-accelerated-flash by now. 

The users who wont have acceleration due to lack of support at the Ati, Nvidia or Xorg Side will have to wait.

I tried Gnash, compiled it succesfully, but my Ati9600 have no acceleration under dapper and so it crashed every flash page I throwed it to with Gnash installed.

---

### Post by eidex on 2006-06-08
hi, i still have problems with compiling gnash:

./configure gives me the following errors:

```
ERROR: No GtkGLext development package installed! You need to have the GtkGLext development package installed to build the GTK gui. Try --with-gui=sdl or install** libgtkglext1-dev**  (using apt-get) or gtkglext-devel (using yum).
ERROR: No Gtk2 development package installed!You need to have the Gtk2 development package installedto compile this project or install **libgtk2.0-dev** (using apt-get) or gtk2-devel (using yum).
        Pango flags are: -I/usr/include/pango-1.0
        Pango libs are: -lpango-1.0
        Glib flags are: -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include
        Glib libs are: -lglib-2.0
        Atk flags are: -I/usr/include/atk-1.0
        Atk libs are: -latk-1.0
        Xft flags are: -I/usr/include/X11
        Xft libs are: -lXft
ERROR: No SDL development package installed! You need to have the SDL development package installed to compile, or install **libsdl1.2-dev** (using apt-get) or SDL-devel (using yum).
WARNING: No SDL_Mixer development package installed! You need to have the SDL Mixer development package installed if you wish to have MP3 support for Gnash. To compile this project with SDL sound support, install libsdl-mixer1.2-dev (using apt-get) or SDL_mixer-devel (using yum).
        POSIX Threads flags are: -I/usr/include
        POSIX Threads lib is: -lpthread

```

apt-get refuses installing libgtkglext1-dev, libgtk2.0-dev, libsdl1.2-dev due to dependency errors (e.g. depends on libglu1-mesa-dev which SHOULD (?) not be installed according to apt-get.

a few weeks ago i thought this was a beta issue, but now i am clueless, should i force apt-get to install these packages?

thanks

--

PS: is there a good howto for creating a *.deb after compiling, or is it harmlass in terms of system stability to compile one cvs after the other and install them?

---

### Post by n00bWillingToLearn on 2006-06-08
I had a problem with IBM's java that it just didn't make a link to the right place. If that is your problem too then it is easily fixed.

What is the output of typing

```
java
``` 
and 

```
cd /usr/alternatives
java
```

And I am sorry to say, there is simply no flash for PPC:(

---

### Post by n00bWillingToLearn on 2006-06-08
If you want speed, you could also try xubuntu.

---

### Post by maddog39 on 2006-12-19
I wrote a small guide here:

[http://ubuntuforums.org/showthread.php?p=1900193#post1900193](http://ubuntuforums.org/showthread.php?p=1900193#post1900193)

On compiling gnash 0.7.2 on ubuntu. Try it, it should work.

---

