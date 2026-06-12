---
title: "Using Wine with Mono"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by xNsOmNiAx on 2007-08-16
I installed wine correctly, and can open simple .exes such as notepad.

But i want to run .net  apps and it tells me i need to install Mono, so i downloaded it and was about to install it when i relized i dont know where to install it. I installed it in 2 differnt places and it still doesnt work for wine, can someone tell me where to install it?

---

### Post by finer recliner on 2007-08-16
mono is for linux you dont need wine for it.

to install it from the repos:

```

sudo apt-get install mono

```

---

### Post by xNsOmNiAx on 2007-08-16
ok well then i did that awhile back but when i try to open one of my exectuable files through wine it tgives me this error
"install the Windows version of Mono to run .NET executables"

is ther any other way to run the .exe's or is there a simple solution to this problem?

and btw when i typed that command you gave me it tels me mono is up to date and not needing an update, meaning that its installed correctly i believe cause that was the first way  i did to install mono

---

### Post by finer recliner on 2007-08-18
say you wrote a hello world app in C# (lets call the file hello.cs). to compile it with mono you use mono's C# compiler (mcs):
```

$mcs hello.cs

```
this creates a file called hello.exe

now to run the file hello.exe you use mono:
```

$ mono hello.exe
Hello World!

```

help you?

EDIT: and note that i didnt use wine for anything. i wrote my c# in linux, and it runs in linux. no windows support needed.

---

