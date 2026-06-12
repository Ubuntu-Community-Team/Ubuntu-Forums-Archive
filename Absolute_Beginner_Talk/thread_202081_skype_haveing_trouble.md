---
title: "skype haveing trouble"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by Blade1357 on 2006-06-22
haveing trouble installing skype on system anny helpfull hints?

---

### Post by rado_london on 2006-06-22
Hi and welcome. Can you tell us what is the problem like. Do you end up with a message? Be more specific so we can help you.

---

### Post by Blade1357 on 2006-06-22
i have done all of this 
wget -c [http://download.skype.com/linux/skype_staticQT-1.2.0.18.tar.bz2](http://download.skype.com/linux/skype_staticQT-1.2.0.18.tar.bz2)
sudo tar jxvf skype_staticQT-1.2.0.18.tar.bz2 -C /opt/
sudo ln -s /opt/skype-1.2.0.18/skype /usr/bin/skype
sudo cp /opt/skype-1.2.0.18/skype.desktop /usr/share/applications/skype.desktop
sudo cp /opt/skype-1.2.0.18/icons/skype_32_32.png /usr/share/icons/hicolor/32x32/apps/skype.png
rm skype_staticQT-1.2.0.18.tar.bz2
 in the ternmal but it seems not to be working

---

### Post by rado_london on 2006-06-22
That isnt real installing. Why dont you got to [www.skype.com](www.skype.com) and get a official deb file. Then double click it and you are done.

---

### Post by Blade1357 on 2006-06-22
thanks i try that

---

### Post by Blade1357 on 2006-06-22
well i have downloaded the file an i still cant get it to insall need help gives err unknown directory

---

### Post by rado_london on 2006-06-22
OK assuming you have the deb. Open Terminal. Then type the following
```
sudo dpkg -i /path/to/the/file.deb
```
Then fill your password and you are done. If something is wrong post the output of the above command.

---

### Post by Blade1357 on 2006-06-22
dpkg: error processing /path/to/the/file.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /path/to/the/file.de
that wht it gave me

---

### Post by Drakkor on 2006-06-22
Get automatix: [http://www.getautomatix.com/index.php?option=com_content&task=view&id=4&Itemid=23](http://www.getautomatix.com/index.php?option=com_content&task=view&id=4&Itemid=23)

---

### Post by rado_london on 2006-06-22
[QUOTE=Blade1357]dpkg: error processing /path/to/the/file.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /path/to/the/file.deb
that wht it gave me[/QUOTE]
Change the  /path/to/the/file.deb with the actual path and the file name of the skype package.

---

### Post by Blade1357 on 2006-06-22
i can not figer out file directory i have it on my destop but i can figer out the file directory i am such a nooob

---

### Post by rado_london on 2006-06-22
[QUOTE=Blade1357]i can not figer out file directory i have it on my destop but i can figer out the file directory i am such a nooob[/QUOTE]
No one was born with knolwedge. To figure out the path I need your username and the exact skype package name. Then I will be able to tell you the exact command.

---

### Post by Blade1357 on 2006-06-22
user name is blade an the excat name of the package is skype_1.2.0.18-2_i386.deb

---

### Post by rado_london on 2006-06-22
[QUOTE=Blade1357]user name is blade an the excat name of the package is skype_1.2.0.18-2_i386.deb[/QUOTE]
So the command should be:
```
sudo dpkg -i /home/blade/Desktop/skype_1.2.0.18-2_i386.deb
```

Post the result mate!

---

### Post by Blade1357 on 2006-06-22
dpkg: dependency problems prevent configuration of skype:
 skype depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing
 well now i got this error ?

---

### Post by rado_london on 2006-06-23
[QUOTE=Blade1357]dpkg: dependency problems prevent configuration of skype:
 skype depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing
 well now i got this error ?[/QUOTE]
The skype package is probably broken. Now you have to do it the hard way. I will show you the steps as much as I can.
First go to [www.skype.com](www.skype.com) and download the RPM package for mandrake/mandriva.
Save it to the desktop and rename it to skype.rpm.
Now go to the terminal and do:
```
sudo apt-get install alien
sudo alien /home/blade/Desktop/skype.rpm
sudo dpkg -i /home/blade/Desktop/skype.deb
```
This should work, if not go to synaptic package manager and search for libstdc++5. Good luck.

---

