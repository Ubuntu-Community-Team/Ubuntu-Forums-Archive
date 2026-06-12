---
title: "HOWTO: Zipping multiple files in multiple subdirectories"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by paligap2012 on 2007-11-20
**Hello every one.**

Here is the deal:

I have a Directory with many subdirectories.
Inside each one of them there is a DOC file.

What I want is a command to compress each Doc file with the ZIP extension in all directories at once

Then, I would like to delete all the DOC files, leaving just the Zip files

I would apreciate your help

Thanks

**Paligap **

---

### Post by 1/0 on 2007-11-20
1st, the name of this thread is a bit misleading. It sounds like you wrote a Howto so maybe remove the HOWTO prefix...

Now, for your problem. Do you mean that you want to compress lots of .doc files in a path with the path kept? I think this might do the trick:

```
tar -cfZ foo/
```

refer the man for tar if you're uncertain

```
man tar
```

---

### Post by HermanAB on 2007-11-20
Hmm, use tar.  Always tar a directory.  Never tar a file or worse, a bunch of files. (If you ever tar a bunch of files, then some crazy geeks are going to hunt you down and clobber you with a baseball bat...)

$ tar -zcvf archivename.tgz directoryname

Cheers,

H.

---

### Post by stchman on 2007-11-20
> **paligap2012 said:**
> **Hello every one.**

Here is the deal:

I have a Directory with many subdirectories.
Inside each one of them there is a DOC file.

What I want is a command to compress each Doc file with the ZIP extension in all directories at once

Then, I would like to delete all the DOC files, leaving just the Zip files

I would apreciate your help

Thanks

**Paligap **

You will need to use the find command with -exec in the mix.  Also the great thing about find is that it is recursive meaning it will start at the top and work its way down the directory tree.

[http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=f/find](http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=f/find)

Example:

```

find ~/ -name "*.doc" -exec gzip {} \;

```

This will search for all files in your home directory with the .doc extension and work its way down the directory tree.  Every time find finds a .doc file it will execute the gzip command on that file.  The {} uses the result of the find as the argument for gzip.  Gzip is handy as it just adds a .gz onto the filename.

Now gzip will usually replace the file in favor of its new compressed format.  If it does not then you will have to find all the .doc files and delete them.

```

find ~/ -name "*.doc" -exec rm -f {} \;

```



Hope this helps.

---

### Post by 1/0 on 2007-11-20
Oh, and to remove something recursively add the -r flag to rm.

---

### Post by paligap2012 on 2007-11-20
[B]Thanx a lot to all of you!
[/B]
**Stchman** gave me the answer I wanted, except for just one thing...

Is it possible to have a *.zip file instead of a *.GZ file? 

Thanx!

**Paligpa2012**

---

### Post by disturbedite on 2007-11-20
i'd second this, i'd like to know if this is possible with rar.  iirc, i remember seeing that it isn't possible with winrar, but what about rar (command line of course) linux?

---

### Post by HermanAB on 2007-11-20
Rar has a licensing problem.  Don't use it.

Tar balls, including gzipped tar balls are fine on all kinds of Unix and Windoze.  Both Winzip and 7-zip understand tar balls.  So, there are good reasons why tar balls are preferred on Linux - it is truly cross platform.

Cheers,

H.

---

### Post by stchman on 2007-11-20
> **paligap2012 said:**
> [B]Thanx a lot to all of you!
[/B]
**Stchman** gave me the answer I wanted, except for just one thing...

Is it possible to have a *.zip file instead of a *.GZ file? 

Thanx!

**Paligpa2012**

I chose gzip as it replaces the file in favor of the new gzipped file.  It simply adds a .gz on to the end of the file i.e. mydoc.doc.gz

There is no advantage of a .zip over a .gz especially since you are doing a search.  You could try this:

```
find ~/ -name "*.doc" -exec zip my_docs.zip {} \;
```

This will create a my_docs.zip in your home folder.

Only problem is that you still have all the .doc files as well.  You will need to delete them after they are compressed.

---

### Post by disturbedite on 2007-11-20
i'm aware rar isn't open-source, but that doesn't mean there is a "licensing problem" per se...

---

