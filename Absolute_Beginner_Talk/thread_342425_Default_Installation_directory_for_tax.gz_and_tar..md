---
title: "Default Installation directory for tax.gz and tar.bz2 files"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by Souljah on 2007-01-20
Hey guys,

Well I've gotten pretty proficient with ubuntu.I managed to get some advanced editing done. Now I want to know, by default when I install packages from synaptic, it shows up in my applications menu by default and I assume it gets installed the way it's suppose to.

However, if I download a file from the internet, ending in a tar.gz or tar.bz2 extension, into which folder do I extract/install the file, package? By default. I want it to show up in my applications menu by default as well, I also created a link to an application but it wouldn't launch unless I launched it directly from the folder. It's VLC. Anyway, what is the default installation directory?

Thanks,
Ryan

---

### Post by po0f on 2007-01-20
Souljah,

For custom-compiled software you want available system-wide, /usr/local should be the directory you use.  /usr/local/src for compiling, stuff installed will go in the appropriate /usr/local/lib, /usr/local/bin, /usr/local/man when you `sudo make install`...  You get the idea.  :)

If this is a single user system, you could just create a ~/src directory where you can have all the programs' source code available to you that you have compiled.  I really don't recommend compiling something, installing it, then deleting the program source directory.

As far as programs showing up in the Applications menu by default, it's up to the program author.  I believe GNOME's menu handles *.desktop files for adding stuff to the menu, but I don't recall what directory they go under (probably somewhere under /usr/share).  With custom-compiled software, it's more likely that you'll have to manually add an entry for it.

HTH.

---

### Post by Souljah on 2007-01-20
I have some good experience now in compiling and installating software. The basic commands are ./configure, make, make install, make clean. Thanks for the info, I will now have to install it like this:

[code]sudo tar -xzvf somepackage.tar.gz[/code

Now by default, I'm in my home directory, by using the above command, can I specifiy on the same line itself to extract to a specified directory? Or do I have to CD to that directory.

---

### Post by po0f on 2007-01-20
Souljah,

You mean to extract a tarball to /usr/local/src?
```
[FONT="Courier New"]$ sudo tar xv(z,j)f sometarball.tar.(gz,bz2) -C /usr/local/src[/FONT]
```

z corresponds to *.gz, j to *.bz2.

---

### Post by Sef on 2007-01-20
Read [Psychocat's installing software]("http://www.psychocats.net/ubuntu/installingsoftware").

---

### Post by Souljah on 2007-01-20
> **po0f said:**
> Souljah,

You mean to extract a tarball to /usr/local/src?
```
[FONT="Courier New"]$ sudo tar xv(z,j)f sometarball.tar.(gz,bz2) -C /usr/local/src[/FONT]
```

z corresponds to *.gz, j to *.bz2.

Thanks. Also thanks for the psychocats link. Yeah I think the -C option allows you to extract.

---

