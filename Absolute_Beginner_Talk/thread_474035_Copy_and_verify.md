---
title: "Copy and verify"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by ImpelGD on 2007-06-14
Is there a way to verify source and target copies of files in one process?

I'll be copying lots of flac files from a few places to my new server and would like to check for errors. Thanks.

---

### Post by meatpan on 2007-06-14
The '-v' flag to the cp command might be useful in this case.  This flag causes the command to output a brief summary of the operation that is being performed.  For example,  'cp -v a.txt b.txt' will output ' `a.txt' -> `b.txt' ' in addition to the typical errors/warnings (if any). 

Does that help?

---

### Post by ImpelGD on 2007-06-14
Thanks meatpan. But does that verbose flag actually result in verification?

---

### Post by meatpan on 2007-06-14
No, the -v flag wont check the files for existence.   The only way I know how to do this is by using commands 'stat', 'file', or a shell built-in test flag.  For example:

```


if [ -e file.txt ]; then
   # Operate on file
fi


```

---

### Post by ImpelGD on 2007-06-15
I need to not only check for files' existance, but make sure they're perfect copies.

I left a load going overnight with a normal copy from a Buffalo linkstation to the new computer, and now have 110GB of flac files ready for comparing. I'm trying to mount the samba share so that I can use the diff command, but am having a little trouble with that...

```
user@ubuntu:~$ sudo mount -t  smbfs -o username=user,password=pass //snapdragon/musiclibrary /mnt/snapdragonmusic
mount: wrong fs type, bad option, bad superblock on //snapdragon/musiclibrary,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Any ideas? Thanks for your help and suggestions.

---

### Post by 5-HT on 2007-06-15
[md5deep]("http://md5deep.sourceforge.net") would be worth checking out. It can recursively create and verify various kinds message digests.

Here's a little example that would get the job done that you can modify to your needs:```

To create the hashes: [code]md5deep -rl base_of_orig_path >> file_to_hold_digests
```To verify the hashes: ```
md5deep -x file_holding_digests -r base_new_path
```

---

### Post by 5-HT on 2007-06-15
double post

---

### Post by ImpelGD on 2007-06-15
Ok, thanks. :) But I'd still need to mount the share to treat it as part of the local filesystem?

---

### Post by vanadium on 2007-06-15
I am not sure, but would cmp not be better for comparison of binary files? Indeed, for these commands, you need to mount the remote file system in one way or another.

Probably the md5 approach will be more convenient and faster, especially if you could run the commands on local and server system. Then, only the "report" generated on the server would need to be accessed remotely (or can be copied to the local system) for verification. With the cmp approach, all of your flacs have to travel the network (again).

---

### Post by wcoenen on 2008-03-23
> Is there a way to verify source and target copies of files in one process?

You should use rsync. It always verifies the checksum of any copied files. It can do both local copies or copies over a network with a client/daemon setup. Just make sure you read the examples at the start of the man-page to understand the effect of trailing slashes :)

Sometimes however, you've already done a regular local copy and start to suspect errors afterwards. Or you started a copy, then had to abort it, and resumed with cp -ru, resulting in one file being copied only partially. In those cases, I use the following command to find any missing/different files between two directories:
```
diff -qr --speed-large-files /path/to/folderA /path/to/folderB
```

The -r option provides recursion for folders.
The -q option causes diff to just list the files instead of trying to list the differences.
The --speed-large-files option may yield performance improvements in some cases.

There also exist graphical tools that can compare folders, like kdiff3.

---

