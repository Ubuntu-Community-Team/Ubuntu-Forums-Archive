---
title: "how to install a tar.gz file"
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2006-06-29
i downloaded a new version of inkscape .044 tar.gz file can some one please post instructions on how to install it. thank you

---

### Post by ciscosurfer on 2006-06-29
[quote=abu-fatu]i downloaded a new version of inkscape .044 tar.gz file can some one please post instructions on how to install it. thank you[/quote] You can add various switches to "tar" to remove the tar and the gzip (or bz2) from the file.  
Typically I use the following for files that are archived and compressed with tar and gzip (.tar.gz)
```
tar zxvf *packageName*.tar.gz
``` And for files that are archived and compressed with tar and bz2 (.tar.bz2)
```

tar zxvj *packageName*.tar.bz2

``` Hope that helps! :D

** EDIT:** The above code will decompress and unpack the files.  Post which files in are in the directory and then I can help you install the program.

---

### Post by woedend on 2006-06-29
this depends greatly.  tar.gz is just a compressed file(like zip).  It could be the source code, an installer, or an actual binary file(rare).  Most likely youve downloaded the source, in which case you would have to compile it.  To do so, you'll have to read up on it a little bit.

---

### Post by tonyr on 2006-06-29
Are you comfortable using a terminal and the command line?
**cd** to the directory where the tar file is, do what **ciscosurfer** said.

It creates a directory named **inkscape-0.44**. **cd** ino that directory
and read the INSTALL file.


If you are not comfortable with a terminal and the command line, it's going to be a little
more difficult.

Is there some reason you are building from a tar ball instead of building it
using Ubuntu conventions?  Read [this]("http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu").

---

### Post by abu-fatu on 2006-06-29
i found a link for it at gnomelook.org wanted to upgrade the version of inkscape i installed from synaptic this may be a little complicated for me . how long would it be before it is available in synaptic? thank you for the replies.

---

### Post by tonyr on 2006-06-29
[QUOTE=abu-fatu] how long would it be before it is available in synaptic? thank you for the replies.[/QUOTE]
It's hard to say.  It really depends on when the packager has time to package it and when
the maintainer gets around to putting it in the repositories.

---

