---
title: "How to install things in Ubuntu"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Dvorakis on 2007-06-17
I've recently installed ubuntu and its a charm...Im in love,everything about it I like...besides maybe one thing thats confusing me,For most things to install you have to use these wierd codes in the terminal...and **** like that,you know.I really get confused with all of this...and I was wondering if someone had a guide to help,or something like that....I've been trying to install the kiba dock and gdesklets...and I just can't figure out what the hell it is they are trying to do.

---

### Post by p_quarles on 2007-06-17
There are a lot of things you can install without the terminal. The best place to start is in the Applications menu, under "Add/Remove." If you don't find what you're looking for there, go to the System menu, select Administration, then select "Synaptic Package Manager." Synaptic has a huge list of apps, so it's best to use the search function.

EDIT: Also, for some apps you need to add special repositories. This link gives you a good how-to: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by mikewhatever on 2007-06-17
Here is one of many [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
If you need more, well, I've googled it for you
[http://www.google.co.il/search?q=ubuntu+install+software&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](http://www.google.co.il/search?q=ubuntu+install+software&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a)

---

### Post by Dvorakis on 2007-06-17
Ok...Well Just incase,if I need to use the terminal...Is there anything you can tell me that might help me understand exactly what the hell it is Im doing,and how to know if IM doing it right.

---

### Post by machoo02 on 2007-06-17
Asiyu has a good little intro guide over at [Psychocats]("http://http://www.psychocats.net/ubuntu/terminal")

---

### Post by p_quarles on 2007-06-17
> **Dvorakis said:**
> Ok...Well Just incase,if I need to use the terminal...Is there anything you can tell me that might help me understand exactly what the hell it is Im doing,and how to know if IM doing it right.
Sure. If you were to type ```
sudo apt-get install gdesklets
```

you would be telling the system to 1) log you in as a superuser (requires your password), 2) run the "apt" package management application for downloading 3) installing the file(s) that were downloaded, and 4) specifying the file that you want to download and install.

---

### Post by steveneddy on 2007-06-17
Please [look here]("http://doc.gwos.org/index.php/Main_Page") also.

Choose Ubuntu Administration and click the version of Ubuntu you are using. This is guide to help you understand Ubuntu and how to install and customize the installation for you.

---

### Post by arvevans on 2007-06-18
The Linux CLI (Command Line Interface) commands are actually fairly simple, once you understand the principle behind most CLI inputs. In Windows CLI you had commands like "dir System_32" or "copy source_file dest_file".  Linux CLI commands are much the same but with a more structured approach.  The usual layout of a command is like this:

[INDENT]command [options] target[/INDENT]

The "options part is "optional" and are modifiers that control how the command works, or what it does to the target.  For instance "ls -l /home" lists the superblock (the directory list) of files in location /home.  The "-l" option tells the ls command to use the long form of output that shows more detail about the files.

In the CLI command:  "apt-get install foobar"  you are telling the system to use the program called "apt-get" to locate an installable program called "foobar" and the option tells it to "install" the program when it finds it.

Almost all CLI commands have a manual page.  This is the description of what the command does and how to use it.  You can view the manual or "man page" for almost any CLI command by simply typing something like this:

[INDENT]man apt-get[/INDENT]

This will let you see the man page for the apt-get command.  When viewing man pages you use your keyboard arrow keys to scroll up or down in the text and just hit "q" when you are done and want to exit the page.
_._

---

### Post by Dvorakis on 2007-06-18
Thanks a lot,This helps a ton...I love linux haha.

---

### Post by steveneddy on 2007-06-18
If you highlight a CLI command with your mouse and then go to the terminal, click the middle mouse button, the scroll wheel, it will paste it there for you so you don't mis-type anything.

---

