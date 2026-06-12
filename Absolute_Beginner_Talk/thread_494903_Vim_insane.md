---
title: "Vim insane"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by desijays on 2007-07-07
i have a problem using vim properly. whenever im using vim, im not able to see whether im in insert mode or in command mode. usually at my uni, it says in which mode i am at the bottom. but here in feisty fawn, vim doesn't say anything. i have to find out by trial and error to know in which mode i am in.

and when i press the backspace key in vim, it functions like the left arrow key. doesn't delete the character. it just directs the cursor to the previous character. Im having to press the 'delete' key in order to delete a character. Sometimes even the 'delete' key doesn't work properly. sometimes it deletes the prior char from the cursor and sometimes deletes the current char.

And the biggest problem im facing is with the 4 arrow keys in insert mode.

When i press the left arrow key it outputs 'D'
If i press the right arrow key it outputs 'C'
And for the down arrow key it outputs 'B'
And for up arrow key it outputs 'A'

could someone help me with this. Im using vim version 7.0.164.

---

### Post by PilotJLR on 2007-07-07
Try this:
```

sudo apt-get install vim-full

```

---

### Post by desijays on 2007-07-07
how do i uninstall the vim already in my system. if i install vim-full won't the already installed vim be in conflict with the new one?

and on the same note, i've been trying to do the following, but i can't get a definite answer.

Im using the command line and have been trying to figure out the,

Command to view the list of all the packages i have installed on my system?

Command to view the dependencies for a particular package?

Command to uninstall a particular package along with its dependencies? In other words, command to take the system back to the state before the package was installed..

Command to view location where a particular package is installed on my system? If it involves more than one file, then location of all those files too?

Command to search for a particular package in the repositories specified in the sources.list file?

Command to see some kind of description for a package.

Im not sure about this one though. Is there a command, where; if i specified the name of a package, i would get back in stdout the names of all the other packages that depend on it.

thanks

---

### Post by PilotJLR on 2007-07-07
You're thinking too hard into this.  :-)
If you run the command I gave, apt-get will take care of "upgrading" your vi to vim-full.

The answer to all of your other questions lies in the apt-get and apt-cache tools, provided you are using Feisty 7.04.
Good info here too: [https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)

---

### Post by desijays on 2007-07-07
i guess i was thinking too hard :)

Thanks for the link..
That should help

---

### Post by biker-dude on 2007-07-07
You might also try using emacs, thus using keychords rather than entering and exiting cumbersome modes. Emacs can be started inside a terminal with the following command:

emacs -nw

Note: the -nw options stands for "no window"

---

### Post by andrew.46 on 2007-07-12
Hi,

 Just create a ~/.vimrc file and these bizarre signs will go,

                Andrew

---

### Post by ushills on 2007-07-12
I had problems editing config files with vim but now use

```
gksudo gedit /etc/blah
```

instead, is there a special reason to use vim, I find gedit much easier.

---

### Post by Tomshaq on 2007-07-12
Hmmm... I know there is a line you can add in your .vimrc that actually controls the display for command/insert mode. 

EDIT: command is :set showmode

As far as the arrow keys,  check your keyboard mapping. btw, is it ABCD or ^A,^B,^C, and ^D?

---

### Post by baghdadi13 on 2008-03-16
You need only to create  an empty    .vimrc   file in your home directory
It works for me all the time :)

---

