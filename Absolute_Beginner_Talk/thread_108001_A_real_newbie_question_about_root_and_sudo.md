---
title: "A real newbie question about root and sudo"
date: 2005-12-24
forum: Absolute Beginner Talk
---

### Post by brummieman on 2005-12-24
Well here we go a real newbie question.

Other Linux distros I used had a root user and I found this a simple way to administer my system and unlike many I didn't use it as my default login.

However, I now realise with this distro, the root is disabled and instead we have the Sudo command for CLI and the run as different user on the GUI.

So far so simple, until I came to run the file Browser as root (as I wanted to put the macromedia flash plugin manually into the plugin directory).

Now the stupid part.....I can't drag the file browser into the CLI line on the 'run as different user' dialogue, and neither can I track down the executable location and name from the menu (in my XP I would do a properties on the icon).  How do i get it to run file browser, and in future, how do I track down the path and executable I need in the dialogue to run it as root.

I am trying this as my last attempt (after searching the help and forum) before I do the most terrible of sins and re-enable the root :eek:

---

### Post by brummieman on 2005-12-24
Aha partly answered my own question....

I created a link on the desktop and got the command from the launcher tab.... :p 

however....there must be a more elegant method than this ???

---

### Post by Zimmer on 2005-12-24
You are better off using the Terminal commands to copy the plugin to the directory using sudo, 
and not trying to run the file browser (I will assume you mean Nautilus) AS root.
There is a method I use for 'opening' files and folders as root From the Nautilus, which I found on these forums, but can't remember where (good job I saved the info in a text file..)
and there are useful tips to be found...
[http://ubuntuguide.squarecows.com/doku.php](http://ubuntuguide.squarecows.com/doku.php)
[http://ubuntuguide.org/index.html](http://ubuntuguide.org/index.html)
[http://makuchaku.info/amnesty/](http://makuchaku.info/amnesty/)
..
9.13. 	
How do I open files as root user via right click?
   1.
gedit $HOME/.gnome2/nautilus-scripts/Open\ as\ root
   2.
      Insert the following lines into the new file

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gnome-sudo "gnome-open $uri" &
done

   3.
     Save the edited file (sample/Open-as-root_openfilesasrootviarightclick)
   4.
chmod +x $HOME/.gnome2/nautilus-scripts/Open\ as\ root
   5.
      Right click on the file and Scripts->Open as root

Have a read here, while I find the really GOOD links for you..

[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

Zimmer

---

### Post by Zimmer on 2005-12-24
regards

 Zimmer

[http://www.ubuntuforums.org/search.php](http://www.ubuntuforums.org/search.php)
[https://wiki.ubuntu.com/FindPage](https://wiki.ubuntu.com/FindPage)
[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
[http://doc.gwos.org/](http://doc.gwos.org/)

---

### Post by Mustard on 2005-12-24
I've just noticed that Zimmer has posted some good links above, but I thought I would post this anyway.

Installing flash for mozilla is described in this this wiki article.
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

