---
title: "Installing non-Ubuntu programs"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by sbussy89 on 2007-10-17
For some of my classes at school I have to install Matlab and Maple.  they both came in .tar.gz folders which i unzipped, and inside was a readme telling me to run a file called "install."  I double-clicked on it and it went through the entire install process successfully, but the program doesn't show up anywhere in any of the menus.  What's going on?

---

### Post by -grubby on 2007-10-17
you might have to start them from the terminal. Try typing there name "maple" and "matlab" and see what happens. You can also create a  launcher for them on the desktop by right clicking and hitting "create launcher"  under "command" type their name

---

### Post by Siph0n on 2007-10-17
try typing mat in a terminal and hit tab, to see if matlab or something comes up.... Or maybe map and a tab to see if a program called maple comes up... You could also use the find / -name maple to try and find where it is located? I probably have the exact syntax wrong, but u get the idea? :)

---

### Post by jw5801 on 2007-10-17
Yeah you'll need to run Matlab from the command line. Either through a terminal, or by hitting Alt+F2 and then typing matlab. You can also use the "whereis" command as opposed to find to work out where it's stored. ```
whereis matlab
```

---

### Post by sbussy89 on 2007-10-18
i couldnt get any of those to work... if i go to the terminal and type in "whereis matlab" it just puts out "mallab:" and gives me a new command line.  the same thing happens for maple.  if i just type the program name it says it doesnt exist... btw if i go into the list of known applications in "run application" it doesnt show anything related to either program, but im not sure then why it would say the install completed successfully if it didnt actually put the program on my pc

---

### Post by JacobSteelsmith on 2007-10-18
Normally, in Linux, you don't install a program by double clicking on a file. You have to open up a command prompt, and use cd to change to the directory. For example, if you have extracted the files to your desktop to a folder called example, type cd Desktop/example. You can also type the first letter and hit tab. If you have another folder that starts with an e, using this example, you will be presented with those choices. 

Once you are in the folder where the file marked install is in, try typing ./install into the command line (that's dot an forward slash).

---

### Post by alienexplorers on 2007-10-18
Go into synaptic and search for matlab.  If it finds it, you could look at the preferences and find out where it is installed.  I have had this way work with several programs I loaded that were not in the synaptic database. If you try to load envy from synaptic it won't find it.  Yet after you download it and run it, it is listed in synaptic.

---

### Post by jw5801 on 2007-10-18
Matlab doesn't install through synaptic. JacobSteelsmith's suggestion is a goodie. Try installing it via the commanline. If you double click on it it will probably run but if something goes wrong then we won't be able to see. So try running the install file via the commandline.

---

### Post by curtis1552 on 2007-10-18
Check for compatability:
[Maple OS Support]("http://www.maplesoft.com/support/faqs/platforms.aspx")
I didn't see anything on Matlab but you could still e-mail thier [support line]("http://www.mathworks.com/support/product/solutions.html?product=ML&type=Solution&category=1-15ERB&topic=Installation&productcategory=1-1478S&parentcategory=1-15ERB").

---

### Post by Sef on 2007-10-18
Read [How to Install Anything in Ubuntu]("http://www.monkeyblog.org/ubuntu/installing/").

---

### Post by jw5801 on 2007-10-18
[Matlab install guide](http://ubuntuforums.org/showthread.php?t=74708)

---

### Post by sbussy89 on 2007-10-18
is ubuntu red hat, suse, or mandrake? those are the only 32-bit os' listed in the link from curtis

---

### Post by jw5801 on 2007-10-18
Ubuntu is a Debian derivative. I'm VERY surprised that Debian at the least isn't listed there...
If you have a look [here](http://www.physics.drexel.edu/liki/index.php/Debian_Sysadmin) there's a section about halfway down the page on installing maple from CD. One would assume that whatever your school gave you would be the same contents as the CD so it should translate. Did you manage to get matlab installed via that howto?

---

