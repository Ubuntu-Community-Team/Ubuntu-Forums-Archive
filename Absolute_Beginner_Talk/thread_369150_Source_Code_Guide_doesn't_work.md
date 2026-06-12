---
title: "Source Code Guide doesn't work"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by grogger13 on 2007-02-24
[HTML]To proceed you must have the compiler tools installed. They all come with the package build-essential, available in Synaptic. When you're sure you have the compiler tools installed, you fire up the terminal and change directory to the one you've just extracted (if you're not sure how to do that see: Navigating the terminal. When you're in the correct directory you execute a configure script: ./configure. Don't worry if it complains that there is no configure script - many packages don't come with one! Then you compile it with make and after it's been compiled you can install it. There are two ways:

Normal install: If you want to install it the normal "primitive" way, type sudo make install. To remove the temporary files you run make clean. To uninstall the program you run sudo make uninstall. These two clean-up commands don't always work, though, the programmer needs to have enabled them.

Package manager install: If you want to install it in a way that means it can be easily removed from inside the package manager, first install the package checkinstall. To install the package type sudo checkinstall. This will take slightly longer than a normal install and quite possibly you'll have to supply a description of the application yourself (and edit the other information slightly). If the need arises, this will be easy to take care of from inside the checkinstall program.[/HTML]


Thats the guide i found on source code install on .tar etc. but when i type in ./configure it gives me an error, can someone tell me the procedure for compliing source code

---

### Post by Athropos on 2007-02-24
Did you install build tools as requested? If not, you may do so with the following command:

```

sudo apt-get install build-essential

```

---

### Post by Bachstelze on 2007-02-24
> **grogger13 said:**
>  when i type in ./configure it gives me an error, can someone tell me the procedure for compliing source code

Hold on a sec. while I ask my crystal ball what the error is...

---

### Post by PurplePenguin on 2007-02-24
> **HymnToLife said:**
> Hold on a sec. while I ask my crystal ball what the error is...

This is "Absolute Beginner Talk", maybe you could try being a bit more helpful and less sarcastic?  What seems obvious to you may not be obvious to new users.

---

### Post by Maestro23 on 2007-02-24
> **Athropos said:**
> Did you install build tools as requested? If not, you may do so with the following command:

```

sudo apt-get install build-essential

```

And just to add this for the OP to read/bookmark: CommandLine Beginner's: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

---

### Post by v8YKxgHe on 2007-02-24
> **PurplePenguin said:**
> This is "Absolute Beginner Talk", maybe you could try being a bit more helpful and less sarcastic?  What seems obvious to you may not be obvious to new users.

True, but when the op goes "it gives me an error" how can we help if we don't know the error? That's what he's getting at.

---

### Post by PurplePenguin on 2007-02-24
Exactly.  And explaining the lack of information is a lot more productive than being sarcastic.  It's not often that I see rude posts on UbuntuForums, which is the thing that I like the most about it.

---

### Post by grogger13 on 2007-03-21
```
mike@mike-laptop:~/gtuxnes-0.75$ ./configure
bash: ./configure: No such file or directory
```

---

### Post by jvc26 on 2007-03-21
Does the installer of that application have a configure file? Are the instructions at the top for the specific app you are trying to install? And finally, have you installed the build-essential package as instructed above?
Il

---

### Post by devnulljp on 2007-03-21
> **grogger13 said:**
> ```
mike@mike-laptop:~/gtuxnes-0.75$ ./configure
bash: ./configure: No such file or directory
```
First (as noted above)
```
sudo apt-get install build-essential

```
Then cd into that gtuxnes-0.75 directory then read the file INSTALL (cat INSTALL)

```
Instructions:
        1) expand the archive
                tar zxvf gtuxnes-0.75.tar.gz

        2) change directories
                cd gtuxnes-0.75

        3) make it
                make

```
There's no ./configure step, just make

Hope that helps (what is it? an emulator?)

---

### Post by glotz on 2007-03-21
Try reading the README or INSTALL or whatever for starters.

---

### Post by theDaveTheRave on 2007-03-21
I'm only a beginer too, I often find that I get a similar error when attempting to ./configure stuff that i have downloaded.

It seems that there is often an issue with permissions so as the file can write to logs or into other restricted areas of the file system, hence I usually run the command as
> 
sudo ./configure

sudo make

sudo make install

The other issue I often seem to get though when i do that, is that i then can't find the executable (often a .bin file in Linux systems) !

And then when I do it doesn't want to run.

for instance. I have been trying to upload Netbeans 4.1 J2EE / J2Me for a college course, and it all works fine and lovely, and the IDE is great, but unless I load up the super new version (not the one recomended for my course I hasten to add) of netbeans (5.5) then I have all sort of funny errors and stuff, it isn't really a problem as I can then save the binary file and open this in the XP version that I have on the dual boot - a bit of a fad though I must say!

hope that helps.

Dave M

---

### Post by Lord Illidan on 2007-03-21
You should not type:

sudo ./configure or sudo make **unless** the files are not in your home directory and you don't have write access.

---

