---
title: "name of directory?"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by limac on 2007-11-02
While untaring something or while cd, how can I figure out the name of a directory?? any directory, how can I figure out the name of one. give an example. 

thnx

---

### Post by DezSP on 2007-11-02
I'm not entirely sure what you mean. You can use the ls command to list all the files/folders in a directory (ls -a for .hidden files too), and you can do stuff like ls *socks*, which will match socks/, socks.jpg, et cetera. Or you can hit tab while typing in the directory name to have it autocomplete.

---

### Post by limac on 2007-11-02
I mean like when cd, you need to enter the directory u want to change to, but how exactly can u figure out the name of the directory?

---

### Post by mgmiller on 2007-11-02
from a terminal type the command 
```
ls
```

you can also use:
```
dir
```

but it won't give you as much info.
These will show you the contents of the directory you are in.

If you then type:
```
cd ..
```

That will move you up one level.

Try typing:
```
ls
```
 again to see what's there.

Again do the:
```
cd ..
```

To move up another level, and repeat the ls command.

This is a very slow way of learning your directory file structure.
Once you see a directory name in the terminal after typing ls, you can then
directly cd to it.

Remember, Linux is case sensitive, so watch capitals.

Also, remember, in Linux you use / between directory entries, not \ as in DOS-windows.

You can also just browse around in Nautilus and look at the Location bar in the Nautilus window and it will show you where in the tree you are. Click on View in the top of the nautilus window and make sure location bar is checked off.  On the left side of the location bar is a small icon that changes how the location is displayed.  Just click it to toggle between plain directory names and names/seperated/by/.

f9 key also toggles the side bar in Nautilus on and off, you can also set that to display multiple views of your file system by clicking on the Places with the little down triangle at the top of the side bar.

The directory structure in Linux is very different than windows.  It just takes getting a little used to.

Good luck.

---

### Post by limac on 2007-11-02
what do u mean move me up one more lvl?

---

### Post by mgmiller on 2007-11-02
It's the exact same command as used in DOS/Windows.  cd ..  will move you up one level in the directory tree.  For example, in Linux (which is where we are now, I assume)  If you open a terminal and type ls  it will give you the contents or your home directory.  Mine would be /home/marty  for example.  

If you then enter cd .. in the terminal and hit enter, you will move up one level to /home

another cd .. will move you up once again to / which is the root directory.  You can't go any higher.  ls at this point will show you your entire basic directory list.  

Starting again in your home directory, type ls and then select any of the directory names you see and try cd directory name.  I have a directory named Pictures, so to get into it, I would type:
 ```
cd Pictures
```

There is no / before Pictures, because I am already in the directory I need to be. 

You could also give it the whole path to the directory which would be /home/marty/Pictures   (yours will have your name instead of marty)

You can get a little more info here:
[http://www.fast-track.cc/t_linux_22_change_directory_cd.htm]("http://www.fast-track.cc/t_linux_22_change_directory_cd.htm")

Also Here:
[http://www.tuxfiles.org/linuxhelp/linuxfiles.html]("http://www.tuxfiles.org/linuxhelp/linuxfiles.html")

You should also spend time just browsing around in your file system with Nautilus.  

Click on Places > Home   to start and turn on the features I mentioned earlier.  Get used to the layout of the file system.

---

### Post by Maestro23 on 2007-11-02
> **limac said:**
> what do u mean move me up one more lvl?

Intro to Terminal Use: [https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal)

---

