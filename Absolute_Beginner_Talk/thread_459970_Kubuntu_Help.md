---
title: "Kubuntu Help"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by jrandolph on 2007-05-31
I have been using Ubuntu Edgy for a while now and I wanted to try Kubuntu Feisty and I am having troubles installing software on there that I have previously installed on my Ubuntu

is there something different that I need to do with a tar.gz file in Kubuntu??

Any help will be greatly appreciated

---

### Post by plcdfa on 2007-05-31
What troubles do you have concretely? If you try to compile a program designed for gnome than make sure you also have the gome lib packages installed. Otherwise the process should be the same.

---

### Post by jrandolph on 2007-05-31
[http://ubuntuforums.org/showthread.php?t=383427](http://ubuntuforums.org/showthread.php?t=383427)

This was my original post when I was trying to install this program in Ubuntu and I did exactly as I was told and it worked without a hitch -- but now it does not work

---

### Post by plcdfa on 2007-05-31
Ok, but what error message do you get now?

---

### Post by jrandolph on 2007-05-31
dpkg: dependency problems prevent configuration of tn5250:
 tn5250 depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
dpkg: error processing tn5250 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tn5250


That is what it is telling me
I dont know where I can find that -libssl0.9.6

---

### Post by plcdfa on 2007-05-31
hmm, searching for it in synaptic doesn't come up with anything?
Try just libssl without the version number, a newer version could do the trick as well.

---

### Post by jrandolph on 2007-05-31
I did not have to have this when I installed it within Ubuntu

Shall I search for that in adept manager????

---

### Post by plcdfa on 2007-05-31
Probably because this package is installed by default with ubuntu, but not in Kubuntu. (So it might be a Gnome related package. I'm not sure though, I'm not writing from my home Kubuntu box.) So try searching for a package with name like lbssl in adept (or use synaptic - I still prefer that) and if you find one install it.

---

### Post by jrandolph on 2007-05-31
so i found that but it was a different version -- installed that and it still tells me that it needs it?

I am so confused right now

---

### Post by jrandolph on 2007-05-31
Bump

Anyone? Anything?

---

### Post by plcdfa on 2007-05-31
Be patient please, I need time to get home. ;)Could you give me a link to this source package you have the problem with? I'll try to compile it on my own Kubuntu box.

---

### Post by jrandolph on 2007-05-31
[http://www.mochasoft.dk/tn5250linux.htm](http://www.mochasoft.dk/tn5250linux.htm)

That is the package from the website

---

### Post by plcdfa on 2007-05-31
My internet connection was down all night, but tomorrow I'll try it.

---

### Post by plcdfa on 2007-06-01
I thought the whole time it's a source package that needs compiling, and you didn't correct me. :) It's binary only tough. It runs flawlessly on my Kubuntu system, so it surely can be done. According to the readme it needs gtk1.2 and gdk1.2. To be sure install these packeges:
libgdk-pixbuf2
libgtk1.2
libgtk1.2-common
libgtk2.0-0
libgtk2.0-bin
libgtk2.0-common
I have these installed and the program ran without any other setup. After installing the packages just untar the compressed file to a directory in your home dir, and run 
```
sudo bash ./Install-sh
```
in it.
Then you can run the program by typing tn5250 at the terminal.

---

### Post by jrandolph on 2007-06-01
Is there a way to make a graphical icon to launch this program for my desktop?

---

### Post by lbriner on 2007-06-01
Right-click the K menu button and select "Menu Editor" this brings up the editor window. Select the location in the menu you want to place your new shortcut and click the "New Item" button at the top (or File->New Item). You can enter the relevant information on the right hand side and File->Quit when finished.

---

### Post by lbriner on 2007-06-01
Sorry, should have read the previous post properly! 
To place a shortcut on the desktop, right click the desktop and choose "Create New->Link to Application" fill in the details - name, command etc and then "OK" to finish. Easy as that!

---

### Post by jrandolph on 2007-06-04
Works perfectly 

Thanks oh so much

If it wasnt for people like you I would never have been able to switch from MS Windows

---

### Post by plcdfa on 2007-06-04
Don't mention it. And never hesitate to turn to the community with your Linux difficulties. :)

---

