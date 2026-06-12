---
title: "[SOLVED] install programs"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by metalpancake on 2007-10-04
I am a very green user who doesn't really know much about ubuntu.
I was wondering if anyone could teach me how to install programs that have not been got through any package manager or are deb files. I have a few such programs and I know that you have to compile them yourself.
could anyone teach me how to do this?
thanks.

---

### Post by ThrobbingBrain66 on 2007-10-04
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

The above link will be invaluable to you.  Compiling is pretty easy though.  Usually it's just the same three commands in order: ./configure, make, make install; and you're done!

The vast majority of packages you'll need are in the repos however, what programs are you speaking of?

---

### Post by metalpancake on 2007-10-04
The one i'm most interested in is a video editing tool called kdenlive. it is marked as a tar.gz file format.

---

### Post by ThrobbingBrain66 on 2007-10-04
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)
Reading that section of the link I posted in my first reply will get you started.

The good news is that kdenlive is in the Gutsy repos.  So when/if you upgrade after Gutsy is released (Oct. 18th) you won't have to compile it anymore.

---

### Post by metalpancake on 2007-10-04
ok, thanks. I didn't know that. i had a look at the link, and yes, it is very good although at one point it asks you to use synaptic package manager amd this is not not working at the moment because it keeps asking me to put the ubuntu feisty disk in my drive, which I did, but it doesn't seem to recognise it.:confused:

---

### Post by ThrobbingBrain66 on 2007-10-04
To get rid of that issue, open your sources.list file
```
 gksudo gedit /etc/apt/sources.list
```

Somewhere around the top of the file should be a reference to using the Fesity CD as a repository.  Delete the reference (or just comment it out), save and close the file.  Then after you 'sudo apt-get update && sudo apt-get upgrade' in a terminal, you shouldn't have that problem anymore.

---

### Post by metalpancake on 2007-10-04
I tried all that and it worked perfectly:) thanks for the help!
the package I was trying to install by the way was build-essential, a package that the site your link went to advised me to get.

---

