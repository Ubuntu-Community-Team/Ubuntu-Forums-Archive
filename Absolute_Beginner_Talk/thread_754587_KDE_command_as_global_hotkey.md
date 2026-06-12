---
title: "KDE command as global hotkey"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by Lolicon on 2008-04-13
How would I wrap a command such as:
```
/home/w/Desktop/foobar2000/foobar2000.exe /pause
```
as a global hotkey?

---

### Post by cm.squared on 2008-04-14
The howto listed in [this thread]("http://ubuntuforums.org/showthread.php?t=79560") would seem to fit the bill.

Also, forgive me if you are just using foobar.exe as a generic example, but ubuntu (and linux in general) can't run programs that end in .exe, which is a sign that it is a windows program.

That is to say, ubuntu can't run .exe/windows programs natively.  Using an emulator-like program called *wine* you can run windows programs, but it doesn't always work perfectly.  With how many native applications there are for linux you can probably find one with the functionality you need.

If you already know all of that, sorry for being redundant.

---

### Post by Lolicon on 2008-04-15
No problem, you helped immensely.

---

### Post by Lolicon on 2008-04-16
I installed xbindkeys, but it doesn't seem to work. The keys dont connect to the command and I get a:
> sh: /home/w/Desktop/foobar2000/foobar2000.exe: Permission denied

---

### Post by cm.squared on 2008-04-17
It sounds like foobar.exe isn't executable.  Try this:
```
chmod +x /home/w/Desktop/foobar2000/foobar2000.exe
```
In unix based operating systems files have permissions attached to them that determine who can do what with them, so users don't interfere with each other.  For any given file the permissions give rights to read, write or execute a file.  Files you make are automatically read/write, but as a security measure you have to explicitly make a file executable (run it as a program).

That should work, but if you don't have wine installed you won't be able to run a .exe program.

---

### Post by Lolicon on 2008-04-19
> **cm.squared said:**
> It sounds like foobar.exe isn't executable.  Try this:
```
chmod +x /home/w/Desktop/foobar2000/foobar2000.exe
```
In unix based operating systems files have permissions attached to them that determine who can do what with them, so users don't interfere with each other.  For any given file the permissions give rights to read, write or execute a file.  Files you make are automatically read/write, but as a security measure you have to explicitly make a file executable (run it as a program).

That should work, but if you don't have wine installed you won't be able to run a .exe program.

It should work and it did. Thank you very much, now I have global hotkeys!

---

