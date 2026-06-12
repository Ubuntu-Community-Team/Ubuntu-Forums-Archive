---
title: "how to use wine?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-12-07
how does wine exactly work?
is there a howto on it?
or can anyone explain it to me...thanks

---

### Post by styracosaurus on 2006-12-07
You install the package wine, you can use "apt-get install wine" on the command line.

Then, when you find a Windows program you want to run, from the command line execute "wine *name of .exe file*" If it is a setup program, it will usually install it to ~/.wine/drive_c/Program Files/etc etc.

Then, you can cd to where it installed to, and do "wine *name of program*" and it will work, or it won't and you can spend some time messing with it.

There is a way to get a shortcut on desktop or button on taskbar too.

---

### Post by lucky_chouhan on 2006-12-07
if wine is perfectly compatible & configure then start the wine.


user@root#wine realplayer.exe

setup is begin like windows exactly.

---

### Post by Mazen on 2006-12-07
how? lol

---

### Post by styracosaurus on 2006-12-07
Here is some more information:

[https://help.ubuntu.com/community/Wine?highlight=%28wine%29](https://help.ubuntu.com/community/Wine?highlight=%28wine%29)

---

### Post by styracosaurus on 2006-12-07
I have found that in Ubuntu it get set up pretty nicely just by installing WINE with apt-get, like in my previous post. I was able to run StarCraft and Worms2 without touching WINE config files. So you just have to do

$ apt-get install wine

And then from the command line, in the directory it was installed to:

$ wine *name of .exe*

---

### Post by Mazen on 2006-12-07
allright..i already had wine installed, so can i go to a windows directory and excute any file already installed in windows? because i have a windows partition...
i tried running a setup but it gave me this 
" wine: could not load L"c:\\windows\\system32\\Windows.exe": Module not found "
!!

---

### Post by Mazen on 2006-12-07
ok i just tried WinRAR just to see...and it works!!:D gotta love it!!

---

