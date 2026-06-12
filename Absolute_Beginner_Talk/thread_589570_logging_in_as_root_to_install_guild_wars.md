---
title: "logging in as root to install guild wars"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by Dark-Angel on 2007-10-24
Hello,
          I am trying to install guild wars and i am trying to install to c program files but it says it can't do that and to check I have sufficient rights.  I try to log into root but it says i can't login to that from login screen. I try to install to desktop but says access denied. Any way i can install guild wars then?

---

### Post by Seisen on 2007-10-24
You can type sudo in front of the command you are trying to use in the terminal. Otherwise you will need to setup a root account because by default Ubuntu doesn't come with it setup.

---

### Post by donkyhotay on 2007-10-26
Be aware that running a standard program like that as root is a serious security no-no. Seriously, you might as well be running windows it thats the way your going to use your system. I would recommend changing the permissions of the directory you're trying to install to rather then running it with sudo (default is ~/.wine/drive_c/Program\ Files/Guild\ wars/). If your trying to install to a windows partition (your mention of "c program files" is what makes me mention this) then you may run into problems with NTFS permissions but then I would also mention you might as well play it natively by that point. Another thing I've noticed similar to this you mentioned (and possibly related) is the most recent versions of guild wars with wine changes the permissions of Gw.dat and Gw.tmp (both files are located wherever guildwars itself is isntalled) to 'no read, no write' when it's shutting down. Next time you try to run the game with wine it fails because it can't read/write those files. To fix it you need to change the permissions on both files before playing. Myself, I just created a small script to change the permissions of these two files to accept read/write before running the actual program itself. Not certain why it does this but it didn't do it until recently so I think it's an 'enhancement' to guildwars itself.

---

### Post by Crafty Kisses on 2007-10-26
> **Dark-Angel said:**
> Hello,
          I am trying to install guild wars and i am trying to install to c program files but it says it can't do that and to check I have sufficient rights.  I try to log into root but it says i can't login to that from login screen. I try to install to desktop but says access denied. Any way i can install guild wars then?

You might want to try the following:
```
sudo -i
```
Then try what you were going to do.

---

