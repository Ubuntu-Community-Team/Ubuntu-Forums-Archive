---
title: "Adding fonts"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by niceguy123 on 2007-09-11
Can someone please explain how to add new fonts and get them to work in openoffice. Thanks,

---

### Post by Perfect Storm on 2007-09-11
make a folder called **.fonts** then put your font types there. Done.

---

### Post by hyper_ch on 2007-09-11
or if you want to make them available to all users, put the TTFs into this folder:

/usr/share/fonts/truetype

---

### Post by niceguy123 on 2007-09-11
> **hyper_ch said:**
> or if you want to make them available to all users, put the TTFs into this folder:

/usr/share/fonts/truetype

Thanks,

What does it mean, telling me that I am not the owner so can't write to the folder?

aside for that I see that in the /usr/share/fonts/truetype[ folder each font is in its own folder should I make one for each new one I'd like to insert?

---

### Post by Steve1961 on 2007-09-11
> **niceguy123 said:**
> Thanks,

What does it mean, telling me that I am not the owner so can't write to the folder?

aside for that I see that in the /usr/share/fonts/truetype[ folder each font is in its own folder should I make one for each new one I'd like to insert?

You need root privileges to write to that folder.  You can open nautilus in super user mode by typing gksudo nautilus.  However It's much easier to just drop the fonts into ~/.fonts unless there are multiple users on the system.

---

### Post by stchman on 2007-09-11
> **niceguy123 said:**
> Can someone please explain how to add new fonts and get them to work in openoffice. Thanks,

Use my procedure:

[http://www.stchman.com/install_fonts.html](http://www.stchman.com/install_fonts.html)

---

### Post by niceguy123 on 2007-09-11
> **stchman said:**
> Use my procedure:

[http://www.stchman.com/install_fonts.html](http://www.stchman.com/install_fonts.html)

Can you please explain this:  > Next open a terminal in the folder  

How is the terminal related to specific folders?

---

### Post by Perfect Storm on 2007-09-11
not really, I think it means you change directory in CLI

---

### Post by stchman on 2007-09-11
> **niceguy123 said:**
> Can you please explain this:   

How is the terminal related to specific folders?

Install a package called nautilus-open-terminal.  After that you will be able to open a terminal in that folder by right clicking in that folder.

```
sudo apt-get install nautilus-open-terminal
```

---

### Post by niceguy123 on 2007-09-11
> **stchman said:**
> Install a package called nautilus-open-terminal.  After that you will be able to open a terminal in that folder by right clicking in that folder.

```
sudo apt-get install nautilus-open-terminal
```

I ran that but got no change, still see gray "create new folder" in /usr/share/fonts

Also it seems that the fonts in  /usr/share/fonts/truetype are not showing up in open office.

---

### Post by stchman on 2007-09-12
> **niceguy123 said:**
> I ran that but got no change, still see gray "create new folder" in /usr/share/fonts

Also it seems that the fonts in  /usr/share/fonts/truetype are not showing up in open office.

Ok, if you now right mouse click in a Nautilus window you will have a new menu item called Open in Terminal.

The reason the the Create New Folder is greyed out is that folder is owned by root.  You will need to either do this:

sudo nautilus (then navigate your way there)

or 

sudo mkdir /usr/share/fonts/<name of folder you wish to create> (in a terminal)

I recommend the terminal way as it is less likely you will delete something you need.

---

### Post by skyjacker on 2007-09-12
Hello Niceguy123.
This worked for me. 

The easiest way to install a truetype font is to press alt-F2 and enter the following code (this will open nautilus in the right directory):

gksu nautilus /usr/share/fonts/truetype

Then create a new directory, name the directory whatever you like (choose a name that you remember if you ever need to backup your fonts personal fonts). Copy the fonts into that directory and finally rebuild the font information files by pressing alt-F2, mark 'run in terminal' so you can see the progress and entering the following code:

sudo fc-cache -f -v

<!> Note: After you install a new font, you will need to make sure that programs in which you want to use the new fonts can recognize them. In most cases this is done by closing and reopening the programs; however, some programs may require you to log out and log back in.
try it if you choose to. Don't give up tho...:)

---

