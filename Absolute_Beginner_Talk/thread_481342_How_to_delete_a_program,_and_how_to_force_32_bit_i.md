---
title: "How to delete a program, and how to force 32 bit install?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by virgilnilson on 2007-06-22
Hi, I am running Feisty 64 bit, and I have two questions here. The first has to do with how to delete a previous install of Savage ([http://www.s2games.com/savage/downloads.php]("http://www.s2games.com/savage/downloads.php")).

I used all the default settings in the GUI installer, and it seems to have installed to /usr/local/games/Savage. At first I tried to use the normal "Savage" icon under applications to run the program, and it did nothing. When I tried to run the dedicated server, it produced this output:

```
grep: /home/virgil/.savage/startup.cfg: No such file or directory
Your startup.cfg doesn't include dedicated_server 1!

Press any key to close this window...
```

When I then used terminal to navigate to /usr/local/games/Savage and typed ./Savage, I would get this output:

```
./silverback.bin: error while loading shared libraries: libcom_err.so.2: cannot open shared object file: No such file or directory

```

After searching around it seems that my problem may have to do with this being a 64 bit version of Ubuntu, and someone suggested there was a way to force a 32 bit install and that that would solve my problems. So I decided to try to uninstall this failure and try again to install it under forced 32 bit when I could figure out how to do that.

So once again I was in terminal navigated to /usr/local/games/Savage and I typed ./uninstall which would give me this output:

```
 ./uninstall
Could not find a usable uninstall program. Aborting.

```

So, I have no idea how to go about uninstalling it. Searching for the similar error on google had suggestions for people to be under the same user that installed it, which I really have no idea what it means, I assume that since I am always using the only account that would be the case. I'm also iffy about just deleting the folders and files, as I have no idea what that would leave behind.

Finally, after eventually uninstalling it, how would I go about forcing a 32 bit install? The file format is .run, which was a godsend to me because I get so lost trying to compile source.

Thanks in advance.

---

### Post by octoberdan on 2007-06-23
Try asking this guy [http://ubuntuforums.org/showthread.php?t=481426](http://ubuntuforums.org/showthread.php?t=481426) what guides he followed.

---

