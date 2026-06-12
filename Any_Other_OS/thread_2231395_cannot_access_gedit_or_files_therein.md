---
title: "cannot access gedit or files therein"
date: 2014-06-25
forum: Any Other OS
---

### Post by newtocoding123 on 2014-06-25
[FONT=arial]I'm trying to do some practice code but I can't open gedit from my terminal. (I have a Mac OS so it's built in.) I go to my applications folder and all I see is a file called gedit.app. So when I type in the following code

gedit practice1.cpp &

I get the following feedback:

new-host:applications gregdreifus$ -bash: gedit: command not found

So, I just opened gedit through the Mac terminal and saved a file on it called practice1.cpp

However, it only let me save this on my desktop. So, now that I'm trying to compile my code, I go to the desktop file and try to put into the terminal the following code:

[/FONT] g++ practice1.cpp -o practice1

but I'm given the following output:

-bash: g++: command not found

What do I do?

---

### Post by DuckHook on 2014-06-25
> **newtocoding123 said:**
> ...[FONT=arial]I have a Mac OS... [/FONT]What do I do?Not trying to be uncharitable, but we can't help you here and you really need to post your questions to an Apple forum. Mac OS is not Linux, even though they may have kidnapped some Gnome tools for their own purposes.

---

### Post by oldos2er on 2014-06-25
Moved to Other OS/Distro Support.

---

### Post by Lars Noodén on 2014-06-26
I don't have OS X available at the moment but if I recall correctly you'll have to use [open](https://developer.apple.com/library/mac/documentation/Darwin/Reference/ManPages/man1/open.1.html) to launch the graphical app you want if that file .  

```

open -a gedit practice1.cpp

```

If you take a look a the graphical app using the shell, you see that it's really a set of directories with a huge number of files included.  If I understand correctly, they are self-contained and statically linked.  

About gcc and g++, you'll have to get that from XCode.  I think it still might be free but you do have to download it from the Apple Store.

---

### Post by buzzingrobot on 2014-06-26
> **DuckHook said:**
> 

... even though they may have kidnapped some Gnome tools for their own purposes.

Believe this a version of gedit the Gnome folks released for OS X, as they have for Windows.

I used Macs from System 9 days until a few months ago and recall nothing "kidnapped" from Gnome.

---

