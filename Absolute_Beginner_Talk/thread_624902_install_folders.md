---
title: "install folders"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by rob1984 on 2007-11-27
hi, i'm just getting started on linux and i have a few questions.

can anyone tell me where programs are installed to?  ie. the equivalent of "c:\program files" if there is one.  

when i install a program, does it become available to all users? if not, how do i make it available?

can i choose where a program is installed?  we all know what a mess windows program installers make if we let them.  is this a problem in linux?

any help is greatly appreciated.

---

### Post by mcduck on 2007-11-27
There is no single directory where all the files of a program would be installed. Instead different files are placed in different places, depending on the meaning of the file. Usually the actual executable file will be in /usr/bin, icons in /usr/share/icons or /usr/share/pixmaps, all documentation and help files end in /usr/share/doc and so on. Most programs also have their own directory in /usr/share, and this directory contains those files that don't have any better place in the system.

These places are described in the package itself, and cannot be changed. But there really is no need to change it, the package management handles this stuff with no problems and with no mess.

If you, for some reason, would like to install some of these files into different disk it's possible to mount the disk as one of these directories. You can actually mount anywhere in the system if you just do it correctly. However doing this would not in most cases give any benefits. 

If you install a program using the package manager (apt-get, Synaptic, Add/Remove or any other tool that installs .deb packages) they are installed system-wide, and are available for all users.

Linux doesn't make mess by installing/removing programs. When you uninstall something, all it's files will be removed, and as there is no registry like Windows has there's no problem with the registry filling with useless entries. Only things that may be left behind are some text files that store settings of the programs, and using the '--purge'-option in apt-get (or 'mark for complete removal' in Synaptic will remove the setting files as well.  But as these setting files are not doing anything if the program is not running leaving them won't make your system any slower. Usually removing them is only really needed if some program is having problems and you wan to make a clean reinstall of the program.

---

### Post by PeterJS on 2007-11-27
> **rob1984 said:**
> hi, i'm just getting started on linux and i have a few questions.

can anyone tell me where programs are installed to?  ie. the equivalent of "c:\program files" if there is one.  

Yes, and no. In windows programs are monolithic, everything about a given program goes in that program's folder, linux is not like that at all, things are sorted by necessity and function.

```

/bin           contains the bare minimum basic user programs to make a system boot-able
/sbin          contains the bare minimum administrative tools to make a system boot-able
/usr/bin       is where most programs are going to end up
/usr/sbin      are the non essential administrative tools
/usr/lib       is where libraries shared among multiple programs go
/etc/          is where settings are stored

```

Taking the terminal program as an example, it has components in /bin, /usr/bin, /usr/lib, and /etc.

> 
when i install a program, does it become available to all users? if not, how do i make it available?

Depends what the program is, things that don't change system settings are available to every one right from the second they are installed. Programs that make changes to system settings are only available to people in the admin group through sudo, if you want to let user use administrative tools they should be put in the admin group.

> 
can i choose where a program is installed?  we all know what a mess windows program installers make if we let them.  is this a problem in linux?

This is technically possible but not a good idea, because things are interdependent if you put them in a non-standard location other programs that may need them can't find them. And not necessary, linux has a much more extensive path than windows, so everything ends up some where on the path, so knowing the exact location of a program isn't particularly important for most tasks.

---

### Post by Nano Geek on 2007-11-27
> **rob1984 said:**
> can anyone tell me where programs are installed to?  ie. the equivalent of "c:\program files" if there is one. The executable files themselves are usually in **/usr/bin**. But some other files are in different places around the filesystem. > when i install a program, does it become available to all users? if not, how do i make it available?It does unless it requires root to run it. Then, if you set it this way, some users will not be able to access them. But by default any user can use a root program.

> can i choose where a program is installed?  we all know what a mess windows program installers make if we let them.  is this a problem in linux?

any help is greatly appreciated.You can if you compile it yourself. But no, you can't tell the installer where to put the applications.

---

### Post by rob1984 on 2007-11-27
thanks everyone! 

this seems to be a lot better system than the windows way.
im really enjoying using linux and its so different from winows that im finding myself having to learn a lot more new stuff than i thought.

thanks again,

just one more thing, i find i remember things better if i really understand them rather than just trying to memorise random facts so, -what does etc stand for?

---

### Post by PeterJS on 2007-11-27
Same thing it does in english, et ctera. Odd I know but that's what it is, I'm sure some one more steeped in the history of old school unix could offer a better explanation of how it got that name. And the 'S' in sbin stands is for system, and usr is Unix Standard Resources.

---

### Post by Nano Geek on 2007-11-27
This might help.
[http://en.wikipedia.org/wiki//etc#Directory_structure](http://en.wikipedia.org/wiki//etc#Directory_structure)

---

### Post by rob1984 on 2007-11-27
thanks!

---

### Post by baxterdog on 2007-12-01
Yes! Thanks for answering the program location question. The answer makes sense. Am used to configuring msofts OS every dang time I reinstalled so got used to the file system and registry. Never understood why programs actually had to be 'installed' w/ MS.

Found that if I installed all my programs on a separate drive and then reformatted the OS drive, (then reinstalled) that all the programs still worked. It was obvious then that the OS really didn't need to put info about the app into every nook and cranny for it to work. i.e. just the dependent lib's and etc needed to be able to be found by the app.

---

