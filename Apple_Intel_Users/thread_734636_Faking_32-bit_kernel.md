---
title: "Faking 32-bit kernel"
date: 2008-03-24
forum: Apple Intel Users
---

### Post by Mr. Pink on 2008-03-24
I installed the 64-bit version of Gutsy on my Macbook, and everything works great except I need to install Matlab, which is a 32 bit application (Student Version).  I would really rather have it in Linux rather than OS X since I use it a lot, so is there anyway to just get the computer to 'fake' a 32 bit kernel just to run the program?

---

### Post by cyberdork33 on 2008-03-24
> **Mr. Pink said:**
> I installed the 64-bit version of Gutsy on my Macbook, and everything works great except I need to install Matlab, which is a 32 bit application (Student Version).  I would really rather have it in Linux rather than OS X since I use it a lot, so is there anyway to just get the computer to 'fake' a 32 bit kernel just to run the program? You actually just need the 32 libraries, although I am unsure what all libraries matlab depends on... There is a utility called getlibs that might help though:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

Probably the best thing would be to find a guide on installing Matlab in a 64bit environment. 

If you aren't doing anything majorly advanced, you might checkout [FreeMat]("http://freemat.sourceforge.net/"). There are other Matlab clones too: [Octave]("http://www.gnu.org/software/octave/"), [Scilab]("http://www.scilab.org/"), [Rlab]("http://rlab.sourceforge.net/")

---

### Post by Mr. Pink on 2008-03-25
Ok I managed to install it using an old guide here:

[http://ubuntuforums.org/archive/index.php/t-90895.html](http://ubuntuforums.org/archive/index.php/t-90895.html)

I installed it using the -glnx86 switch and then had to link all of the folders to glnxa64 and it works quite well with a few exceptions:

1) The main window shows up and looks very similar to this:

[Main Screen]("http://www.udel.edu/CIS/106/iaydin/07F/labs/lab01_files/matlab.png")

except the "File edit.." menu line is not there, but I can click where they should be and navigate the menus and similarly with the toolbar immediately below it.

2) Similar problem for plot windows

3) nothing shows up for the editor window, it is just a big blank screen, but I can still click the non existent "File edit ..."

My main question is just: Would problems with java only make these certain parts not work or might I have missed linking an image library somewhere or...? 

Thanks again.

---

