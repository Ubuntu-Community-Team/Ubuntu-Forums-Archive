---
title: "Compiling Software"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by nkingcade on 2007-11-17
I enjoy compiling my own applications. However, my system is becoming a mess. So, my question is:

1. Where should I keep the tarballs once I download?

2. Once I extract, where should I extract too?

3. Normally, where do the finished applications reside?

I am simply trying to put some organization around my new found compiling business. thanks in advance.

---

### Post by taurus on 2007-11-17
1.  The default directory is ~/Desktop so anywhere is fine as long as you have permission to write to it.

2.  Same as where you have saved it.

3.  usually in /usr/local/bin unless you specify somewhere else during the ./configure.

```
./configure --PREFIX=/usr
-or-
./configure --help <-- for more options
```

---

### Post by meatpan on 2007-11-17
There is no 'correct' location for installing these programs, but /usr/local is a good location because it implies the installation is specific to your machine (rather than an os distribution).  Personally,  I prefer to install third-party-software in /opt.  I follow this procedure:

1.  Create a directory under /opt for the basic, non-versioned, package name
2.  Make a BUILD directory and the versioned package name directory under #1.
3.  Extract tar file to BUILD
4. configure/make/make install, with --prefix= #2 above
5. Create a softlink named 'default' under #1, pointing to #2.  This makes shell path config a bit easier, and nicely displays parallel build flavors and versions of the software.

Package src is stored in BUILD (sometimes this is a direct CVS repos), and various builds are listed under the main package name.

---

### Post by nkingcade on 2007-11-17
I'm not sure I understand your instructions. Here is a screenshot of what I have done so far:

neal@Bubba:/opt$ sudo mkdir ettercap-NG-0.7.3
neal@Bubba:/opt$ cd ettercap-NG-0.7.3
neal@Bubba:/opt/ettercap-NG-0.7.3$ mkdir BUILD
mkdir: cannot create directory `BUILD': Permission denied
neal@Bubba:/opt/ettercap-NG-0.7.3$ sudo mkdir BUILD
neal@Bubba:/opt/ettercap-NG-0.7.3$ cd BUILD
neal@Bubba:/opt/ettercap-NG-0.7.3/BUILD$ 

Can you help me understand the configure prefix?

---

### Post by taurus on 2007-11-17
Is there anything in that directory because you just created by hand?

```
ls -la /opt/ettercap-NG-0.7.3
```

And by the way, "mkdir BUILD" is not going to work since you can't write or create in /opt!  Make your life a little easier, stay in your $HOME directory until you want to actually install it to your system, then include the **sudo** in front of the command.

---

