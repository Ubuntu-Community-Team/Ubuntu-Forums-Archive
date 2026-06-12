---
title: "C++ Programming w/ Linux"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by atraeyu on 2007-03-11
I'm a CS student ... I've only programmed in Microsoft's Visual Studio IDE using their compiler & libraries.  I'd like to learn to program without MSVS using a basic text editor & doing some command line compiling. 

The problem is, I have no idea where to start.  Is there a c++ compiler installed w/ Ubuntu by default?  How do I use it?  Are the libraries similar?

Can anyone help get me started and maybe point me to some good references?  Thanks!

---

### Post by jvc26 on 2007-03-11
I'd advise looking at the programming talk section in the forum it has loads of useful likes for learning all kinds of languages C++ included.
```

sudo apt-get install build-essential

```
Installs the c++ compiler I believe.
Il

---

### Post by blanky on 2007-03-11
You then use it like:

```
g++ myfile.cpp -o myoutputfile
```

Though, that's a very basic example. For more elaborate projects with multiple source files you might want to learn how to write and use Makefiles, or use an IDE such as KDevelop or Anjuta that have project files (*Which can also use the auto tools which automatically create the Makefiles and whatnot for you*).

---

### Post by Vajra Vrtti on 2007-03-11
Ubuntu has the GNU C++ compiler installed (Synaptic package g++-4.1).

This are the GNU C++ libraries:
[http://directory.fsf.org/libs/cpp/](http://directory.fsf.org/libs/cpp/)

You can find examples of command line compiling here:
[http://www.stat.uchicago.edu/~gosset/Compdocs/gcc.html](http://www.stat.uchicago.edu/~gosset/Compdocs/gcc.html)

You may also find this useful:
[http://www.cppreference.com/](http://www.cppreference.com/)

---

### Post by dhughes on 2007-03-11
Anjuta seems to be the most popular IDE as far as I can tell.

 Install it with Synaptic.

---

### Post by Ergo on 2007-03-11
If you have played around with Microsofts .NET framework, you might find KDevelop useful.

[http://ubuntuforums.org/showthread.php?t=273088&highlight=kdevelop](http://ubuntuforums.org/showthread.php?t=273088&highlight=kdevelop)

---

