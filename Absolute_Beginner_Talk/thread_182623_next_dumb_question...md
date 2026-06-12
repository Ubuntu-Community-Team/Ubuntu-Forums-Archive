---
title: "next dumb question.."
date: 2006-05-26
forum: Absolute Beginner Talk
---

### Post by edwardzafra on 2006-05-26
When you install apps..errmm..where does it go? i im sure i successfully installed Gtkpod but i cant see it anywhere.

---

### Post by KingBahamut on 2006-05-26
Provides from [http://packages.ubuntu.com](http://packages.ubuntu.com) 

usr/bin/gtkpod						    sound/gtkpod [universe]
usr/share/applications/gtkpod.desktop			    sound/gtkpod [universe]
usr/share/doc/gtkpod/NEWS.Debian.gz			    sound/gtkpod [universe]
usr/share/doc/gtkpod/README.gz				    sound/gtkpod [universe]
usr/share/doc/gtkpod/changelog.Debian.gz		    sound/gtkpod [universe]
usr/share/doc/gtkpod/changelog.gz			    sound/gtkpod [universe]
usr/share/doc/gtkpod/copyright				    sound/gtkpod [universe]
usr/share/gtkpod/gtkpod.glade				    sound/gtkpod [universe]
usr/share/gtkpod/gtkpod.gladep				    sound/gtkpod [universe]
usr/share/gtkpod/pixmaps/gtkpod-add-dirs.png		    sound/gtkpod [universe]
usr/share/gtkpod/pixmaps/gtkpod-add-files.png		    sound/gtkpod [universe]
usr/share/gtkpod/pixmaps/gtkpod-add-playlists.png	    sound/gtkpod [universe]
usr/share/gtkpod/pixmaps/gtkpod-icon-32.png		    sound/gtkpod [universe]
usr/share/gtkpod/pixmaps/gtkpod-icon-32x32-2.png	    sound/gtkpod [universe]
usr/share/gtkpod/pixmaps/gtkpod-icon-32x32.png		    sound/gtkpod [uni

---

### Post by badrinarayan on 2006-05-26
Sometimes apps don't create a menu entry. You can run then from a terminal (just type gtkpod in terminal) or create a launcher yourself by right clicking on the application menu and choosing "Edit Menus". 

However if you installed gtkpod correctly, it should be in the "Sound & Video" section.

---

### Post by NikoC on 2006-05-26
Well, I'm not an expert myself but i'm guessing this might do the trick, in a terminal type:

sudo updatedb
locate gtkpod

first command updates database with the location of all files on your HD, second one gives you an idea where Gtkpod is located

edit: didn't notice the other replies, sorry ;)

---

### Post by meng on 2006-05-26
Where are you looking for it? In the menu? That's just a list of links/shortcuts anyway. Some things don't automatically add menu selections, in which case get yourself a menu editor (like smeg) and experiment. Otherwise you could try "killall gnome-panel" from a terminal and see if the menu items refresh - I must admit this has never done the trick for me.

---

### Post by edwardzafra on 2006-05-26
thank you...

Now i got the Synaptic Manager almost in my head....HOw do you install from CD?

---

### Post by badrinarayan on 2006-05-26
[QUOTE=edwardzafra]thank you...

Now i got the Synaptic Manager almost in my head....HOw do you install from CD?[/QUOTE]
What do you want to install from CD? Can you be a little clearer?

---

### Post by joshrobinson on 2006-05-26
[QUOTE=badrinarayan]What do you want to install from CD? Can you be a little clearer?[/QUOTE]

the cd should have its self as a repository in synaptic.. some things install off of it unless there is a new version out on the internet portion of the repository

if you dont have fast internet, im assuming you can remove the internet repository's and just install what you can from the cd.. although its limited

---

### Post by mostwanted on 2006-05-26
In Windows, applications usually put all of their files in one specific folder, in Linux they usually go in separate folders based on what type of files they are. For example libraries in one dir (/usr/lib), translation files go in another (not sure if this is an Ubuntu-specific practice), icons and images in a third (/usr/share), executables binaries in a fourth (/usr/bin).

The reason this differs is because UNIX traditionally used absolute paths for everything, while Windows typically uses relative paths (everything needed in one dir). Which one you think makes more sense, is up to you. The Linux way saves space for libraries and every program will always know where the other ones are located on the harddisk.

---

### Post by Lord Illidan on 2006-05-26
[quote=joshrobinson]the cd should have its self as a repository in synaptic.. some things install off of it unless there is a new version out on the internet portion of the repository

if you dont have fast internet, im assuming you can remove the internet repository's and just install what you can from the cd.. although its limited[/quote] 
TOO limited... And also very out of date. Why would you want to install from CD?


WAIT... Do you want to install UBUNTU from CD?

---

