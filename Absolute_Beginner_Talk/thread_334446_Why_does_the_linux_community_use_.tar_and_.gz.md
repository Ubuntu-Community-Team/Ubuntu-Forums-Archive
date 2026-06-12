---
title: "Why does the linux community use .tar and .gz?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by paul6 on 2007-01-08
My understanding is that these are basically compressed files.... but why not use conventional  file compression like .zip, .rar, and .7z? Is there something special about .tar and .gz?  And why are they often used togethor to make .tar.gz files? I would think good compression software does not need to compress something twice.

Sorry if this post sounds idiotic.

---

### Post by aysiu on 2007-01-08
.tar.gz *is* conventional for Linux.

.zip isn't universally conventional. It's conventional for Windows.

As for compressing twice, I don't believe a .tar file is compressed--just grouped together. the .gz part is the compression. Someone can correct me if I'm wrong on that.

---

### Post by KaeseEs on 2007-01-08
The use of .tar (**T**ape **Ar**chive) and .gz(**G**NU **Z**ip) together  as .tar.gz, or as .tgz, goes back years in Linux and BSD, and other free operating systems.  It's a classic question for newcomers to ask, and typically the first intro a newbie gets to part of the 'UNIX philosophy.  More on that later.

.tar files are archives; a .tar is one file which contains many files, and some data about them (such as file permissions and creation and modification times).  A .gz is a file compressed with the GZip format.  Now, Windows users are used to .zip files, which are compressed archives - a .zip does what a .tar does and what a .gz does.  Why do them separately?  The philosophy of the UNIX operating system, and systems inspired by it (like Linux), is that each program do one thing and do it well, rather than do many things in one but at a lower quality.  This allows for more flexibility; for example, you will also often see .tar.bz2 files, which consist of many files archives with tar and compressed with BZip2.

Note that Linux and BSD systems also have the 'zip' and 'unzip' utilities installed - you can deal with .zip files if you like, it's just not the norm to do so.

---

### Post by tribaal on 2007-01-08
You might also check out [http://en.wikipedia.org/wiki/Tar.gz](http://en.wikipedia.org/wiki/Tar.gz)
:)

Cheers

- trib'

---

### Post by lucky_chouhan on 2007-01-08
Yes linux zip files in .tar  .gz is necessary otherwise how to campare on you download on linux application or windows application.


funny:)

---

### Post by aysiu on 2007-01-08
For the end user it doesn't really matter. I've been on Windows installations where you double-click a .zip file, and Windows has no idea what to do with it. You have to get WinZip or FreeZip or some other program to do it.

Every major Linux distribution comes with File-Roller, Ark, or some other archive manager (and no nagware) to handle .tar.gz files.

Two parts, one parts. Doesn't matter to me, as long as I double-click it and am able to unzip or untar it.

---

### Post by jem7v on 2007-01-08
Part of the reason they were adopted instead of the older ZIP format (and this is me putting together puzzle pieces from Wikipedia and Linus Torvald's autobiography, "Just for Fun") may be that the ZIP archive type is not open-source, whereas .tar.gz and .tar.bz2 are both open-source.  Both formats also allow more compression than a normal zip file.

Furthermore, when ZIP files first hit the scene (~2 years before Torvalds started working on his OS project, which would become Linux) it was amidst heated legal debate between its developer and his previous employers.  .tar.gz appeared about a year after Torvald's first release (Linux 0.01) and, bearing the GNU license, was probably just the more palatable (and more portable) option for an OS that already bore the GNU license.

(But that last bit is just conjecture on my part.)


edit: clarification regarding the post following this one: Yes. .tar is old; gzip (tar.gz) appeared in 1991 though.

---

### Post by dickm35 on 2007-01-08
Well people just a quickie here. I am a retired software engineer and we were using
tarballs ( tar ) back in the late 70's and early 80's with real unix. yes I really am that old
and love Ubuntu.

dickm35

---

### Post by revertex on 2007-02-19
tar(Tape Archiver), has designed to do backups to tape (DAT), it has a better control, is safer , can handle bigger files and is faster. 

You can try yourself, create a big zip file of your root file system( or something bigger), then try extract just one file, do the same with tar and you will see the difference.

zip can handle very well small files, but is a pain to compact several gigs.
tar can handle files of any size.

do you do backups?

---

### Post by steve.horsley on 2007-02-19
> **dickm35 said:**
> Well people just a quickie here. I am a retired software engineer and we were using
tarballs ( tar ) back in the late 70's and early 80's with real unix. yes I really am that old
and love Ubuntu.

dickm35

Yup. The question is backwards - Why don't windows users use conventional file comnpression instead of reinventing the wheel?

---

### Post by nonewmsgs on 2007-02-19
ok.  a lot of the step by step instructions involve downloading them and automatically compiling/installing them in the console.  what if you download them?  is there a way to handle that in the GUI or what is the command for the console.  i remember reading about tar command, but i am a recent covert.

---

### Post by tubasoldier on 2007-02-19
I assume you are talking about downloading source codes for programs.

That would depend on the program. Most have a readme file that has the installation instructions. I would say that the majority of them will have you do a series of three commands like this:
```
configure
make  
sudo make install

```

This will compile the program from the source code and install it on your system. The issue is that this program will not show up in the package manager.

---

