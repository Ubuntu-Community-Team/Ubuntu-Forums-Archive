---
title: "Ubuntu 7.10 upgrade Firefox 2.0.0.6 to Firefox 2.0.0.9"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by cronosmachine on 2007-11-10
Dear all i'm absolute beginner using linux,
however i just installed ubuntu 7.10, now I'm trying to update Firefox 2.0.0.6 > Firefox 2.0.0.9 by using 'firefox-2.0.0.9.tar.gz'

Since i want do in command line, can someone help me to how to upgrade/install it by using terminal mode step by step?

thank you very much in advance

---

### Post by matthewcraig on 2007-11-10
You do not need to do this.  The Ubuntu methodology is to allow Ubuntu to update the software itself.  You really never need to download tar.gz files and try to install them yourself.  All the software you need is in the Synaptic Package Manager.  If you still can't find an application, then you might encourage the application owner to work with the Ubuntu packaging team to add their software to the repository...

---

### Post by cronosmachine on 2007-11-10
hi matthewcraig,
thanks for replying, but i need to know the installation base on linux by cli, specially update/upgrade program such tar files. i don't want using gui intead using cli syntax.

thanks

---

### Post by devilears on 2007-11-10
in a terminal or konsole window, cd <directory_where_the_gzip_file_is> then type:
gunzip firefox-2.0.0.9.tar.gz
then type:
tar xvf firefox-2.0.0.9.tar
a firefox subdirectory will be created so type:
cd firefox
and then just type firefox

---

### Post by cronosmachine on 2007-11-11
hi devilears,
it that your suggestion command is replacing the old version of firefox 2.0.0.6? or just running the 2.0.0.9 at extracted folder? it seem running at extracted folder.

do you know the command to replacing the old firefox at the system?

thanks

---

### Post by FuturePilot on 2007-11-11
That's just running it from the extracted folder. You don't want to try and replace the existing version. It could totally mess your system up. The best thing to do is just wait for the update to come down through the repos.

---

### Post by PmDematagoda on 2007-11-11
Firefox 2.0.0.8 is in the repos and you can update your firefox to that with no problems.

The reason Firefox 2.0.0.9 is not in the repositories could be because there are no updates/fixes concerning Linux, the same applied for 2.0.0.7 which did not appear on the repositories since there were no fixes or updates for Firefox concerning Linux.

---

