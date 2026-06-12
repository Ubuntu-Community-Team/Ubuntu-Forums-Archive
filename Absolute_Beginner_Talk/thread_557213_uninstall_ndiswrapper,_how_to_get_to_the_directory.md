---
title: "uninstall ndiswrapper, how to get to the directory?"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Zerol on 2007-09-22
Ive installed ndiswrapper without the Ubuntu CD in the drive and now my card isnt being recognised anymore and it seems it will never be.

I want to uninstall ndiswrapper.

Ive read a lot of stuff like;
sudo apt-get remove ndiswrapper-utils-1.9 or ndiswrapper-common those two didnt work since it says its not installed. But the most simple one;

zerol@zerol-laptop:~$ make uninstall ndiswrapper
make: *** No rule to make target `uninstall'.  Stop.

gives that error. Now Ive read that it then isnt installed in the repositories.. dont know what that is but I need to change to the directory where ndiswrapper then is installed. Maybe oh so simple but I just cant seem to find out how to cd to the ndiswrapper leave alone where it is.

Hope somebody can help me.

---

### Post by Zerol on 2007-09-22
Nobody replied yet I dont think that means any good.

Ah well Ill just reinstall Linux again.. for the last time then because this is crazy..

---

### Post by Maestro23 on 2007-09-22
If it was a .tar.gz file you need to use the make uninstall command.

Use "cd" to change to the directory you installed it from.

Get to the directory and type:

> sudo make uninstall

---

