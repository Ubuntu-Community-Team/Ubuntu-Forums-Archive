---
title: "[SOLVED] MonoDevelop - can I compile Linux-native apps?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by microfi on 2008-03-01
Hi folks!
I've just installed MonoDevelop, which I found really easy to use and I've already made a simple application with GTK+ (I was used to develop Delphi apps in Windows).
I can perfectly run my project in the "Run" menu, but when I access the "Debug" or "Release" folder found in my project directory, I find my compiled file, though it's in ".EXE" format. I opened it with Hex Editor and it seems to be a Win32 application!
My question is: can I build Linux executables through MonoDevelop? You know, that things I can run directly from Nautilus.

Thanks, Filipe
PS: I've downloaded MonoDevelop through Ubuntu Repositories.

---

### Post by SOULRiDER on 2008-03-01
That EXE, even if its named .EXE should be a Linux binary, try running it by going to the directory where its located and doing
```
./program.exe
``` or whatever its called, no spaces after "./".
If it complains about permissions do a
```
chmod +x program.exe
```or whatever its called.

---

### Post by microfi on 2008-03-01
It worked! Thanks a lot!
Pardon my ignorance, but what does the "./" before the file name mean?

---

### Post by SOULRiDER on 2008-03-01
It means to look for the file in the current directory. If you just type the name it will try to run the name as a command.. its a bit different from DOS.

Oh, and dont forget to mark the thread as solved!

---

### Post by cwmoser on 2008-03-01
I use MonoDevelop but I execute my apps from the command line like this:

$  mono  ./app.exe

Doing that implies that the output file created my MonoDevelop is a real Windows executable.

Carl

---

