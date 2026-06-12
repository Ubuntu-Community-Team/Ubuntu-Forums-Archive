---
title: "Installing Packages?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by GSF1200S on 2007-03-29
This is an embarrasing question, although it may not be as simple as I think it will be.

Despite all the stuff Ive accomplished on Ubuntu, I still dont know one simple thing- how the hell do I install a program that Ive downloaded for Linux from a website (frostwire for instance) that is sitting on a desktop??? I can extract the package, I can look at all the files in the folder, but I cant figure out how to simply install it. I think im having a hangover from Windows stupidity.

So far, Ive simply installed everything using the terminal or the package manager.. Thanks for any help...

---

### Post by mcduck on 2007-03-29
If it's a .deb package you should be able to install it just by clicking the package on your desktop, or by running 'sudo dpkg -i ~/Desktop/yourpackage.deb'

For other kinds of packages things are more complex, but you might want to read this: [How to install ANYTHING in Ubuntu]("http://cutlersoftware.com/ubuntuinstall/")

---

### Post by ziggykg on 2007-03-29
Asking is the only way of knowing ;) 

If it's a .deb file you can install it like this:

sudo dpkg -i my-app.deb

If you've downloaded a .tar.gz file, it most like will have an install script to install it.  After uncompressing and untarring the file (e.g. tar xvzf my-app.tar.gz) look for a README file or an INSTALL file which should contain info on installing the file.

If you've had to download an rpm file (coz of no .deb or even a .tar.gz app available), you can use a program called 'alien' to convert it to a .deb then install the .deb file using 'dpkg'.

Hope this helps.

---

### Post by GSF1200S on 2007-03-29
> **ziggykg said:**
> Asking is the only way of knowing ;) 

If it's a .deb file you can install it like this:

sudo dpkg -i my-app.deb

If you've downloaded a .tar.gz file, it most like will have an install script to install it.  After uncompressing and untarring the file (e.g. tar xvzf my-app.tar.gz) look for a README file or an INSTALL file which should contain info on installing the file.

If you've had to download an rpm file (coz of no .deb or even a .tar.gz app available), you can use a program called 'alien' to convert it to a .deb then install the .deb file using 'dpkg'.

Hope this helps.

The one im trying to install is a .tar.gz file. So let me try to get this... 

I have to uncompress, and then open a terminal. In the terminal I write:
tar xvzf frostwire.tar.gz  (in this case, frostwire is the program)

Then ill be able to find an install readme? I can already open the uncompressed folder, so I guess im uncertain what "tarring" is...

the .deb package sounds easy enough, as a simple command installs it. The .tar.gz is a little confusing though... Im looking at the page linked above right now to try and learn more...

---

### Post by STREETURCHINE on 2007-03-29
here is a link to a good howto to install frostwire.


[http://www.ubuntuforums.org/showthread.php?t=305337&highlight=how+to+install+frostwire](http://www.ubuntuforums.org/showthread.php?t=305337&highlight=how+to+install+frostwire)

---

### Post by Xoanan on 2007-03-29
> **GSF1200S said:**
> The one im trying to install is a .tar.gz file. So let me try to get this... 

I have to uncompress, and then open a terminal. In the terminal I write:
tar xvzf frostwire.tar.gz  (in this case, frostwire is the program)

Then ill be able to find an install readme? I can already open the uncompressed folder, so I guess im uncertain what "tarring" is...

the .deb package sounds easy enough, as a simple command installs it. The .tar.gz is a little confusing though... Im looking at the page linked above right now to try and learn more...

To quote the book I bought a few years back, "The linux tar command creates a single file that contains data from several files¨

It doesn't really compress any files per se;  it just puts files together.   Sometimes, tarring data can be useful for backing up data as well. 
There is a similarity with .zip files in that you have to extract the contents

---

### Post by viergeame on 2007-03-29
> **mcduck said:**
> If it's a .deb package you should be able to install it just by clicking the package on your desktop, or by running 'sudo dpkg -i ~/Desktop/yourpackage.deb'

For other kinds of packages things are more complex, but you might want to read this: [How to install ANYTHING in Ubuntu]("http://cutlersoftware.com/ubuntuinstall/")

This link says that the instructions are for Dapper with GNOME.  I run Edgy using xfce sometimes and KDE, I don't really like GNOME at all.  I have heard some people say that there are major differences.  Are the differences so major that I can't use that guide at all?

---

### Post by mcduck on 2007-03-29
> **viergeame said:**
> This link says that the instructions are for Dapper with GNOME.  I run Edgy using xfce sometimes and KDE, I don't really like GNOME at all.  I have heard some people say that there are major differences.  Are the differences so major that I can't use that guide at all?

Most of the stuff is same, you might not have the same graphical tools (because you use KDE) and some tools might look slightly different (because of the different version), but in the end it's still the same Ubuntu and most of the things work the same way. And everything done from command line (like compiling programs that come in .tar.gz packages) works in the same way.

Only difference between Ubuntu and Kubuntu is the desktop environment and default graphical applications installed.

---

### Post by viergeame on 2007-03-29
> **mcduck said:**
> Most of the stuff is same, you might not have the same graphical tools (because you use KDE) and some tools might look slightly different (because of the different version), but in the end it's still the same Ubuntu and most of the things work the same way. And everything done from command line (like compiling programs that come in .tar.gz packages) works in the same way.

Only difference between Ubuntu and Kubuntu is the desktop environment and default graphical applications installed.

You make it sound so much more logical than I was thinking about it.  I'm not sure why I was making it so complicated in my mind.  It's great to know now though.   There have been a few times that I spent extra time searching for different guides for things because I was confused on this.

---

