---
title: "need help on cp command"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by s1baker on 2006-11-27
I am trying to copy a directory (with all the files and directories that it contains) to another directory and I am having problems.

 When I do this:
sudo cp /home/coder/2.6.15-26-386  /etc/init.d

I get this error message:
cp: omitting directory '/home/coder/2.6.15-26-386'

2.6.15-26-386 is a directory that has other directories and files in it that are needed to get the winmodem to work, but I need for it to be in the /etc/init.d directory.

Thanks for any help

---

### Post by taurus on 2006-11-27
```
sudo cp -R /home/coder/2.6.15-26-386 /etc/init.d
```

---

### Post by Ben Sprinkle on 2006-11-27
Needed this, thanks Taurus.
I was always doing this meh:
```

sudo tar -cvf folder.tar folder
sudocp folder /newfolder
sudo rm folder.tar
sudo cd /newfolder
sudo tar -xvf folder.tar
sudo rm folder.tar

```
:p

---

### Post by s1baker on 2006-11-27
Thanks, that got it
s1baker

---

### Post by tonyr1988 on 2006-11-27
Just to explain (better to teach a man to fish, right?):

The -R that you have to add stands for "recursive" i.e. "do this operation to this folder and everything underneath it"

If you copied the folder to the destination, but none of the files / subfolders, it wouldn't really do much good, so the computer is skipping it. Telling it to copy recursively (via -R) copies the folder as well as all files and subfolders underneath it. :)

---

### Post by Ben Sprinkle on 2006-11-27
Well thanks for the information then. :)

---

### Post by taurus on 2006-11-27
```
man cp
```
:rolleyes:

---

