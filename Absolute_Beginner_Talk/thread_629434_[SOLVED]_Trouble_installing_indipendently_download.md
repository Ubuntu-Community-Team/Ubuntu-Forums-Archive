---
title: "[SOLVED] Trouble installing indipendently downloaded packages"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by fmbugdadi on 2007-12-02
I have manually downloaded several software packages in tar.gz format, however, I don't know how to install them. I have no problems installing packages through synaptec, but how do you install a package that I manually d/l myself. On synaptec under file menu, I click on "add downloaded packages", the files I want are grayed out, and I can't let click on them. most of the packages I have manually downloaded have had the tar.gz extension. I am sure there are many ways of installing these packages. What is the easiest way?

---

### Post by PmDematagoda on 2007-12-02
You have to compile those packages you downloaded which will require a little more work than using .debs.

If you could post what applications you want to install then we could give you the names of those applications on the repositories so that you can install them using apt-get or Synaptic.

---

### Post by hackle577 on 2007-12-02
[https://help.ubuntu.com/7.10/add-applications/C/install-file.html#tarballs](https://help.ubuntu.com/7.10/add-applications/C/install-file.html#tarballs)

Let me know if that helps! :-)

EDIT: Yes, you should check you Add/Remove Programs list for those programs to see if they are available there. If so, install them that way; they will be updated automatically, whereas they will not if you compile them.

---

### Post by rob1101 on 2007-12-02
first try the methods that were posted above

after you unpack it you can open up the terminal and cd to the directory that you extracted it to then input the following commands

./configure
sudo make
sudo make install

---

### Post by fmbugdadi on 2007-12-02
the file I am trying to install is called "secure delete 3.1" from thz..

---

### Post by hackle577 on 2007-12-02
I'm assuming you meant ["Secure Delete" from THC]("http://freeworld.thc.org/releases.php?q=delete")?

---

### Post by hackle577 on 2007-12-02
Go to System > Administration > Synaptic Package Manager.

When it starts, click the Search button on the top toolbar. Search for "secure-delete". Click the box under the S column, select "Mark for installation", then click the green Apply checkmark to install it.

Enjoy!

---

### Post by fmbugdadi on 2007-12-02
Ok, thanks, I was able to install through synaptec. Can you lead me to some docs? I assume this is a command line program, which is fine with me... thanks....

---

### Post by hackle577 on 2007-12-02
Documentation for Secure Delete is in /usr/share/doc/secure-delete.

The README.Debian there is useless, though. The instructions are in the README.gz archive.

---

### Post by hackle577 on 2007-12-02
I would also advise being ***extremely*** careful with this program, as you could easily wipe data you didn't want erased.

Also, please mark this thread as solved (in Thread Tools menu above your original post).

---

### Post by fmbugdadi on 2007-12-02
ok thanks a million

---

