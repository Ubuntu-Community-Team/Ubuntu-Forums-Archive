---
title: "[SOLVED] Adding programs (IE4linux for example) to &amp;quot;Applications&amp;quot; menu"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by mahasmb on 2007-08-25
I'm really stuck on this, even though I think it should be very easy to figure out.

I've installed IE6 with IES4Linux. It works fine. Just, I can't get it installed under Application menu. 
I can only open the program after finding the file through Nautilus.

I can't open it with the Terminal, and I can't get it to work when I add it under the Applications menu.

This is what I'm entering in the Launcher Properties dialog box when I try to add it to the menus.

Type: Application
Name: IES4Linux
Command: ie6

What am I doing wrong?

I also had the same problem with the latest version of Azureus. So i installed the (older) version in the repos, but I'd really rather have the latest version.

---

### Post by wolfen69 on 2007-08-25
did you try going to system>preferences>main menu? that's how ive added things to the menu.

---

### Post by rkrug on 2007-08-25
Open the terminal and type ```
alacarte
```

There are options to add/remove things to the menu.

---

### Post by mahasmb on 2007-08-26
Yes, I was able to access that Menu editor before I started this thread... I just didn't write in the details properly. In any case, I tinkered with it some more and have finally been able to figure it out.

For Azureus I have
> 
Type: Application
Name: Azureus3
Command: /home/maha/.azureus/azureus

Initially, I just had
> 
Type: Application
Name: Azureus
Command: azureus

And for IE4Linux, I now have
> 
Type: Application
Name: IE4Linux
Command: /home/maha/bin/ie6 

When before I had:
> Type: Application
Name: IES4Linux
Command: ie6

I thought that in "Command:" I just had to write whatever I would in any terminal.

Still learning here ^^;

Thanks for the help.

---

