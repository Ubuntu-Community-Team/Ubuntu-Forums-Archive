---
title: "wine help"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by jhayes on 2007-08-30
ok i dide apt get to get wine going. was trying to follow along with the long post on how to get wow going. but i can not get the installer started. has to do with not being able to read or write to the "c:\windows" directory. here is the errors: $ wine Install.exe
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/media/sda4/jon/wowcds', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\Install.exe": Module not found

i have looked, and i cannot figure out why. i, have full control ie 777, over the /media/sda4/jon folder. i have been in winecfg, and set the "c" drive in there. and got no where.

---

### Post by Hobo Joe on 2007-08-30
When you run 'Install.exe', are you trying to run it from the CD?

Try running it like this:
```

wine /media/cdrom0/Install.exe

```

---

### Post by jhayes on 2007-08-30
nope.
copied the cds to a folder on /media/sda4/wowcds
which i have full control over.
did cd to that dir, ran install from there to get above message.

---

### Post by Hobo Joe on 2007-08-30
Try navigating to the file with the broswer and opening it with wine.

---

### Post by jhayes on 2007-08-30
i did right click on the install file, 
chose open with wine ...
nothing happens

---

### Post by splintercellguy on 2007-08-30
Can you cd to where the EXE is, do wine nameofEXE.exe and show the terminal output?

---

### Post by jhayes on 2007-08-30
it says all this


$ wine Install.exe
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/media/sda4/jon/wowcds', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\Install.exe": Module not found

---

### Post by splintercellguy on 2007-08-30
You didn't cd to the location of the CD-ROM mount point.

Do cd /media/cdrom0 (or whatever the CD-ROM is mounted on) before running, or you could try doing wine "<drive letter of CD-ROM as set in winecfg>:\Install.exe"

---

### Post by Mogurijin on 2007-08-30
Did you [setup wine]("http://ubuntuforums.org/showthread.php?t=497332")?

---

### Post by jhayes on 2007-08-30
yes. 
i did winecfg
went through each one of the tabs. 
changed defaut guess from oss to alsa sound, set the "c" path. etc etc.

---

### Post by jhayes on 2007-08-31
some people from the #winehq channel helped.
i needed to wipe the ~/.wine dir with
rm -rf ~/.wine
then a supersecret command of "wineprefixcreate" in a terminal
right after a fresh install is needed to. that command sets up the 'c:\windows" directory.
i was good after that.

---

