---
title: "super newbie needs help"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by Airais on 2007-05-22
okay I wanted to get my older computer up and running again so I put Xubuntu on it, it sweet runs fast has the things I need, but I also wanted to check out gaming on linux so I hit the web and found Dangers of the Deep (a sub simulator) and "downloaded" it, all it was was a .bin file, ........ okay now what. how do install it configure it etc......

---

### Post by BarfBag on 2007-05-22
EDIT!  Go to the website and download the package for Debian unstable.  This is much easier to install.  Then, open a terminal and type (without quotes) "dpkg -i filename.deb"

---

### Post by Alterax on 2007-05-23
.deb packages are easier, but sometimes you can't get away from a good ol' fashioned .bin file.

So just in case you get one of those, try this:

Open the terminal.
move to the directory that the .bin file is in, using the cd command.
once you find the .bin file.  Type this:

sudo chmod a+x whateverthefilenameis.bin (it's easier once you get to typing the .bin file's name, to put in the first few letters and hit tab to autocomplete it.  It's a timesaver AND prevents nasty type-os)

This sets a flag on the .bin file to make it executable.

Now run the .bin file, like this:

./whateverthefilenameis.bin

the dot followed by a slash tells the terminal "in THIS directory".  Don't put any spaces into it.

So now if you get caught having to install a .bin, you'll know what to do.

--Alterax

---

### Post by Sef on 2007-05-23
Check out [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

