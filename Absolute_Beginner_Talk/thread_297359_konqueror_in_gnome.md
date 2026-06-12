---
title: "konqueror in gnome"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by dpan on 2006-11-11
How can I make konqueror my default file-manager on my gnome desktop? 

Can this be done?

---

### Post by ciscosurfer on 2006-11-11
Go to System > Preferences > Preferred Applications and set your Web browser to be konqueror instead of what's there already.  I know this isn't what you're asking for, but thought I'd throw it out there anyhow.

Nautilus is tightly integrated into Gnome.  I'm sure though you can do this by hacking the Places menu code.  I will look into this for you.

EDIT: After some thought, this can most probably be done through the configuration editor.  Hang on, I figure this one out!

EDIT: I'll keep tweaking, but here's where I would start:: Go into your Configuration Editor (or enter gconf-editor in a terminal) and go to /desktop/gnome/applications/main-menu/file_browser
mess with the settings there.  You can do a search for nautilus from within the editor--search for the entry in both titles and keys.  You can try to modify these keys that you find with konqueror.  Just try to remember which keys you mess with so you can revert if you need to!
Good luck!

EDIT: Definitely check here as well > /desktop/gnome/applications/main-menu/file-area/

---

### Post by aysiu on 2006-11-11
You might also want to try this: ```
sudo dpkg-divert --divert /usr/bin/nautilus.old --rename /usr/bin/nautilus
sudo ln -s /usr/bin/konqueror /usr/bin/nautilus
```

---

### Post by dpan on 2006-11-11
This app reminds me of regedit... I do not see anywhere to make I don't see anyway to change the default file-manager....

---

### Post by ciscosurfer on 2006-11-11
That's sneaky.   ;) 

I love it! \\:D/

Looks like it'll work...does it? :-k

Okay.  I'll try it out.  

At first glance, the command looks or seems counterintuitive/backwards.

Diverts nautilus to nautilus.old, links konqueror to nautilus...right?

Well done.

---

### Post by dpan on 2006-11-11
Ok how do I undo that .... my system just hangs

> **aysiu said:**
> You might also want to try this: ```
sudo dpkg-divert --divert /usr/bin/nautilus.old --rename /usr/bin/nautilus
sudo ln -s /usr/bin/konqueror /usr/bin/nautilus
```

---

### Post by ciscosurfer on 2006-11-11
Did I speak too soon?

---

### Post by aysiu on 2006-11-11
Bummer. This will undo the change: ```
sudo rm /usr/bin/nautilus
sudo dpkg-divert --rename --remove /usr/bin/nautilus
```

---

### Post by ciscosurfer on 2006-11-11
Were the --divert and --rename switches backwards?

---

### Post by dpan on 2006-11-11
Thanks that fixed it back...

any other ideals??

---

### Post by ciscosurfer on 2006-11-11
Couldn't he simply link the two up--the second part of the above comand--causing konqueror to load when nautilus is executed?

Reverse the line to look like this?```
sudo ln -s /usr/bin/nautilus /usr/bin/konqueror
```

Btw, Aysiu, while I've got your attention, and I know this is not the appropriate place to comment on it, but your Songbird scripts rocks!  Seriously.

---

