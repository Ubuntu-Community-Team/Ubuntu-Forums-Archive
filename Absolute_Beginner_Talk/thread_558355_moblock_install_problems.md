---
title: "moblock install problems"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by uknowho008 on 2007-09-23
EDIT
I realized i forgot to install unrar. so now i just need to know how to reinstall the program cause its running but not doing what its supposed to do. thanks




i installed moblock another computer just fine but on this machine i get this error after running the last command.

gunzip: level1.gz: No such file or directory
dpkg: error processing moblock-nfq (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 moblock-nfq
E: Sub-process /usr/bin/dpkg returned an error code (1)



here is the command "sudo apt-get install moblock-nfq"

and here is what im following for the install [http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock](http://ubuntuforums.org/showthread.php?t=192559&highlight=moblock)

thanks guys

---

### Post by uknowho008 on 2007-09-23
ok, so i forgot to install the unrar thingy. so now moblock is running. but do to the errors during the original install it is not doing what its supposed to do. so how do i reinstall it??

---

### Post by uknowho008 on 2007-09-24
anybody?

---

### Post by uknowho008 on 2007-09-24
still havent figured this out.

---

### Post by Maestro23 on 2007-09-24
How did you install moblock-nfq?  .deb?

> sudo dpkg -P moblock-nfq

*Will delete config files as well.

Then re-install.

---

### Post by uknowho008 on 2007-09-24
awsome man, thanks for the help.

---

### Post by misfitpierce on 2007-09-24
Thought... If this is for downloading etc... Deluge and Azureues on torrent side can do IP blocking built into them and while they are running it will block those IP's from whole environment. Much easier... just an idea tho :)

---

