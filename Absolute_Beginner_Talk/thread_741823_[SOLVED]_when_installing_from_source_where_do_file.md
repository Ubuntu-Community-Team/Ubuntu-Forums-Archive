---
title: "[SOLVED] when installing from source where do files go?"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by tropdoug on 2008-04-01
[COLOR=Black]If I am installing a package from source forge [/COLOR]

[COLOR=Blue]http://sourceforge.net/project/showfiles.php?group_id=154566&package_id=171775&release_id=585444

[COLOR=Black]In windows I am used to the installer placing the files and creating the directories but I am a bit at a loss as to what happens in Ubuntu. I still have not got to grips with the directory structure. So when doing this from source, and having to install it manually, what do I do so that I maintain a well structured file system, (if that makes sense) 

Thanks for any help[/COLOR]
[/COLOR]

---

### Post by talsemgeest on 2008-04-01
It varies between programs, but it will probably be somewhere in your /usr/share/ directory.

Hope this helps :)

---

### Post by aquavitae on 2008-04-01
What program is it (the address you gave didn't go anywhere)? Have you looked for a deb file instead of source - much easier to install!

Assuming you do have to compile from source... what commands are you typing? Ususally it goes along the lines of ./compile, make, make install.  But sometmes these an install script instead. If you're typing make install, then you might be able to find out where it puts files by opening up the file 'makefile' and seeing what it says under Install. But otherwise you could always just do a search...

---

### Post by talsemgeest on 2008-04-01
> **aquavitae said:**
> What program is it (the address you gave didn't go anywhere)? Have you looked for a deb file instead of source - much easier to install!

Assuming you do have to compile from source... what commands are you typing? Ususally it goes along the lines of ./compile, make, make install.  But sometmes these an install script instead. If you're typing make install, then you might be able to find out where it puts files by opening up the file 'makefile' and seeing what it says under Install. But otherwise you could always just do a search...
Don't you mean ```
./configure
```?

---

### Post by Xiong Chiamiov on 2008-04-01
[This]("http://en.wikipedia.org/wiki//etc#Directory_structure") seemed to be the best explanation that I could find of where most apps are stored.  I find myself constantly frustrated by not knowing where most of my applications are, without having to search for them or look up the installed files list in adept.

---

### Post by xeth_delta on 2008-04-01
> **Xiong Chiamiov said:**
> [This]("http://en.wikipedia.org/wiki//etc#Directory_structure") seemed to be the best explanation that I could find of where most apps are stored.  I find myself constantly frustrated by not knowing where most of my applications are, without having to search for them or look up the installed files list in adept.

You can try using certain commands to find where programs are:
```
whereis program_name
```

---

### Post by Xiong Chiamiov on 2008-04-01
> **xeth_delta said:**
> You can try using certain commands to find where programs are:
```
whereis program_name
```

Mmm, that is quite a useful tip.  Thanks much.

---

### Post by tropdoug on 2008-04-01
Thanks for the information, especially the hierarchy tree. have bookmarked that & will use it often. 

The program I am going to install is called SlideProject, I think it's similar to Pro Show gold, for windows, and that is what I need. I don't know if it comes in a deb file I will search and see. 

From most of the answers it seems that there is not one main directory that contains all the apps, as in windows 'program' so does anyone know how linux decides where to put apps? or is it all down to the users preference, like as in /usr/ 

Doug

---

### Post by xeth_delta on 2008-04-01
One more thing I would like to add, that has not been mentioned, is that you actually choose the path were the compiled prgram will be installed. For instance let's say we want to install program compiled by ourselves in a separate directory, say /compiled:
```
./configure --prefix=/compiled
```
In that case executables will be installed in /compiled/bin, libraries in /compiled/usr/lib, etc. This way you could separate what you compile from what has been installed via apt (which would go in the regular directories).

To be then able to run the program from the command line, no mather where in the directory structure you are, just add the executable directory to the PATH evironment variable.
For bash, make a backup of ~/.bashrc, edit it, look for the line starting with "export PATH" (if there is no such line, create it) and append the new directory:
```
export PATH=$PATH:/compiled/bin
```
Save the file, the new PATH will be available in any newly open terminal or source ~/.bashrc
```
. ~/.bashrc
```
to make the new PATH available in the current terminal.

---

### Post by aquavitae on 2008-04-02
> **talsemgeest said:**
> Don't you mean ```
./configure
```?
Yes :oops: I think my mind was on something else!

---

### Post by 3rdalbum on 2008-04-02
When you compile software, by default everything will go into */local/* directories.

For instance, rather than /usr/bin, it will install the executable into /usr/local/bin. Instead of libraries going into /usr/lib, they will go into /usr/local/lib.

There's a very good way to maintain a clean system when you are installing from source. Install the package "checkinstall". Whenever you are compiling, instead of doing "sudo make install", run "sudo checkinstall" instead.

Checkinstall will use the source to create a Debian package, and register it with Synaptic. So if you decide you don't want the program anymore, you can go into Synaptic and uninstall it like you would any other package.

---

### Post by tropdoug on 2008-04-03
Very useful replies thanks everybody, my apolagies for not getting back sooner, that 'work' thing got in the way. 

One other thing, I downloaded hplip ti install as I needed it to find my wireless hp all in one. The source fourge instructions said to download it to a location such as ~/desktop, so I did that and then followed the instructions for installing it. Everything went great except that I am left with the file 'hplip 2.8.4' sitting on the desktop where I don't want it. 

2 questions, 

1) do I need this file anymore, or can I delete it, or move it. 
2) if either of the above, how? because I tried to move it to see what happened and was told I did not have the permission, so I am thinking that I would have to do 
[COLOR=Blue]sudo mvdir[/COLOR] in order to move it, is that correct?

---

### Post by talsemgeest on 2008-04-03
You should be able to delete it, I doubt an app would leave somehing important on your desktop. The easiest way to delete it is to open a root nautilus: ```
gksudo nautilus
``` Navigate to the file then <shift>+<Delete> it.

Hope this helps :)

---

