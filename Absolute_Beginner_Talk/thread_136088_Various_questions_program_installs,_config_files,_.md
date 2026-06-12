---
title: "Various questions: program installs, config files, etc."
date: 2006-02-25
forum: Absolute Beginner Talk
---

### Post by Solver on 2006-02-25
I am now getting relatively comfortable with Ubuntu, and I have also used some other Linux distros before, although I never really had much knowledge of the system. So I have some questions, both technical and regarding Linux-using customs.

1. I download some software in a tarball, like Skype or Thunderbird, whatever. Where do I unpack? I know I can technically unpack anywhere and it will run, but what's the standard way? Like, on Windows the standard's to install to the Program Files folder, what is it on Linux? Home folder, /opt, /usr/local?

2. I download a source tarball. Do the ./configure, make, make install dance to compile and install. What's the proper way to uninstall such software? I know there's make clean, but that would mean I have to keep the source for everything I compile around, right? Or is there a better way?

3. I understand that for a lot of installed software, /usr/bin often contains the symlinks to the actual binary execeutables. How do I do maintenance there? Is there a command that will scan for symlinks that point to nothing and delete them, or must I maintain the /usr/bin folder manually?

4. There's a load of config files under /etc. What's the most important ones that every user should know about? /etc/xorg.conf, /etc/fstab, /etc/passwd, what are the rest?

5. How sensitive is the system towards the /var folder? Is it always safe to delete logs from /var/log?

6. I have the 2.6.12-10 kernel. However, Grub also shows me the 2.6.12-9 one, and there are some 2.6.12-9 files in /boot. I assume I don't really need to keep the older version around? How can I cleanly get rid of it, if so?

Thanks!

---

### Post by cilynx on 2006-02-25
1.  You can unpack the tarball anywhere as you don't need it once you've got whatever program installed.  If you want to keep source around, the official place is /usr/src, but I'm not a fan of that as it requires root access during the compile.  Personally, I have a 'src' directory in my normal unprivileged user's home.

/opt is generally used by commercial software
/usr/local is the official place for the binarys of locally compiled software
/usr/local/bin in where the main programs go
/usr/local/lib is for libraries
...ad nausium...

2. Unless the developer includes a "make uninstall" target, then there is no quick and easy way of doing uninstall.  "make clean" only cleans up the source tree, it doesn't do anything to your filesystem.  And yes, if you're relying on "make uninstall" to save you, you have to keep the source around.  Basically, if at all possible on an Ubuntu system, you want to keep with the package system.  Many source packages include the rules to roll a .deb out of the source.  Look for a 'debian' directory.  The command is "dpkg-buildpackage" run from the root of the source tree.  If you don't have it, install the "devscripts" package and you'll get it then.

3. I don't know of anything that will automatically clean up dead links.  If you "ls --col" dead links show up as red as opposed to light blue.

4. xorg.conf, fstab, passwd, bash*, motd, modules, hosts*, shadow, suders are all pretty good things to know

5. To the best of my knowledge, it is safe to delete the archived logs.  Deleting live logs will make it complain about the log file being truncated or some such.

6. Remove the old kernel package.  
```

apt-get remove linux-image-2.6.12-9

```
or some such.

Good Luck --

---

### Post by Solver on 2006-02-25
Thanks, that's very helpful!

---

### Post by cwaldbieser on 2006-02-25
[QUOTE=Solver]Thanks, that's very helpful![/QUOTE]
Also, the "checkinstall" package makes turning source installs into a .deb a snap!  You just:
```

$ ./configure
$ make
$ sudo checkinstall -D

```

---

