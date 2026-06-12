---
title: "Windows to Linux Questions?"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by Zoiked on 2007-09-03
Here are a few questions that always stumped me...

What is the .exe for linux?

What is the .dll for Linux?

Does Linux have an API like Windows? (Or do you just use the functions provided by your programming langauge)

More questions later, just can't think of any.

---

### Post by nosrednaekim on 2007-09-03
a .exe is a file that is executable. they can have all sorts of suffixs like .run and .sh and none at all

.dlls are .so  in linux.

If you mean like .NET, yes, there is Mono. Desktop managers also have bindingds. There is dbus as well.

---

### Post by -SpaZ on 2007-09-03
The closest to '.exe' is '.deb'.

---

### Post by Error403 on 2007-09-03
Well, there are .sh, .run, and stuff like that.  Usually you do ls in bash and the ones in green are executable.  There are many, just like there's .exe, .bat, .msi, .com that start programs in Windows.

Also, the equivalent to your Start menu is the Applications menu at the top left  ;)

---

### Post by Paul133 on 2007-09-03
What is a .so? For that matter, what is a .dll? As for the question at hand, .deb is a Debian binary, .sh is a shell script, but th UNIX file system actually doesn't need extensions, so an executable could have no extension.

---

### Post by CryptiniteDemon on 2007-09-03
> **Paul133 said:**
> What is a .so? For that matter, what is a .dll? As for the question at hand, .deb is a Debian binary, .sh is a shell script, but th UNIX file system actually doesn't need extensions, so an executable could have no extension.

[http://en.wikipedia.org/wiki/.dll](http://en.wikipedia.org/wiki/.dll)

---

### Post by Zoiked on 2007-09-03
Thank you. Also, .Deb is a package install, not really a runnable program.

---

### Post by Paul133 on 2007-09-05
Good point.

---

### Post by SOULRiDER on 2007-09-05
One thing that confused me at first was binaries (like ,exe in windows). Binaries dont have extensions usually in fact, file extentions are there to help users, linux actually looks at the content of the files.

---

### Post by Celegorm on 2007-09-05
In linux, it is the permissions on a file that make it executable or not. If you type 'ls -l' you will get a long listing for files, the first part of which looks something like "-rwxrwxrwx" 'r' stands for read, 'w' for write, and 'x' for execute. The first rwx are permissions for the owner of the file, the second set for the group, and the third for everyone. A '-' means the file does not have that permission. So, for a file to be readable by all, writable only by the owner, and not executable by anyone, the permissions would look like "-rw-r--r--" Also, sometimes you will see a 'd' in the first slot, which means the file in question is a directory.

---

### Post by Paul133 on 2007-09-12
Actually, file extensions are not so much for users as for programs. Obviously, the *nix file system doesn't recognize file extensions. But individual programs, particularly proprietary ones, do. That's why I never save a file without an extension. I save all (ASCII) text files as .txt and all shell scripts as .sh.

---

### Post by Pumm4 on 2007-09-13
[FONT=Arial][SIZE=2]In the example below notice the distinct differences between of MS-Word and OpenOffice:

[IMG]http://www.reallylinux.com/docs/images/2_image_6b.jpg[/IMG]
[/SIZE][/FONT]

---

### Post by stchman on 2007-09-13
> **-SpaZ said:**
> The closest to '.exe' is '.deb'.

A .deb file would be analogous to a .msi for Windows.

---

