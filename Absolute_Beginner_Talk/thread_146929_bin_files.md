---
title: "bin files?"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Reggaeton King on 2006-03-19
I have no clue what bin files are. I googled it and I got you can burn them onto a cd. I dont want to do that. What other type of file are like bins? How do I open them? I want to install Java SDK and I downloaded the bins. Can someone help me?

---

### Post by brainkilla on 2006-03-19
make it executable by running ```
chmod a+x name_of_the_file.bin
``` and then run it ```
sh name_of_the_file.bin
``` It will install Java in /usr/share I believe. And these .bins are something completely different than .cue/.bin container files, which are similar to .iso files....

---

### Post by Reggaeton King on 2006-03-19
Thanks a lot man! But it installed on the desktop lol. The filesystem is not editable, I can create or modify any folders or files in there. And do I have to set java executable like in Windows in my enviroment variables?

---

### Post by taurus on 2006-03-19
Actually with Java, you need to move it to /usr/share first if you want to extract it there because if you run it, it will extract it wherever it is rght now and don't forget to use "sudo" in front if you want to install it for your system...

---

### Post by Reggaeton King on 2006-03-19
I can not make any changes in that directory! I am the main user and the only user.

---

### Post by taurus on 2006-03-19
What directory?  Is that your home directory or somewhere else?

---

### Post by Reggaeton King on 2006-03-19
in the filesystem, the main place where all my files are. 
example: usr/share
I can't make or modifiy any thing in there. I keep saving things on my desktop

---

### Post by taurus on 2006-03-19
If you want to modify anything outside of your home directory, you need to be root and one way is to use the sudo command!!!  For instance, if you want to modify your apt-get's sources list, you would do
```

sudo gedit /etc/apt/sources.lst

```

---

### Post by Reggaeton King on 2006-03-19
I am the root and it still wont enable me to do anything with the system files

---

### Post by taurus on 2006-03-19
[QUOTE=Reggaeton King]I am the root and it still wont enable me to do anything with the system files[/QUOTE]
What do you mean you are the root???  Do you actually login as root or "su" to root or do you mean you login with your username and password that you have created during installing and thinking that you are root since you are the only user on your machine?  Again, have you tried running the command with sudo in front and if it's still giving your problem, what is the output of this command then,
```

id

```

---

### Post by Reggaeton King on 2006-03-19
[PHP]uid=1000(chris) gid=1000(chris) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),44(video),46(plugdev),104(lpadmin),
105(scanner),106(admin),1000(chris)[/PHP]
this is what it gives me when using the "id" command

---

### Post by taurus on 2006-03-19
Then do you get any error message when you run these?
```

sudo cp /etc/X11/xorg.org /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf.bak

```

---

### Post by Reggaeton King on 2006-03-19
[PHP]
chris@RKing:~$ sudo cp /etc/X11/xorg.org
cp: missing destination file
Try `cp --help' for more information.
chris@RKing:~$ sudo gedit /etc/X11/xorg.conf.bak
chris@RKing:~$ sudo cp /etc/X11/xorg.conf.bak
[/PHP]
That is the result.

---

### Post by steve.horsley on 2006-03-19
You should be aware that there is an administrator account called **root** on your system. You do not log in as root, but you can assume root's identity for a while and thus gain the rights to modify all files/directories by puttong the word **sudo** (Super User Do) in front of any command you type. In the example you gave above, you entered a short version of the command taurus gave you, so got an error message about the missing argument. Otherwise, it would have silently obeyed the command. 

Read this: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

You should run the java installer (?.bin) as root, i.e. **sudo ./whatever-it-is.bin** and this will give it the right to install itself where it wants. You will then need to change the symlink  /etc/alternatives/java to point to your installation rather than the JVM that gets instelled by default.

Incidentally, the Sun JVM is in the multiverse repositories, and can be installed by Synaptic. This is probably easier to do. You need to add the repositories to synaptic though:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

HTH

---

### Post by taurus on 2006-03-19
If you look at my above message again, you would see I have
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo gedit /etc/X11/xorg.conf.bak

```
:confused:

---

