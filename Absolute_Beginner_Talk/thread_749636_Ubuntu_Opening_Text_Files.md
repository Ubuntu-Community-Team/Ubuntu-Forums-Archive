---
title: "Ubuntu Opening Text Files"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by R6V2 on 2008-04-08
Well, I have one problem with Ubuntu, im using a application made for windows, that uses the registry to modify some stuff so it works properly. I need when I click a .au3 file, to run that file, via a executable, like:

Run("the script runner.exe /AU3EXECUTESCRIPT " and then the path to the goes after, also, when right-clicking on the file and choosing open (I'd perfer it if it said: EDIT), I need it to open this script in a specific script edtior, it's on Wine/Programs/AutoItv3/Scite/Scite.exe same with that, it must open that and the file after the name. Is this possible in Ubuntu/Linux, I am a script maker (Make programs..etc.) And really need it to be able to do this, because also, everytime i click a .txt or .au3 it gives me a warning saying it's a executable text file, which it's not, unless it's compiled.

My first impression of Linux though, I LOVE IT! It comes with all these free tools, basically MS word/powerpoint etc. FOR FREE!! Also, it's a free OS, unlike windows!

So, how can I get these right-click menus and stuff for Linux, im new, so please give me some slack, if this is already been done :) .

---

### Post by R6V2 on 2008-04-08
Ahh, My topic is going off the board! Bump!

---

### Post by stchman on 2008-04-08
> **R6V2 said:**
> Well, I have one problem with Ubuntu, im using a application made for windows, that uses the registry to modify some stuff so it works properly. I need when I click a .au3 file, to run that file, via a executable, like:

Run("the script runner.exe /AU3EXECUTESCRIPT " and then the path to the goes after, also, when right-clicking on the file and choosing open (I'd perfer it if it said: EDIT), I need it to open this script in a specific script edtior, it's on Wine/Programs/AutoItv3/Scite/Scite.exe same with that, it must open that and the file after the name. Is this possible in Ubuntu/Linux, I am a script maker (Make programs..etc.) And really need it to be able to do this, because also, everytime i click a .txt or .au3 it gives me a warning saying it's a executable text file, which it's not, unless it's compiled.

My first impression of Linux though, I LOVE IT! It comes with all these free tools, basically MS word/powerpoint etc. FOR FREE!! Also, it's a free OS, unlike windows!

So, how can I get these right-click menus and stuff for Linux, im new, so please give me some slack, if this is already been done :) .

If you want to open text files for editing gedit does a great job.

---

### Post by Joeb454 on 2008-04-08
Also, it's generally considered appropriate to bump a thread a minimum - once every 24 hours.

31 minutes....not such good forum practice ;)

Just a polite notice :)

---

### Post by R6V2 on 2008-04-08
Aha, Sorry. But, I like gEdit for like in replace of Notepad, but I cant use gEdit for making my script, I have a script edtior, and it has syntax highlighting,,,etc, And I need that one :) If I could find it on my system, I'd use it, but I cant find where it was installed.

---

### Post by ByteJuggler on 2008-04-08
> **R6V2 said:**
> Aha, Sorry. But, I like gEdit for like in replace of Notepad, but I cant use gEdit for making my script, I have a script edtior, and it has syntax highlighting,,,etc, And I need that one :) If I could find it on my system, I'd use it, but I cant find where it was installed.

What editor are you using?  (Are you using a Windows editor via Wine on Linux?)  I would actually recommend you try to find a native script editor with syntax highlighting, there should be several.  (Aside: If you're using Scite then note that there's a native Linux version of that.  I would not bother with running it via Wine.)

The warning about the executable text file, may be due to the file being marked executable, which may or may not be correct.  If it's a windows script and thus essentially a text file to Linux, you should remove the executable permissions from the file.  (To wit: Linux doesn't depend on file extensions to know what a file is, and furthermore, has "executable" as an attribute in the filesystem, so *any* file, can be potentially marked as executable, regardless of extension.  Linux decides *how* to execute a file marked as executable by looking at the file's "magic number", e.g. the first two bytes of the file, which is supposed to identify the file.)

---

### Post by stchman on 2008-04-08
> **R6V2 said:**
> Aha, Sorry. But, I like gEdit for like in replace of Notepad, but I cant use gEdit for making my script, I have a script edtior, and it has syntax highlighting,,,etc, And I need that one :) If I could find it on my system, I'd use it, but I cant find where it was installed.

Yes, gedit has syntax highlighting for writing scripts.  I use gedit to write shell scripts, C programs, Java programs, etc. and the syntax highlighting works very well.

---

