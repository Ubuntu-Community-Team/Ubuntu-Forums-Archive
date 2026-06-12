---
title: "Problem with bzip2"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by jwmwalrus on 2007-07-01
Hi,

Not much of an absolute beginner (I've been a Ubuntu user since 2005), but this is my second post so far (and the first one is still unanswered).

I'm having a problem trying to uncompress files (with bzip2, tar, gzip).  Trying with a *.tar.bzip2 file, I get the following error:

[INDENT][INDENT]bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now[/INDENT][/INDENT]

Trying with a *.tar.gz file, I get:

[INDENT][INDENT]gzip: stdin: invalid compressed data--format violated
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now[/INDENT][/INDENT]

So far I've tried with different bz2/gz files and I always get the same error regardless of the command options I use (and I get no error with *.zip and *.rar files).  I also reinstalled bzip2, tar and gzip, but it's still the same.

What should I do to solve the the problem?  Thanks in advance for the help provided (if any).


JWM

---

### Post by gborzi on 2007-07-01
Hello jwmwalrus,
I think you need to provide some more details, i.e. which command you use and, if possible, attach a .gz and/or a .bz2 file that gives you this problem.

Regards.

---

### Post by jwmwalrus on 2007-07-01
Thanks for the reply.

I think it's not possible to post the compressed files, since they're huge (i.e., the Intel Fortran compiler, Intel Math Kernel, Sun Studio 12, VMWare server, Eclipse IDE, etc.), but nevertheless I think I just solved the problem ---or at least found a different way to uncompress.

It seems that if the files are downloaded to an ntfs file system, and then transferred to an ext3 file system, tar/bzip2/gzip are unable to uncompress properly.

It still sounds pretty weird to me, but... That's it!


J.W.M.

---

### Post by gborzi on 2007-07-01
Perhaps this is a bug in the ntfs support, AFAIK it's still in beta.

---

