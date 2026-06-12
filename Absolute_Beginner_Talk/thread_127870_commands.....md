---
title: "commands...."
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by vipin on 2006-02-10
Ok!

Finally I have learned the hard way on how to execute an application in linux. I was not aware that the way to execute an application is using ./abc where abc is the name of the application. 

I am still short of commands in linux which are required to be used. Please tell me some basic commands so that I can start exploring Linux. 



Also, please tell me how to actually Install an application in Linux...

For example, Xmms player is the WinAmp of Linux. Remember that I don't have internet connection at my home. So I will have to manually install it. How to do that? Say, if I can download the Xmms player and copy its file at a folder in my desktop, how to install it then?

Also, if possible please tell me about the folders of Linux. There are folders, 

media, etc, bin .... I am not able to understand what they do. I know about media and home folder.any help will be appreciated!


I have also found the real Winamp of Linux, here it is:-
[http://www.filepedia.com/alternative_platforms/linux_software/winamp_for_linux.cfm](http://www.filepedia.com/alternative_platforms/linux_software/winamp_for_linux.cfm)
thanx

---

### Post by Maelgwyn on 2006-02-10
if it's a .deb file, you can do this:
 
```

sudo dpkg -i *filename.deb*

```
 
And that will install it :)

---

### Post by vipin on 2006-02-10
thanx, more commands are welcome!!!:-D

---

### Post by 3rdalbum on 2006-02-10
To change directories in the terminal, type "cd " then drag a folder to the terminal. Switch back to the terminal and hit Return.

To get a manual showing how to use a particular program from the command line, type "man " and the name of the program.

If you want to search through the available manual pages for a piece of text, type "man -k " and the string.

That's about all the Unix I know...

---

### Post by jsiii on 2006-02-10
I also found out how to copy files in terminal. Ain't that cool :p 

```
sudo cp /sourcedir/sourcefile.txt /destdir/destfile.txt
```

It was interesting for me to find out that files and directories are case sensitive.

Other interesting trick is to press TAB key when you are writing to terminal. It will autocomplete your commands, insert filenames and so on.

---

### Post by Tiede on 2006-02-10
Take a look at [ this website ](www.linuxcommand.org). It will teach you a LOT about the command line, who knows, maybe you'll even fall in love with it! ;)

---

### Post by Madpilot on 2006-02-10
Tab-complete is very cool; case sensitivity trips a lot of people up...

[https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands) has some of the basic terminal stuff, and links to more tutorials.

---

### Post by jsiii on 2006-02-10
[QUOTE=Tiede]Take a look at [ this website ](www.linuxcommand.org). It will teach you a LOT about the command line, who knows, maybe you'll even fall in love with it! ;)[/QUOTE]

Command line is very good thing. When someone directs you what to do, it is pretty simple when you use command line. You don't need to give directions like: Drag this there, click this, ... no no, not this. I already love it.

---

