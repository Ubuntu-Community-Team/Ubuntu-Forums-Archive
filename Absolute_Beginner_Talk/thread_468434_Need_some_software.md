---
title: "Need some software"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by mocqueanh on 2007-06-08
I need some software equvalent to Windows.
In Windows, i usually use Virtual CD to emu ISO file (for playing games without CD)
I want a software to burn CD such as Cyberlink Power2Go, also. In Ubuntu i know the command to make ISO file and burn CD (cdrecord), but it's not comfortable, a GUI software is better than command when i burn CD
And in Ubuntu, i cant read the CHM file, PDB file, what software can i use ?

---

### Post by pavpan on 2007-06-08
To mount ISOs use gISOmount (find it in synaptic)

To burn cds, you can use either the simple "CD/DVD Creator" option on your places menu (Not Kubuntu or Xubuntu) or (haven't tried it myself, the previous choice worked for me) the program Serpentine.

CHM Files are Microsoft help files, no idea why you want to use them, look around in google for some software if you really need it...
PDB: also some Microsoft file format for storing Visual C++ projects. Google it is all that I can tell you...

---

### Post by machoo02 on 2007-06-08
[Gnochm]("http://gnochm.sourceforge.net") is a CHM viewer for GNOME, [Kchmviewer]("http://www.kchmviewer.net/") does the same for KDE.  Both are available through the repositories.  For cd burning, I would highly recommend [K3B]("http://k3b.plainblack.com/"): it's so much better than any of the other burning software out there for linux.  It's Qt based, but don't let that stop you if you are using GNOME (I do, and it's worth it!).

---

### Post by ryanVickers on 2007-06-08
I would recommend K3B for burning and everything else like that, and Gmount-iso for mounting iso's (some of it's in french, some german, some english, but you'll figure it out!  there's only like 2 buttons, and the words are similar to english:))

---

### Post by kwacka on 2007-06-09
For pdb files try txt2pdbdoc:

'txt2pdbdoc -d file.pdb > file.txt'

will save it in the same directory as the command is issued as a standard text file

---

