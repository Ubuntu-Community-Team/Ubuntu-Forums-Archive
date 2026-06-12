---
title: "compiling programs"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by flash2lightning on 2006-12-09
i need help compiling tar.gz files. 
i use checkinstall, but when i type *make* into the terminal, it says [I]make: *** No rule to make target `install'.  Stop.
[/I]
what else do i need to type in?

---

### Post by public_void on 2006-12-09
If you haven't done so already, check the program your compiling isn't in the repos. It so much easier using synaptic to install. Otherwise it should be:
```
tar -xvzf foo.tar.gz
cd foo
./configure
make
sudo checkinstall
```
It sounds if you haven't run ./configure. This will check dependencies, if it fails it will tell you in the last couple of lines. These dependencies will have to be resolved for the program to be installed.

---

### Post by camilluk on 2006-12-11
And what if the file is a filename.run (presumably a script)? I tried to just click on it, but instead of installing something it gets opened by a text editor and it accomplishes nothing. How do you tell Linux to actually run the script?

Also, in some cases I noticed that the 'make' command fails, as it does not find a 'makefile' or something like that. I'll be more specific at the next opportunity by editing this post with the actual error message. These programs actually come from a popular linux magazine's dvd, so they're supposed to be working (except for dependencies issues of course)...

---

### Post by taurus on 2006-12-11
```
chmod 755 filename.run 
./filename.run 
-or-
sudo ./filename.run
```

---

