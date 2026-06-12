---
title: "How do I get a list of installed programs?"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-07-18
How do I get a list of installed programs?

Yes, I know about the Applications listing however this is only for program that have been add to the menu.

But there are other programs that have no entry in the list.
Example: nano

I found this program while trying to edit my fstab, it was used as an example editing program.

What other programs are available that I am not aware of because they are not listed in the Applications list?

I have done a search on the forums here but have yet to come up with anything.

---

### Post by moma on 2006-07-18
List installed (ii) programs (packages):
$ dpkg -l 

$ dpkg -l | less

$ dpkg -l | grep nano 

See also 
$ ls -l /usr/bin | less 

$ man dpkg 
-----------------------------------------------

Read also "Apt-get and dpkg guide..."
You'll find a link to it here 
[http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

---

### Post by geco on 2006-07-18
> **gargoyle said:**
> How do I get a list of installed programs?

Yes, I know about the Applications listing however this is only for program that have been add to the menu.

But there are other programs that have no entry in the list.
Example: nano

I found this program while trying to edit my fstab, it was used as an example editing program.

What other programs are available that I am not aware of because they are not listed in the Applications list?

I have done a search on the forums here but have yet to come up with anything.

use wildcards with dpkg, e.g.
```

dpkg -l *acpi*

```
will tell you all packages whose name contains acpi are installed.

otherwise you can do
```

dpkg --get-selections | grep PACKAGE_NAME

```

byebye

---

### Post by shof2k on 2006-07-18
The post [http://www.ubuntuforums.org/showthread.php?t=182201](http://www.ubuntuforums.org/showthread.php?t=182201) mentions a useful program.

---

### Post by gargoyle on 2006-07-18
I do not want to sound pick but none of the suggestions were really what I was looking for.
To moma.
> $ dpkg -l 
This produce a voluminous output. So much to be almost useless. That is unless I want to spend the rest of my life looking up which item did.
> $ dpkg -l | lessAbout the same but this time I was dropped in to some kind of program with no visible way out.
> $ dpkg -l | grep nano  This only good if I already knew which programs were loaded but I do not.
> $ man dpkg 
Again you need to know what you have.
To shof2k,
> The post [http://www.ubuntuforums.org/showthread.php?t=182201](http://www.ubuntuforums.org/showthread.php?t=182201) mentions a useful program.
I tried your suggestion and download what I though I needed only to find that I was apparently missing added pieces.

I know that Windows OS is no better in loading program that are not easily found. I am sure the program listed are useful but I would have thought program that might be useful for normal uses.
How many editing programs are needed?

Any other suggestions?

---

### Post by FuzZy2006 on 2006-07-18
One easy way is to use Synaptic and chose Installed. There's your complete list.

---

### Post by lucia_engel on 2006-07-18
> **gargoyle said:**
> 
About the same but this time I was dropped in to some kind of program with no visible way out.


FYI, you can press 'q' to quit "less".

---

### Post by Franks&amp;Beans on 2006-07-18
I agree. Is hard to remember what you have installed. What you want is the Debian Menu. This is one of the istallations that comes with Automatix. It lists all installed apps and is added to your applictions menu.

---

### Post by btarlinian on 2006-07-18
The suggestion of installing the debian menu is a good one.
Try sudo aptitude install debianx.

However, programs like nano will still not show up. That's because they only run in a terminal. They can't draw their own window. That way you can use them even if X (the program that creates windows on your screen) is broken.
Sometims however there is a gui equivalent for the terminal program. For example, "vim" is a common terminal text editor. To get a similar gui program install gvim. Vim will not show up in the menu, but gvim will.

Vim is already installed on your system. Open a terminal and type vim to run it. (Type ESC followed by :q! to exit.) However, if you type Alt-F2, which opens up a "Run Command" dialog box, and type vim in you will notice that nothing happens. That's because vim doesn't have a terminal to output text into. So if there was an appliction menu entry for it and you clicked on it, you wouldn't see anything. :)

Have fun with Ubuntu,

btarlinian

---

### Post by gargoyle on 2006-07-18
btarlinian said:
> The suggestion of installing the debian menu is a good one.
Try sudo aptitude install debianx.
I tried to install per you instruction but it said it could not find the package.

Is it include in Ubuntu?

btarlinian said:
> However, programs like nano will still not show up. That's because they only run in a terminal.

So I have bunch of these terminal only program loaded, but noway of knowing what they are because there is no list for them. 
Am I correct in this assumption ?

I would rather use graphic interface, I have gotten lazy in my old age and I have not use command line since I gave up DOS 6.0.

So the only programs with graphic interface are the ones located already in the Application list?

---

### Post by btarlinian on 2006-07-18
> **gargoyle said:**
> btarlinian said:

I tried to install per you instruction but it said it could not find the package.

Is it include in Ubuntu?
I'm sorry, try sudo aptitude install menu. (I think the package name changed in dapper.)

> **gargoyle said:**
> 
So I have bunch of these terminal only program loaded, but noway of knowing what they are because there is no list for them. 
Am I correct in this assumption ?

yes, there is no official *list*.


> **garoyle said:**
> 
I would rather use graphic interface, I have gotten lazy in my old age and I have not use command line since I gave up DOS 6.0.

Don't discount the command line to easily. You can do a lot of stuff much more easily in it. And bash (the linux shell) is definitely more powerful than DOS command prompt

> **gargoyle said:**
> 
So the only programs with graphic interface are the ones located already in the Application list?

Not necessarily, but all applications from main. (the ones in synaptic with a ubuntu logo next to them are there.)

To find all executables, i.e. stuff you can run, (sometimes one program consists of multiple execuatbles) on your linux installation, do this.

type $PATH in your installation.

See the colon separated list, type 
ls -l | grep "\-x" | grep -v "drw" >> /home/*your_username*/List_of executables.txt

in each directory that is a member of the list. 

In your home directory "List_of_executables.txt" will have a list of executables.

In any UNIX-like system, there isn't any native conception of a "program." Package managers can install packages, but one package is not necessarily a  program.

Here are some suggestions for finding stuff in synaptic.

If you're looking for stuff you've installed, ,mostly search the universe & multiverse sections in synaptic. Almost everything in main is already installed. (except for games, and the gnome/kde office sutie.)

There is a search function. If you know what you might be looking for, use the search feature!.

Don't hesitate to ask more if you have questions.

Have fun,

btarlinian

---

### Post by OU812 on 2006-07-20
I hope this will not be considered hijacking - can pkgtool be used to list installed packages?

john

---

