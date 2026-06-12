---
title: "To Install Dguitar..:'("
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by rocketboys on 2007-05-13
I'm having hard time installing this program..I looked at the install instruction,

but I don't get it...can anyone please help me step by step..?

thank you.. :)

---

### Post by jfinkels on 2007-05-14
> **rocketboys said:**
> I'm having hard time installing this program..I looked at the install instruction,

but I don't get it...can anyone please help me step by step..?

thank you.. :)

Download the Dguitar-0.5.8.zip file to wherever you download files (let's say in your home directory), open the terminal, type the following commands one at a time in your home directory:
```

unzip Dguitar-0.5.8.zip
chmod +x *.sh
./DGuitar.sh

```

You might want to make a directory for the zip file first and put the zip file in that directory, because unzip will just extract a bunch of files in whatever directory the .zip file is in. Tell me if you need more detailed instructions.

---

### Post by beanco on 2007-05-14
i have a question.... 

> Download ......  type the following commands one at a time in your home directory:

what does it mean-how do you do it....I mean the commands part

Robi

---

### Post by xyz on 2007-05-14
Hi,

Click on Applications > Accessories > Terminal

This will open a terminal into which you'll type the command lines one at a time...hitting Enter at each command line.

First you'll to go to where you downloaded DGuitar using the command: cd
For instance:
```
cd Desktop
```
IF that's where your .zip file is.

Then as jfinkels said, type:
```
unzip Dguitar-0.5.8.zip
chmod +x *.sh
./DGuitar.sh
```

Come back and tell us if it's not clear to you.

---

### Post by jfinkels on 2007-05-14
> **xyz said:**
> Hi,

Click on Applications > Accessories > Terminal

This will open a terminal into which you'll type the command lines one at a time...hitting Enter at each command line.

First you'll to go to where you downloaded DGuitar using the command: cd
For instance:
```
cd Desktop
```
IF that's where your .zip file is.

Then as jfinkels said, type:
```
unzip Dguitar-0.5.8.zip
chmod +x *.sh
./DGuitar.sh
```

Come back and tell us if it's not clear to you.

Yep.

---

### Post by rocketboys on 2007-05-14
> **jfinkels said:**
> Download the Dguitar-0.5.8.zip file to wherever you download files (let's say in your home directory), open the terminal, type the following commands one at a time in your home directory:
```

unzip Dguitar-0.5.8.zip
chmod +x *.sh
./DGuitar.sh

```

You might want to make a directory for the zip file first and put the zip file in that directory, because unzip will just extract a bunch of files in whatever directory the .zip file is in. Tell me if you need more detailed instructions.

Thank you for the response!

I tried to do what you told me to , but I'm getting message like this.

danny@Dan:~$ unzip Dguitar-0.5.8.zip
unzip:  cannot find or open Dguitar-0.5.8.zip, Dguitar-0.5.8.zip.zip or Dguitar-0.5.8.zip.ZIP.

---

### Post by jfinkels on 2007-05-14
> **rocketboys said:**
> Thank you for the response!

I tried to do what you told me to , but I'm getting message like this.

danny@Dan:~$ unzip Dguitar-0.5.8.zip
unzip:  cannot find or open Dguitar-0.5.8.zip, Dguitar-0.5.8.zip.zip or Dguitar-0.5.8.zip.ZIP.

When you give unzip the argument "Dguitar-0.5.8.zip", it looks in the current folder for the file named "Dguitar-0.5.8.zip" (or the other two as it says in it's error message). To use unzip like this, that file must be IN your current directory! To view the files and directory in your current directory use the following command:
```

ls

``` (lower case L and lower case S).

To Print your current Working Directory, type the following:
```
pwd
```

To change to a different directory (which you should do: change to the directory that contains Dguitar-0.5.8.zip):
```

cd *directory*

```
Where *directory* is the name of a directory (you might find this out by typing the 'ls' command that I gave above).

In conclusion, use 'cd' to change to the directory containing Dguitar-0.5.8.zip, then run the rest of the commands given in above posts: unzip, chmod, etc.

Tell me if you need more help.

---

### Post by rocketboys on 2007-05-14
> **jfinkels said:**
> When you give unzip the argument "Dguitar-0.5.8.zip", it looks in the current folder for the file named "Dguitar-0.5.8.zip" (or the other two as it says in it's error message). To use unzip like this, that file must be IN your current directory! To view the files and directory in your current directory use the following command:
```

ls

``` (lower case L and lower case S).

To Print your current Working Directory, type the following:
```
pwd
```

To change to a different directory (which you should do: change to the directory that contains Dguitar-0.5.8.zip):
```

cd *directory*

```
Where *directory* is the name of a directory (you might find this out by typing the 'ls' command that I gave above).

In conclusion, use 'cd' to change to the directory containing Dguitar-0.5.8.zip, then run the rest of the commands given in above posts: unzip, chmod, etc.

Tell me if you need more help.

thank you for the response!..

so i have to change the directory to where the Dguitar-0.5.8.zip exists..which is in my desktop..

so I tried

danny@Dan:~$ cd directory desktop
bash: cd: directory: No such file or directory

..

I think I'm lost.. :'(

I'm really new to this..

---

### Post by jfinkels on 2007-05-14
> **rocketboys said:**
> thank you for the response!..

so i have to change the directory to where the Dguitar-0.5.8.zip exists..which is in my desktop..

so I tried

danny@Dan:~$ cd directory desktop
bash: cd: directory: No such file or directory

..

I think I'm lost.. :'(

I'm really new to this..

No worries, friend. I suggest doing a quick Google search for "linux terminal tutorial" or something like that so you can practice the basics.

Regardless, I will still tell you what you need to know for now:

When you open the terminal in 'Applications > Accessories > Terminal', you will get a "command prompt", which looks like this:
```
danny@Dan:~$
```
'danny' is your username, 'Dan' is the hostname of the computer (it's just the nickname for the computer on the network), and '~' is your current working directory. The tilde '~' is actually a shorthand notation for '/home/danny', so you can write '~' wherever you might have written '/home/danny'. We do this because when using the terminal, you will have to type your home directory very often, and it's easier to type one character than it is to type several.

After the '$' is where you type commands (which are actually just computer programs that you want the computer to run). For example, to run the 'ls' program, type
```
ls
```
This program lists all directories and files which are contained in the current directory. To learn more about the 'ls' program, type```
man ls
``` or ```
ls --help
``` The same goes for pretty much any other program.

So to list the files in your home directory (/home/danny, or ~), open the terminal and type
```
ls
```

You will see a folder named 'Desktop' (remember, file and directory names on Linux are CASE SENSITIVE!). To change to that folder, use the 'cd' program to change your current working directory. Type
```
cd Desktop
```
to change your current working directory to the Desktop. Now use 'ls' again to view the files on the desktop. You should now be able to see the Dguitar-0.5.8.zip. Now try to unzip it.

Think you can take it from here?

If all else fails, or if using the terminal nauseates you, you can try to use the graphical file browser, Nautilus (equivalent to Microsoft Windows Explorer...but better :D), by pressing <Alt>+<F2> and typing "nautilus" at the "Run Application" dialog.

Tell me if you need any more direction.

---

### Post by rocketboys on 2007-05-14
> **jfinkels said:**
> No worries, friend. I suggest doing a quick Google search for "linux terminal tutorial" or something like that so you can practice the basics.

Regardless, I will still tell you what you need to know for now:

When you open the terminal in 'Applications > Accessories > Terminal', you will get a "command prompt", which looks like this:
```
danny@Dan:~$
```
'danny' is your username, 'Dan' is the hostname of the computer (it's just the nickname for the computer on the network), and '~' is your current working directory. The tilde '~' is actually a shorthand notation for '/home/danny', so you can write '~' wherever you might have written '/home/danny'. We do this because when using the terminal, you will have to type your home directory very often, and it's easier to type one character than it is to type several.

After the '$' is where you type commands (which are actually just computer programs that you want the computer to run). For example, to run the 'ls' program, type
```
ls
```
This program lists all directories and files which are contained in the current directory. To learn more about the 'ls' program, type```
man ls
``` or ```
ls --help
``` The same goes for pretty much any other program.

So to list the files in your home directory (/home/danny, or ~), open the terminal and type
```
ls
```

You will see a folder named 'Desktop' (remember, file and directory names on Linux are CASE SENSITIVE!). To change to that folder, use the 'cd' program to change your current working directory. Type
```
cd Desktop
```
to change your current working directory to the Desktop. Now use 'ls' again to view the files on the desktop. You should now be able to see the Dguitar-0.5.8.zip. Now try to unzip it.

Think you can take it from here?

If all else fails, or if using the terminal nauseates you, you can try to use the graphical file browser, Nautilus (equivalent to Microsoft Windows Explorer...but better :D), by pressing <Alt>+<F2> and typing "nautilus" at the "Run Application" dialog.

Tell me if you need any more direction.

Thank you for the response!

wow I'm impressed how you explained! I think I get a little bit of how this terminal works..

anyway...I made it to unzip..and I did this:

danny@Dan:~$ ls
cd  Desktop  Examples  xglsnow-0.2.0  xglsnow-0.2.0.tar.gz
danny@Dan:~$ cd Desktop
danny@Dan:~/Desktop$ ls
a_simple_rose.jpg  jre-6u1-linux-i586.bin        xglsnow-0.2.0.tar.gz
DGuitar-0.5.8      LimeWireLinux.bin
DGuitar-0.5.8.zip  Roads_WP_by_realityDream.jpg
danny@Dan:~/Desktop$ cd Dguitar-0.5.8
bash: cd: Dguitar-0.5.8: No such file or directory
danny@Dan:~/Desktop$ cd DGuitar-0.5.8
danny@Dan:~/Desktop/DGuitar-0.5.8$ chmod +x *.sh
chmod: changing permissions of `DGuitar.sh': Operation not permitted
danny@Dan:~/Desktop/DGuitar-0.5.8$ sudo chmod +x *.sh
danny@Dan:~/Desktop/DGuitar-0.5.8$ sudo ./DGuitar.sh
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at javax.swing.JFrame.<init>(libgcj.so.70)
   at dguitar.gui.DGuitar.<init>(DGuitar.java:829)
   at dguitar.gui.DGuitar.main(DGuitar.java:666)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...6 more
danny@Dan:~/Desktop/DGuitar-0.5.8$ 

Is this good..? I think there's a small error..?

umm...I'm proud of my self now! I caused an error lol I did something.

---

### Post by jfinkels on 2007-05-14
> **rocketboys said:**
> Thank you for the response!

wow I'm impressed how you explained! I think I get a little bit of how this terminal works..

anyway...I made it to unzip..and I did this:
[errors etc...]
Is this good..? I think there's a small error..?

umm...I'm proud of my self now! I caused an error lol I did something.

Great! One more hint: if you start to type the first few letters of a command or a filename, and then press Tab, bash (the program with which you are interacting inside the terminal window) will automatically complete the command or filename (or show you possible autocompletions)...so you don't have to make any more annoying spelling errors :D

As for the errors...I tried it on my system and got the same thing. The problem, I think, according to the readme file, is that this program requires java 4, and you are probably using java 5 or java 6. It would be somewhat of a hassle to find java 4 and install it, but if you're willing to go that far for this program, make a new thread in the forums describing your situation and asking for help in finding and installing java 4.

If you need anything else let me know!

---

### Post by rocketboys on 2007-05-14
> **jfinkels said:**
> Great! One more hint: if you start to type the first few letters of a command or a filename, and then press Tab, bash (the program with which you are interacting inside the terminal window) will automatically complete the command or filename (or show you possible autocompletions)...so you don't have to make any more annoying spelling errors :D

As for the errors...I tried it on my system and got the same thing. The problem, I think, according to the readme file, is that this program requires java 4, and you are probably using java 5 or java 6. It would be somewhat of a hassle to find java 4 and install it, but if you're willing to go that far for this program, make a new thread in the forums describing your situation and asking for help in finding and installing java 4.

If you need anything else let me know!

Thank you so much!

I think I'll just give up using this program..lol

I probably could just get normal tabs..

Thank you again!

---

