---
title: "Installing Programs on Ubuntu"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by Jesus_Christ on 2006-06-30
I'm reasonably new to Ubuntu, and I'm having trouble understanding how to install downloaded programs. I download them in the form of the .tar.gz file format, but I have no idea where to go from there.

Any help would be appreciated.

---

### Post by vayde on 2006-06-30
If you un-tar the archive file, there should be a 'readme' in there somewhere which will give you instructions on what to do.  It will probably go so far as to tell exactly what to type on the command line.

Depending on what you are installing, you might need to install things like the gcc compiler first.  To do that, type the following from a command line:

sudo apt-get install build-essential

That will give you the necessary tools to follow most install procedures.

Hope that helps!

---

### Post by deanjm1963 on 2006-06-30
just what programs are you trying to install? if you've set up your repositories correctly, there's VERY little if ANYTHING you need to download and install manually. A little more information might help.

---

### Post by oyvindaa on 2006-06-30
Then you can right click on the downloaded file and then "unpack here". In the folder which gets created there will most likely be a README or INSTALL file. Open it/them and read their instructions. (Open the files by just double-clicking on them should open them in a text editor). 

The usual ways of installing programs are:

```

./configure

```

```

make

```

```

make install

```

This must be done in a terminal.

Hope this clears things up.

---

### Post by Nikusan on 2006-06-30
Read the link in my sig

---

### Post by psb6m on 2006-06-30
Normally you install a program by using Synaptic (System --> Administration --> Synaptic Package Manager) to download it from one of the Ubuntu repositories. So the first thing to do is see if your program is available that way. (Rummage around in Settings --> Repositories to enable some repositories that are not there by default.) Programs from the repositories are pretty much guaranteed to work, and to be configured in such a way as to be most compatible with your system. Synaptic will also take care of downloading any dependent packages.

If the program you want is not available in one of the repositories, or you need the latest bleeding-edge version, then you can get the tar.gz version. This is usually program source code, which you must compile. Normally you do this by opening a terminal window and unarchiving the file:

$ tar -xzvf myprog.tar.gz

This should create a directory "myprog"; change to it:

$ cd myprog

Then, probably, you will issue the three almost-universal commands for compiling and installing a program in Linux:

$ ./configure
$ make
$ sudo make install

The "configure" step will probably complain about missing header files, and you'll have to use Synaptic to install "devel" packages containing the headers you need. It can be quite a tangle. Best stay away from source code for now and use Synaptic if your program is there.

---

