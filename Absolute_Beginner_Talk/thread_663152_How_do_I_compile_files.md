---
title: "How do I compile files"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by supertails on 2008-01-09
I've fixed my computer and now I'm using Ubuntu on the internet. How do I compile tar.gz and rpm files? Thanks everyone. [http://ubuntuforums.org/showthread.php?t=662274](http://ubuntuforums.org/showthread.php?t=662274)

---

### Post by stump138 on 2008-01-09
tar.gz is actually just a compressed file.  Generally there is a readme included in the package that you can read for further instructions.  You can examine the contents in file roller or ark.

a .rpm is a redhat package manager file and they are built to work with red hat builds such as suse.  The equivalent of the .rpm in the ubuntu/debian style world is the .deb

by chance, what packages are you trying to install?

you can also try this link [here]("http://monkeyblog.org/ubuntu/installing/")  :)

---

### Post by arvevans on 2008-01-09
For those RPM files, you do not need to compile them.  You can convert them to Ubuntu/Debian compatible by using the "alien" command.

From a command screen (Applications->Terminal)
[INDENT]sudo apt-get install alien

then

"man alien" to see how to use the alien command
[/INDENT]

Your Ubuntu system can install .deb files by just clicking on the file icon, so that may be a good way to go until you are more familiar with the other formats.

Arv
_._

---

### Post by Sef on 2008-01-09
Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by luisito on 2008-01-09
You probably want to try Synaptic. I support Sef's advice.

---

### Post by supertails on 2008-01-09
Cool. Thanks.

---

### Post by twin_57103 on 2008-01-09
To create tar.gz archives, you can simply select the files, then right click and "create archive".  You will get a dropdown list of several formats, with tar.gz being default.  .tar stands for tape archive, which is a remnant from the days when tape backups were used. .gz is for gzip, a compression format.  You can also extract them directly from Nautilus - just right click and extract.

---

