---
title: "Where do i put my script?"
date: 2005-11-02
forum: Absolute Beginner Talk
---

### Post by Tiger__Style on 2005-11-02
I have just written a very simple script and I have a question. Where do I have to put my script to be able to run it by just typing it's name in Konsole; I want others to be able to run it without having to know where it is?

Thanks.

---

### Post by 23meg on 2005-11-02
Add this command to your .bash_profile file

```
export PATH=$PATH:dir 
```

replacing "dir" with the location of your script. This will put it to your path, so that you can execute it from anywhere by typing "./script_name". 

You can also create aliases to recall often used commands. More about that here: [http://linuxcommand.org/wss0020.php#aliases](http://linuxcommand.org/wss0020.php#aliases)

---

### Post by frodon on 2005-11-02
You have to put it in /usr/bin, or you can create a bin directory in your home directory and add this line in your .bashrc file, so all the scripts in your personnal bin directory are known everywhere : ```
export PATH=~/bin:$PATH
```

---

### Post by wylfing on 2005-11-02
I think these responses need some clarification.

1. If you want to run your own scripts, and you don't care if anyone else on the system can run them, then make a directory under your home called [FONT="Courier New"][COLOR="DimGray"]bin[/COLOR][/FONT], put your script in there, and use the export command frodon gave. 

2. Putting the export command in .bashrc will be fine as long as you run your scripts from a terminal. In other words, if you make a desktop launcher, you should specify the full path to the script.

3. If you want all the other users on the system to be able to run your scripts, putting them in a common directory is a shortest path to making this happen. HOWEVER, putting your scripts into /usr/bin is a **very bad idea**. It is far safer and a much better practice to use /usr/local/bin instead.

(The really "right" way to do this would be to set things up properly with group priveleges so that other users can run your personal scripts, but that is getting fairly complicated.)

---

### Post by LHZ on 2005-11-02
[QUOTE=wylfing]3. If you want all the other users on the system to be able to run your scripts, putting them in a common directory is a shortest path to making this happen. HOWEVER, putting your scripts into /usr/bin is a **very bad idea**. It is far safer and a much better practice to use /usr/local/bin instead.[/QUOTE]
 What exactly is the difference between /usr/bin and /usr/local/bin ?

---

### Post by wylfing on 2005-11-02
From a user's perspective, there's no difference. Putting scripts in either place will allow users to run them by typing the script name from the command line.

From a system administration standpoint, however, there's a ton of difference. The /usr/bin directory is, on a system that manages everything with packages like Ubuntu does, necessarily a place that is managed *by the package maintainers*. If I write an application to calculate pi to the 90th digit, and make a package for it, and the package wants to install a Perl script called do-calc into /usr/bin, I should be able to look at the state of the repositories and find out whether any other package is going to put a file called do-calc into /usr/bin, and thereby avoid any conflict.

But if users are putting their private stuff into /usr/bin, the package mainainers lose the ability to successfully manage their packages. Furthermore, the machine itself can become a wreck when users start pasting scripts into /usr/bin that are named the same as someone's packaged files.

Now, /usr/local/bin is more or less safe from these worries. That's the point of the "local" bit -- it's for stuff you, the local administrator, are doing on your machine. It doesn't involve anyone else.

Here's an example: If you want to run Firefox builds that you download from the Mozilla web site, you should install them into /usr/local. The official Ubuntu Firefox packages won't try to put their binaries there (or, at least, if they did, the package maintainers should be poked in the eye). This way, you can have your local code and your managed code all happily living together.

Make sense?

---

### Post by Tiger__Style on 2005-11-02
Thank you guys for all your help :)

One more thing i need to ask. I have a script that brings up a graphical menu in Konsole, xterm or wherever I run it from. Like the old MS-DOS menus where you use the arrow keys and ENTER-button. The menu has 2 options; Konsole and xterm. When I select Konsole or xterm I want the one I chose to run another script I have. I have tried konsole -scriptname, konsole scriptname, xterm scriptname, and a bunch of other commands. Does anyone have a clue what the commands are?

Thanks again

---

### Post by LHZ on 2005-11-02
[QUOTE=wylfing]Make sense?[/QUOTE]
Makes a lot of sense, thanks for the excellent explanation!

---

