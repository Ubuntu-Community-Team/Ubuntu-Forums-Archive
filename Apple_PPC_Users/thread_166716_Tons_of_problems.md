---
title: "Tons of problems"
date: 2006-04-26
forum: Apple PPC Users
---

### Post by PaulB007 on 2006-04-26
Ok, I got the gstreamer plugin for totem. Said I needed to compile it. I did so, then I got the message configure: error: no acceptable C compiler found in $PATH

I looekd up this error and it said I needed a thing called GCC for a C compiler and stuff. Downloaded that and it has an .rpm extension. Tried opening it and it wouldnt even open, said it was an invalid format or something. 

I cant even compile anything I download, and I cant get the proper C, C++ language compiler. What do I do?

Also I still dont know how to install the codecs for MP3s

---

### Post by gabruo on 2006-04-26
Just use synaptic package manager from your system administration menu to download and install gcc.  For that matter you could use it to install whatever codecs you might need.  If you prefer a terminal install use 'sudo apt-get install build-essential' and you will be ready to go with gcc.

---

### Post by nanotube on 2006-04-27
like gabruo says, your first step when you want to install something should be to fire up the synaptic package manager (available under System>Administration), and search there to see if you can find your software. that's the easiest way to install. (and make sure to enable the universe/multiverse repositories).

only if you cannot find it there should you resort to compiling stuff from source. the gstreamer codecs should all be in the repositories - just search for gstreamer in synaptic, and a bunch of plugins/codecs will come up.

---

### Post by Sef on 2006-04-27
To compile you need build-essential.  It will install everything you need to compile.

From the terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo apt-get install build-essential

---

