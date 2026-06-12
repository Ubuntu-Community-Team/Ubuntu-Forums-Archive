---
title: "Mad Libs"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Clay85 on 2006-05-09
Breezy and Dapper are types of Ubuntu. (?) 
But, what are Gnome and KDA?

I have Linux Ubuntu Breezy Gnome. Whatever that means. 

This sounds like one of those mad lib games. :)

---

### Post by ryanakca on 2006-05-09
Wharty, Hoary, Breezy and Dapper are different releases of Ubuntu/Kubuntu/Xubuntu. Kinda like Windows 3.1 and Windows 95, and Windows 98, and Windows XP.... 
Gnome is a window manager... it lets you see a desktop and icons. It has configuration utilities, and a whole bunch of other goodies... instead of you seeing a black and white terminal, where you type commands... Gnome stives for simplicity...
KDE is another window manager.... except that it's known to have more eye candy.
Kubuntu is Ubuntu running KDE.
Ubuntu is a linux distro (based on Debian) that runs KDE.

---

### Post by Clay85 on 2006-05-09
Ah, thanks. What's 'distro'?

---

### Post by ComplexNumber on 2006-05-09
[quote=Clay85]Ah, thanks. What's 'distro'?[/quote] its an abbreviation for distribution. a linux distribution is basically where a company(eg canonical owns ubuntu. ubuntu is the name of the distribution) has put together a collection of packages and customised it how it thinks the user may like it. for example, some have gnome as the default desktop environment whereas others may have KDE as default. some distributions may include lots of administration tools to allow the users more control over such tasks as adding users and such like. other distributions may not include them at all. 


btw strictly speaking, gnome and KDE are whats called desktop environments, although many people do casually refer to them as window managers.
[this]("http://www.linuxnewbieguide.org/") may give you some help.


btw as for mad libs. Mad is an audio decoder. "mad libs" are the Mad libraries.

---

### Post by Clay85 on 2006-05-09
Cool! :)

I have a quick question, why am I having so much trouble with file permissions? Everything seems to be locked. I copied a bunch of my art to my hard drive from a CD and I have to now go through every single file in the terminal and switch them to R-WR-X because they are locked. I'm having the same file permission issues with Mozilla Firefox. Is there a way to stop locking files?

---

### Post by IYY on 2006-05-09
I don't know -why- you have this problem, but you certainly don't have to change the permissions file by file. The chmod command takes a "-R" argument that makes it recursive: just call it on a folder, and everything in it gets the permissions changed.

For example:

```
chmod -R u+rwx ./*
```

Will allow the user to read, write and execute all files in the current directory, and all subdirectories in it.

---

### Post by ComplexNumber on 2006-05-09
> why am I having so much trouble with file permissions? because you're being saved from destroying your system :D.


> I copied a bunch of my art to my hard drive from a CD and I have to now go through every single file in the terminal and switch them to R-WR-X because they are locked. you don't have to do every single one individually. just create a (temporary) folder in your home directory (call it MyFiles or something), and put everything in there that you want to change the permissions of. then fire up the terminal(ie the program that allows you to type on the commandline) and enter the following command:
sudo chmod -R 777 /home/<username>/MyProgs
it will then ask you or the password that you gave during installation. this will make everything writable and readable.
note that its not necessary to type in the whole path as i have done there to MyProgs.

---

### Post by Clay85 on 2006-05-09
[QUOTE=IYY]I don't know -why- you have this problem, but you certainly don't have to change the permissions file by file. The chmod command takes a "-R" argument that makes it recursive: just call it on a folder, and everything in it gets the permissions changed.

For example:

```
chmod -R u+rwx ./*
```

Will allow the user to read, write and execute all files in the current directory, and all subdirectories in it.[/QUOTE]

Hmm I could have used that 'and all subdirectories' oh, I dunno, before i went through every file i own and changed it manually! lol :)

Thanks, actually. I was wondering what that 777 meant when I would change the permissions in the GUI, I guess that's the code for 'everything is clicked!!' hehe

---

