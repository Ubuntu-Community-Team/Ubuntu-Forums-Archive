---
title: "dont know how to install anything"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by mattigus on 2007-05-01
Let's say I downloaded an application from a website that I wanted to install (in this case, Grid Wars 2.)  How would I go about installing it?  I try executing the file that seems to be the installer, but it does not work.

Sorry I'm such a Linux noob.

---

### Post by icechen1 on 2007-05-01
Are you trying to open an EXE file?If yes,you need to install Wine

---

### Post by Tomosaur on 2007-05-01
The 'standard' way of installing things is to click Applications > Add/Remove and choosing your software from there.

If you want to install software from other places, such as websites, then it depends in the file extension. What is the full filename of the file you downloaded?

---

### Post by mattigus on 2007-05-01
It's an "executable" file.  I downloaded the Linux version of the game.

---

### Post by Tomosaur on 2007-05-01
> **mattigus said:**
> It's an "executable" file.  I downloaded the Linux version of the game.

Yes, but what is the actual filename?

---

### Post by mattigus on 2007-05-01
file name is "gridwars"

Mime Type is application/x-executable

---

### Post by icechen1 on 2007-05-01
> **mattigus said:**
> It's an "executable" file.  I downloaded the Linux version of the game.

did you extract it?I extract it and it works.

---

### Post by Tomosaur on 2007-05-01
> **mattigus said:**
> file name is "gridwars"

Mime Type is application/x-executable

Ah ok, well then, right click the file, and select properties. Go to the permissions tab, and set the file to be executable.

Alternatively, in the terminal (applications > accessories > terminal), you need to go to the directory where the file is:
```

cd directory/to/file

```

then use the following commands:
```

chmod 755 ./gridwars
./gridwars

```
This should make the file executable, and then launch it.

Once the file is executable, you should just be able to double click it to run it.

---

### Post by mattigus on 2007-05-01
I extracted it to the desktop.  Does it go somewhere else?

---

### Post by icechen1 on 2007-05-01
> **mattigus said:**
> I extracted it to the desktop.  Does it go somewhere else?

go to where you extracted it and try open it
it dosen't matter where you extract it.

---

### Post by Sef on 2007-05-01
Read [How to install anything on Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

From the above:

> Windows Executable (.exe)
    If you, after having searched around the Internet for a Linux version or a viable Linux replacement for the Windows program you want to install, find that there is no Linux program that will replace it, there is a slight chance the Windows executable will run on Linux[5]. This is not a proper solution to your problem, not in any way, but for some people it's the only way. To run Windows executables you need to install a package called wine. When that is done, run the command wine PATH in the terminal where PATH is the path to your EXE. If the user carl has an EXE called test.exe inside his home folder, he'll run the command wine /home/carl/test.exe to execute it. Be adviced that running Windows programs in WINE is often very buggy and probably won't work to your satisfaction; very often it doesn't work at all!


---

