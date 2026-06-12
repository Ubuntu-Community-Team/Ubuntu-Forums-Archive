---
title: "The lowdown on tar.gz files"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by Gausian on 2007-07-02
ok, after googling and endless searching i thought maybe someone here could help me.

what is the proper procedure for unpacking and installing tar.gz files?

```
tar -xzvf <file> or tar -xjvf <file>

cd <place>

<read readme> ./configure

make

make install

make clean
```

Are these the standard steps for tarballs?  It seems that the same can be achieved with several different commands.  What are the differences in the different commands?

---

### Post by overdrank on 2007-07-02
> **Gausian said:**
> ok, after googling and endless searching i thought maybe someone here could help me.

what is the proper procedure for unpacking and installing tar.gz files?

```
tar -xzvf <file> or tar -xjvf <file>

cd <place>

<read readme> ./configure

make

make install

make clean
```

Are these the standard steps for tarballs?  It seems that the same can be achieved with several different commands.  What are the differences in the different commands?

Hi maybe this link will help you
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
Good luck!

---

### Post by Cypher on 2007-07-02
I think an explanation of the options to TAR will make things clear.

"X" = Extract
"v" = Verbose
"f" = Filename
"z" = GZip
"j" = BZ2

As you've done, you can group these arguments together. If you were trying to extract the contents of a .tar.gz or .tgz file, then you'd use the "z" argument with "xvf", if you had a .tar.bz2 then you'd use "j" with "xvf". 

You can also replace the "x" with a "t" to just list the contents fo the archive to see what kind of directory structure it has or if a file you're looking for is inside it.

The <place> is usually whatever directory root is contained with the tarball.

The "./configure" program will query your system for library depdencies and other programs and create a Makefile uniquely suited for your computer.

The "make; sudo make install" commands will make the program and install the resulting binary, usually in /usr/local/bin. Some programs also include a "sudo make uninstall" to safely remove the installed binaries, but not all programs do. The "make clean" is just to clean out the build files in the local directory.

Instead of doing "sudo make install", I've used "sudo checkinstall". Checkinstall is a program that essentially does the "make install" call, but creates a .DEB file from the result and installs that instead. It is now much easier to remove the .DEB file rather than inidividual files.

People have suggested that they've had issues with Checkinstall, but I haven't had any..

---

### Post by vanadium on 2007-07-02
man tar is your friend: it explains the myriad of options. z is for a gzip compressed tarball, -j for a bzip2 compressed tarball (these are two different compression algorithms, bzip2 more powerfull and newer than gzip, but perhaps also a bit slower)

---

### Post by Gausian on 2007-07-02
things are beginning to become clearer now.....thanks for the explanations :)

---

### Post by cogadh on 2007-07-02
A .tar.gz file is just a compressed archive, like a .zip file in Windows. The procedure for using the contents of that file is different depending on what those contents are. For example, if it contains source code that needs to be compiled before you can use it, the different configure and make commands you list are usually required. However, if it contains a precompiled binary, there is usually just an install script of some kind contained in it that you will need to run. The page overdrank supplied will defintely help you with source code compiling (I'll have to bookmark that one), if your .tar.gz contains a pre-compiled binary, you should verify the install procedure with the site you got it from.

---

### Post by Enverex on 2007-07-02
A GZipped Tarball has nothing to do with software source. You don't install them. It's basically a Linux archive file like Zip or RAR is in Windows.

---

### Post by samuraiCat on 2007-07-02
And from what I've read, all these should be downloaded and unpacked in the /home directory, not in your username's directory or the Desktop.

Correct?

---

### Post by Cypher on 2007-07-02
> **samuraiCat said:**
> And from what I've read, all these should be downloaded and unpacked in the /home directory, not in your username's directory or the Desktop.

Correct?

Nope, you should be unpacking these files into some direcotry in your home directory..i.e., /home/<username>/software or something..

---

### Post by Raineer on 2007-07-02
> **Cypher said:**
> Nope, you should be unpacking these files into some direcotry in your home directory..i.e., /home/<username>/software or something..

Agreed, I have a directory just for unpacking stuff and installing it.

If you put it in /home then it would require root access as well.

sudo should not be required on ANY of those steps until you get to "make install", that's the only time it touches an outside part of your system.

---

### Post by Rui Pais on 2007-07-02
And btw those command assume that you are installing a C or C++ source code with a make file.

Could be a plain source code, python or other language code or even a shell script.

The fundamental is search for an INSTALL or a README and... well read it ;) 
Usually says waht must be done to install :)

---

