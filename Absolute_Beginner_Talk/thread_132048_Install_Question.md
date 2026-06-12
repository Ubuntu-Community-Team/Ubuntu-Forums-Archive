---
title: "Install Question"
date: 2006-02-17
forum: Absolute Beginner Talk
---

### Post by jasrog on 2006-02-17
How do I exactly do Ubantu Live? I have saved the ISO image to a Disc already...now what?

---

### Post by Harold P on 2006-02-17
You need to burn it to a bootable CD, then put it in your computer's CD drive. Reboot, and it should start the live version.

Make sure your computer is set to boot from the CD.

---

### Post by Rumor on 2006-02-17
First you need to burn the ISO to a CD *as an image.*

FOllow this HOWTO for info on, well, How to do that: [http://www.ubuntuforums.org/showthread.php?t=111589](http://www.ubuntuforums.org/showthread.php?t=111589)

Then reboot the computer with the CD in the drive. If your BIOS is set to boot from the CD, off you go.

---

### Post by aggiechemist on 2006-02-17
First off, I'm not sure if you mean you saved the actual iso to the disk or used the iso to burn the disc image. You can tell the difference by  just looking at the contents of the disc. You should see many files, not just one iso on it. If it just has one file, you need to burn differently. Look for options in your burner program about burning a "disc image" and that could fix that.

Step two is to make sure you have CDs in your boot procedure. When your computer first boots, get into your BIOS menu (you usually have to press F1 or delete oduring a splash screen or POST screen). Make sure that CD is listed as something to boot from and that it is listed before the hard drive.

If you have both of those, then all need is to pop in your live CD and start the computer and have fun.

If any of that was unclear, let me know and I can add more detail.

---

### Post by jasrog on 2006-02-17
I do only see one ISO image...I have Nero will that get me the burned boot disc I need?

---

### Post by aggiechemist on 2006-02-17
I have nero express on my windows system. When I start it up, I choose if I want to burn a data cd, audio cd, or "disc image or saved project." What you want is the image option and not the data option. Almost all burning programs have this option somewhere. Then I just have to pick what image file (.iso file) I want to use.

---

### Post by Ghetto_Smurf on 2006-02-17
yes. just choose to record from an image. in some neros it will only serch for .nrg files. you may have to choose to search for .iso's. do this only if you cant find the .iso in the directory. an better an easier choice is alchool 120% which i think the best image recorder for windows.

---

### Post by aysiu on 2006-02-17
[HowTo burn an ISO image with Nero in Windows](http://www.ubuntuforums.org/showthread.php?t=111589).

---

### Post by jasrog on 2006-02-17
Thank You Everyone!!! I got it..... can you import programs you had with windows to Ubuntu?

---

### Post by Brunellus on 2006-02-17
[QUOTE=jasrog]Thank You Everyone!!! I got it..... can you import programs you had with windows to Ubuntu?[/QUOTE]
In a word:  No.

In a few more words:  it is possible to emulate Windows using WINE (which implements Windows APIs on a Linux machine), but this is not always perfect.  It is preferable to use native Linux programs.

What programs did you need to run in Windows, and for what purposes?  We can help you find Linux-native (and, incidentally, Free/Libre!) alternatives to them.

---

### Post by jasrog on 2006-02-17
Programs I want to run would be Nero, dvd shrink, Virtuosa, Mcafee, Counterspy exc.... if software is compatible for Mac does that mean Ubuntu can run it?

---

### Post by Brunellus on 2006-02-17
[QUOTE=jasrog]Programs I want to run would be Nero, dvd shrink, Virtuosa, Mcafee, Counterspy exc.... if software is compatible for Mac does that mean Ubuntu can run it?[/QUOTE]
no.  Mac is a different operating system (two operating systems, actually...MacOS up to OS 9 is different from Mac OSX).  

Nero & DVD shrink:  NOt sure about DVD Shrink, but nero is easily taken care of.   Gnomebaker or K3b would replace nero quite well, and there are cd burning tools included in ubuntu by default.

McAffee & Counterspy:  not necessary.  If you are running your linux machine upstream on a network, and would like to deal with viruses before they propagate to the Windows computers on your network, then tehre's ClamAV.  Otherwise, there are no known Linux viruses in the wild.

---

### Post by jasrog on 2006-02-17
can you direct me to where I can see software available by download for Linux? Thanks.

---

### Post by %hMa@?b&lt;C on 2006-02-17
to download any software, just open terminal and type 
```
sudo apt-get install nameofprogram
```
to search for a piece of software to do a particular job type
```
sudo apt-cache search cd burner
```
cd burner can be replaced with online game, whatever.

---

### Post by Brunellus on 2006-02-17
[QUOTE=jasrog]can you direct me to where I can see software available by download for Linux? Thanks.[/QUOTE]
it doesn't really work like that, especially with Ubuntu (and the other Debian Daughter distributions).   Programs are "packaged" and then uploaded onto central repositories. you then install the program from the repositories--you will also, this way, be able to update all of these programs with a single click (or one command from the command-line).  


Jeffc's post, above, is a good example of how the system works.  On a fully-installed ubuntu system, there's a graphical tool, Synaptic, which allows you to do this from a graphical environment.  Quite handy.  


But if you want an idea as to exactly what's going on out there, have a look at sourceforge.com

Lots of free and open source programs....  Also try freshmeat.net.

But, again, program installation is *not* what you're used to in Windows.  I cannot stress this enough.

---

### Post by jasrog on 2006-02-17
Installing software requires more than inserting cd and installing? How do you do it then?

---

### Post by Rumor on 2006-02-17
I don't know if there is a "complete" list anywhere. You're talking over 16,000 packages for Ubuntu. Most any program that can run on Linux can be compiled and run in Ubuntu.

If you're looking for a list of "equivalents" for Linux of Windows programs, look here: 
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

---

### Post by Brunellus on 2006-02-17
[QUOTE=jasrog]Installing software requires more than inserting cd and installing? How do you do it then?[/QUOTE]
no, it doesn't involve inserting a CD at all in most cases.  you fire up your package manager (Synaptic), search for the software you want, mark it, click "apply changes"...and it installs.

For things that aren't in the package, there are a few other ways:

-Build it yourself from source code (not recommended for novices, and mostly not necessary)

- download packages (*.deb files) and installing them manually (equivalent to self-extracting install .exe files in Windows, but not really)

Commercial software for Linux often comes with its own installer.  In most cases, you go to the cd and execute the installation script.

---

### Post by Brunellus on 2006-02-17
[QUOTE=Rumor]I don't know if there is a "complete" list anywhere. You're talking over 16,000 packages for Ubuntu. Most any program that can run on Linux can be compiled and run in Ubuntu.

If you're looking for a list of "equivalents" for Linux of Windows programs, look here: 
[http://www.linuxrsp.ru/win-lin-soft/table-eng.html](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)[/QUOTE]
In fairness, quite a number of those packages aren't "programs" in the way a windows user thinks of them.  Shared libraries, kernels, drivers, etc...

---

### Post by Rumor on 2006-02-17
[QUOTE=jasrog]Installing software requires more than inserting cd and installing? How do you do it then?[/QUOTE]

Once you have Ubuntu installed, you can click on the upper left hand corner of the screen "Applications" to see all the programs it installs by default. Just about every task you'd normally use a computer for will have a program installed, Open Office, Several mulitmedia programs, Web Browser, Email, Etc. 

There is an option in that menu to install more programs. When you click it, you get quite an expanded list of stuff you can install simply by ticking the check box next to the program name.

If that's not enoguh for you, you can select System |Administration | Synaptic Package Manager from the menu and browse / search all 16,000 packages.

Installing software under Ubuntu is FAR, FAR easier than windows.

---

### Post by Rumor on 2006-02-17
[QUOTE=Brunellus]In fairness, quite a number of those packages aren't "programs" in the way a windows user thinks of them.  Shared libraries, kernels, drivers, etc...[/QUOTE]

You're right. Good point. :)

---

### Post by jasrog on 2006-02-17
I am going to begin my experimental Linux Run...Thank You Everyone for your feedback!

---

