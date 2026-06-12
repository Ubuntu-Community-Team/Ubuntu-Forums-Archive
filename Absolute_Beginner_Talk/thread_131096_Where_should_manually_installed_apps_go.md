---
title: "Where should manually installed apps go?"
date: 2006-02-15
forum: Absolute Beginner Talk
---

### Post by transistor on 2006-02-15
I'm installing Zoneminder ([http://zoneminder.com](http://zoneminder.com)) security system. There isn't an apt-get for it so I have to do it manually.

Where should I untar the files to? i.e. What's the Ubuntu equivelant of "C:\Program Files" in another well known OS?

In the case of ZM it should be accessible by all users.

---

### Post by oakz on 2006-02-15
you can put it wherever you want, a common place to put third party packages is in /opt. If you build the program from source it is typically installed in /usr/local/

---

### Post by rfruth on 2006-02-15
There are several ways to organize things, I'd create a new folder called security2 (whatever) do the other users log in as you or do they have there own unique login ?

---

### Post by engla on 2006-02-15
Most of my custom stuff seems to be put in /usr/local. I installed all my loki games at ~/games though.

---

### Post by taurus on 2006-02-15
If you put the binary in /usr/local/bin, library in /usr/local/lib, and share in /usr/local/share, then it's in path so you can run it from any place...  Most of the programs (but not all) that you have to build from source with ./configure && make && make install commands will install things in those directories for you.

---

### Post by Jucato on 2006-02-16
Ok, let me just get this straight. For example I download the source code of a program, untar it in a folder in my home directory(~/program), then run ./configure && make && make install. It will put the necessary files in those directories that you mentioned right? 

So will it be safe to delete the directory I just made, the ~/program? I read somewhere (forgot where) that you should keep that folder so that you could run "make uninstall" later. Is this the right way to do it?

---

### Post by steve.horsley on 2006-02-16
If it installs outside of your home directory (which is likely), you probably want to run **sudo make install **or you won't have the access privilege to write.

As for keeping the make directory, I look forward to seeing a good answer. I would think that you would be OK just keeping the source tarball.

---

