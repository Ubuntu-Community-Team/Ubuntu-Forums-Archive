---
title: "theme idiot over here..."
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by kbrown3074 on 2006-05-01
I am trying to install some new themes but im having problems.  I downloaded a couple TAR files.  I first tried dragging into theme manager, gave me invalid file format.  I then moved and extracted the files to (/usr/share/gdm/themes/) which gave me the resulting theme directories.  I then tried installing from the package manager...used the .xml file and nothing.  There is 1 that has an xml file, the other theme i have only contains jpgs and pngs.  Suggestions??

---

### Post by joshrobinson on 2006-05-01
[QUOTE=kbrown3074]I am trying to install some new themes but im having problems.  I downloaded a couple TAR files.  I first tried dragging into theme manager, gave me invalid file format.  I then moved and extracted the files to (/usr/share/gdm/themes/) which gave me the resulting theme directories.  I then tried installing from the package manager...used the .xml file and nothing.  There is 1 that has an xml file, the other theme i have only contains jpgs and pngs.  Suggestions??[/QUOTE]

did you try selecting the .tar file from theme manager? dont extract the .tar file

what is it a gdm/gnome theme?

click install theme then click the .tar

---

### Post by kbrown3074 on 2006-05-01
I tried selecting the tar file from the manager but it didnt work that way.  I tried selecting the tar file from the desktop and under the themes directory.  They are gdm themes that I am trying.  Could it be a file permission thing?

---

### Post by joshrobinson on 2006-05-01
[QUOTE=kbrown3074]I tried selecting the tar file from the manager but it didnt work that way.  I tried selecting the tar file from the desktop and under the themes directory.  They are gdm themes that I am trying.  Could it be a file permission thing?[/QUOTE]

when you opened the .tar from "install theme" in the theme manager, did it say any type of error. or did it say it installed fine and you just didnt see it pop up

is it a normal theme? or is it a clearlooks- ubunutu-looks theme?

---

### Post by kbrown3074 on 2006-05-01
It is a gdm theme, doesnt tell me anymore than that.  I downloaded them from gnome-looks.  The error I get each time is 'The File Format is Invalid'.  I would think this would be easy..but is a pain in the butt for me.

---

### Post by joshrobinson on 2006-05-01
[QUOTE=kbrown3074]It is a gdm theme, doesnt tell me anymore than that.  I downloaded them from gnome-looks.  The error I get each time is 'The File Format is Invalid'.  I would think this would be easy..but is a pain in the butt for me.[/QUOTE]

hmm.. the only thing i can think of is to make sure that clearlooks and ubuntulooks are installed

they are in synaptic package manager under the following names

gtk2-engines-clearlooks
gtk2-engines-ubuntulooks

also try a different theme if you still have problems, maybe it was packaged wrong?

---

### Post by kbrown3074 on 2006-05-01
i already had those 2 packages installed.  I've tried gdm and gtk themes..and neither have worked.  It looks like the files start to copy..then I get the invalid file error.  Is there a way i can repair gnome to see if it got messed up somewhere?

---

### Post by Perfect Storm on 2006-05-01
Have you tried my thread at [http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694) ?

---

### Post by mscman on 2006-05-01
If you're trying to install gdm themes, you'd probably have better luck trying to install them via the Login Screen Setup instead of the Themes preferences.  Just  a thought.

---

### Post by kbrown3074 on 2006-05-01
Did what it said in the instructions..nothing has worked  yet.  Always 'invalid file format'.

---

### Post by Bagnaj97 on 2006-05-01
[QUOTE=kbrown3074]Did what it said in the instructions..nothing has worked  yet.  Always 'invalid file format'.[/QUOTE]

For window border (metacity) and control (GTK2) themes that don't install using the theme manager you can extract them in their own folder in /home/your_username/.themes I had the same problem with the Snowish theme from [www.gnome-look.org](www.gnome-look.org)

---

