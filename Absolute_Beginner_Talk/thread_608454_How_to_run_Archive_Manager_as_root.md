---
title: "How to run Archive Manager as root?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by ffury10 on 2007-11-10
I am new to the commandline but getting better daily. I downloaded a premade PHP website and I am trying to extract it to my /var/www directory. Archive Manager returns an error that it cant write to the directory /www.
When I want to edit a file, I open terminal and run sudo gedit.

How do I run Sudo Archive Manager and extract the files to /www?

---

### Post by BoneKracker on 2007-11-10
What you should probably do is learn the appropriate command-line tools.

tar is the tool most often used for creating and extracting archives.  You can learn about it by reading its manual:

man tar

One thing that's a point of confusion for many new linux/unix users that archiving and compressing are two separate things.

A tar file (something.tar) is a bunch of files combined together into a single file (an archive).

To create a tar file you use the command:
tar (and the path to the files)

To extract a tar fle you use the command:
tar -x (and the path to the tar file)

Then there is compression.  Common forms of compression are gzip, bzip, and bzip2.  So you might see a compressed archive that looks like any of the following:
something.tar.gz
something.tar.bz
something.tar.bz2

Tar can handle all of these by adding the appropriate flag.

Sometimes you'll see individuals files that are compressed:
something.gz

In those cases, you need to use tar, you can use the compression utilty itself (in that case gunzip):
gunzip something.gz

A neat thing is that many of the other tools call upon the compression tools without you having to even mention it.  For example, much of the documentation is compressed.  You might want to read the doc file, but it's in .gz format.  Not to worry, the less pager handles it seamlessly:
less something.doc.gz

Start by reading the tar man page:
man tar

Then you might also want to look at the man pages for:
gzip
bzip
zip

Also, you can run a graphical file manager like archive manager as root, but it's a good practice to avoid doing anything graphical as root because of certain weaknesses of the security model of X windows.

---

