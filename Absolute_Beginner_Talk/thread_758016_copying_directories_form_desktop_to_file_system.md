---
title: "copying directories form desktop to file system"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by GoliathWest on 2008-04-17
I just began working with Linux and installed u.buntu 8.04 beta x86_64 to enable me to work with 3rd party scientific software. I have a set of directories that came in the tar file after I extracted to the desktop. To launch a perl script, I need to have a /lib folder with all subdirectories in it copied to the file system. The file browser lets me copy the folder with its contents (I presume) but if I navigate to the file system, the paste option is gone when I right click.

I have tried to use the following in the terminal window:

cp -r /lib/* /usr/local/share/perlx.x.x
or
cp -r /lib /usr/local/share/perlx.x.x (and to other similar subdirectories)

also tried:
cp -avR /lib /usr/local/share/perlxxx
or 
sudo cp -avR /Desktop/dirname/lib/* usr/local/share/perlx.x.x

I am running the command line from the source directory but in all cases above the errors returned are similar to cp: cannot stat ' dir': No such file or directory.

What else should I be aware of? Where is my syntax bad?

Thanks!

---

### Post by wolfen69 on 2008-04-17
run
```
gksudo nautilus
```
then navigate to your desktop, copy files then in same window navigate to the directory where you want to paste.

---

### Post by GoliathWest on 2008-04-17
thanks, I tried gksudo nautilus but had user sharing error 255. Also, got a warning:
** (nautilus:25819): WARNING **: Unable to add monitor: Not supported 

then,
searhorse nautilus module shutdown

any help for using the CLI instead?

---

### Post by oldos2er on 2008-04-17
Start each file location from root:

 sudo cp /home/<user>/Desktop/dirname/lib/* /usr/local/share/perlx.x.x

---

### Post by GoliathWest on 2008-04-17
Thanks,
Still getting cp: cannot stat ' path/filename':  No such file or directory error after trying your suggestion.

Are there hidden directories or permissions I need to set?

---

### Post by oldos2er on 2008-04-17
Are entering any hidden directories into the command? As for permissions, if you prepend your command with "sudo" it should allow you access to all directories.

 Try using the Tab key for filename completion.

---

### Post by st33med on 2008-04-17
Also, a bit off topic, but you could do these commands in Nautilus by [setting up scripts.]("https://help.ubuntu.com/community/NautilusScriptsHowto?highlight=%28NautilusScripts%29")

---

### Post by GoliathWest on 2008-04-17
Thanks, everyone.
It turns out I was in some state where I couldn't move files around or modify anything. I could browse and run some commands, but not much else. I shut down an X window and the GDM, restarted, and then I was able to work again on the files. Sorry this lacks clarity because it was a solution that was found inadvertently.

---