### Post by aysiu on 2006-11-11
It looks as if in /etc/gnome/defaults.list, line #139 has ```
inode/directory=nautilus-folder-handler.desktop
``` and line #175 has ```
x-directory/normal=nautilus-folder-handler.desktop
``` Not sure what the appropriate konqueror*.desktop is... You can try just plain old ```
konqueror.desktop
``` Not sure if that'll work.

To ciscosurfer, this is actually not what we want: ```
sudo ln -s /usr/bin/nautilus /usr/bin/konqueror
``` That links Nautilus to Konqueror so that if you launch *konqueror*, Nautilus will launch instead. We want the reverse of that.

Glad you like the Songbird script.

---

### Post by ciscosurfer on 2006-11-11
I realized my goof after I hit Reply.  It's early in the morning and I'm a wee bit tired.  Thanks for clarifying though.

---

### Post by ciscosurfer on 2006-11-11
I've got a fix.  Not a total fix.  But a fix nonetheless.  This will set Home Folder under Places to open Konqueror.

Hit the key-combo of ALT-F2 and enter in **gksudo nautilus**--this will open nautilus with root permissions.  

Go to the **/usr/share/applications** directory, right-click the file called '**Home Folder**' and go to Properties.  

Click the Launcher tab and on the line where the command says **nautilus --no-desktop **replace it with **konqueror**.  

Close the root nautilus that you've opened.  Go to your Places menu at the upper-left of your screen, click it, and then open your Home Folder -- Konqueror will open up.

---

### Post by taddy_porter on 2006-11-26
Try this:

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

---

### Post by ciscosurfer on 2006-11-27
> **taddy_porter said:**
> Try this:

[http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)I wonder if aysiu has seen this ;)

---

### Post by aysiu on 2006-11-27
> **ciscosurfer said:**
> I wonder if aysiu has seen this ;)
Seen it?

I created that link based on this very thread and your discover, ciscosurfer.

---

### Post by ciscosurfer on 2006-11-27
> **aysiu said:**
> Seen it?

I created that link based on this very thread and your discover, ciscosurfer.I know. :D  I was being slightly playful and a little facetious.

---

### Post by aysiu on 2006-11-27
> **ciscosurfer said:**
> I know. :D  I was being slightly playful and a little facetious.
Ah, gotcha.

---

### Post by Kanji_Man on 2007-11-20
Sorry to dust off an old thread but I keep coming accross this when searching on the topic. I have been moderately successful linking my KDE and Gnome trash cans like so:

```
rm -rf ~/.local/share/Trash/files
rm -rf ~/.local/share/Trash/info
ln -s ~/.Trash ~/.local/share/Trash/files
ln -s ~/.Trash ~/.local/share/Trash/info
```

The above psychocats link works well for most of gnome but apparently not for the desktop drive icons.

---

### Post by re5et on 2007-12-16
i just attempted this in gutsy with some unfortunate results.  :(

I downloaded the script, used the commands provided to switch to konquerer, because after trying out KDE i found that i enjoyed it more than nautilus.  Once completed, konquerer was called instead of nautilus, however other functionality that i had before and expected to still have was no longer available, such as being able to access the network through the interface, seeing my desktop icons, being able to use the context menu on my desktop etc.

So then i attempted the restore method, and it looked to have worked, success message in the terminal, but then after restarting, nothing in my places menu would open at all, i tried going back to konquerer with the same result.

So now i am stuck with no file manager, and having limited knowledge of linux i am facing a reinstall :(

Just thought i would share my experience, and possibly give a word of warning to anyone else who might not be capable of helping themselves yet when something goes wrong](*,)

---

### Post by lswest on 2007-12-16
i have konquerer installed in my Ubuntu and it works no problem, installed it through kdebase, as i needed that pack to get kwifimanager working right.  should work for you.
```
 sudo apt-get install kdebase
```
you might be able to make it default under system-->preferences--> preferred applications

---

### Post by fatbuttlarry on 2007-12-24
The "nonautilusplease" is a great link!  Thanks!

I'm seeing some applications have Nautilus hard coded into them.  More specifically, 3rd party applets, such as Avant Window Navigator Trash Applet.

```

konqueror ~ &

```
View >> Show Hidden Files
Rename the folder ".Trash" to ".Trash_old"

I made a link pointing from ```
~/.Trash
``` to ```
~/.local/share/Trash/files
``` with the command ```
ln -s ~/.Trash ~/.local/share/Trash/files
``` but that just makes Nautilus open the KDE trash location.

I forced a link to overwrite Konqueror with Nautilus, but Nautilus doesn't append the correct backslash to the end of trash ("trash:" instead of "trash:/"), so I'll had to write a script to append it for me. :/

First backup your nautilus:
```

sudo mv /usr/bin/nautilus /usr/bin/nautilus.old

```

Then make a new one:
```

sudo gedit /usr/bin/nautilus

```
Alternately, you can use "kedit" or "kate" in the place of gedit.

Copy the following into the document:

```
#!/bin/sh
#
# /usr/bin/nautilus
#
# Avant Window Navigator Trash Aplet Hack for KDE
#
# Copyleft 2007 A. Tres Finocchiaro
#
# This script is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation

if [ "$1" = "trash:" ]; then
	exec konqueror "$@/"
else
	exec konqueror "$@"
fi

exit 0
```

Then give it execute permissions:
```

sudo chmod +x /usr/bin/nautilus

```

Now the Trash applet will work with KDE's Trash.
-Tres

---

### Post by Sonja on 2007-12-27
Thanks everyone! This is a useful thread.

---

### Post by The Devil Is A Squirrel on 2008-01-14
Thanks for this! One problem remains "Open Folder" & mounted devices working still with Nautilus. How can I change that?

---

### Post by galv on 2008-02-07
> **The Devil Is A Squirrel said:**
> Thanks for this! One problem remains "Open Folder" & mounted devices working still with Nautilus. How can I change that?

I would like to know that too

---

### Post by amoore on 2008-07-22
I used the script to replace Nautilus with Thunar. When I click on a folder on the desktop the file browser opens using Nautilus. When I use the places menu the file broser uses Thunar. Does any one know how a I can fix this so that Thunar is my only file browser.

---

