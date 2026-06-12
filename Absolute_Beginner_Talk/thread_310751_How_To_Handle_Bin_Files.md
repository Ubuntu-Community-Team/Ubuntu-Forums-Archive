---
title: "How To Handle Bin Files"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by agonoruci on 2006-12-01
I need lots of help, I don't know how to open up or execute a bin file. I downloaded the official real-player version for Edgy Eft and I dunno how to open up.

---

### Post by mushroom on 2006-12-01
```
chmod +x <filename>
```

```
sudo ./<filename>
```

where "<filename>" is the bin file you want to use.

---

### Post by agonoruci on 2006-12-01
it's not working in my terminal man, crap

---

### Post by ewl1217 on 2006-12-01
What isn't working? Try using the ls command in the directory where the bin file is to list the contents and make sure that you're typing the right name. If you're getting any errors, please post them here.

---

### Post by NetworkGuy on 2006-12-01
For the above commands to work, you need to be in the same directory as the .bin file.

---

### Post by crazedgremlin on 2006-12-01
make sure you're not typing a space between '+' and 'x'

---

### Post by agonoruci on 2006-12-01
How would I open up the terminal in the right folder. I just downloaded the .bin file and its on my desktop, could i just go to Applications, Accessories, Terminal and then type the stuff you guys told me, and what should I type, because i might be doing it wrong, the name of the file is RealPlayer10GOLD.bin

Thx.

---

### Post by ewl1217 on 2006-12-01
Open a terminal, and try these commands:
```
cd ~/Desktop
chmod a+x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```
Make sure you enter the three lines separately and exactly as they are here. Let us know what happens.

---

### Post by mushroom on 2006-12-01
if it's on your desktop:

```
cd ~/Desktop
```

then the aforementioned commands. By the way, ~/ is a handy shortcut to your home directory. A quick terminal lesson, if you'd like:

cd <directory> - go to a directory
rm <file> - remove a file
cp <file> <location> - copy a file
mv <file> <location> - move a file

---

### Post by agonoruci on 2006-12-01
Thx, It finally worked, I am also wondering if you upgrade from Ubuntu 6.06 to 6.10 without using the CD you just do some commands and upgrade if it is official or not, because I think that this upgrading is un-official for some reason.

---

### Post by ewl1217 on 2006-12-01
Upgrading from Dapper Drake (6.06) to Edgy Eft (6.10) is official and supported. Just check out the [Edgy release notes]("http://www.ubuntu.com/download/releasenotes/610").

---

### Post by mushroom on 2006-12-01
it's official either way you do it, but upgrading from 6.04 to 6.10 is kind of risky. Fresh installation, if you have the time, is the recommended way.

---

### Post by agonoruci on 2006-12-01
Is there a page where there is a full set of command lines, or at least a set that could help a froob like me.

---

### Post by ewl1217 on 2006-12-01
I recommend that you check out the guide at [LinuxCommand.org]("http://linuxcommand.org/learning_the_shell.php"). I've found it to be a very useful resource in learning my way around the command line. If you want specific help with a program you have installed, then check out its man page. Just type
```
man <program>
```
where <program> is the name of the program.

---

### Post by agonoruci on 2006-12-01
Cool, srry for my huge Froobness, but I really wanna get to know this thing because my teacher said if you're going to get anywhere in computers learn linux, cuz its the future so ya.

---

### Post by PilotJLR on 2006-12-01
Buy a book... personally, I don't think any online tutorial beats a good paper book.
Amazon.com if chock full of book Linux books for cheap.

---

