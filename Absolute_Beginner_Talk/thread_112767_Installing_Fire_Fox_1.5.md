---
title: "Installing Fire Fox 1.5"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by lex on 2006-01-05
I've been trying to install Fire Fox 1.5, following the instructions from here, "[COLOR="Magenta"]https://wiki.ubuntu.com/FirefoxNewVersion[/COLOR]". I've downloaded Fire Fox 1.5 from "[COLOR="Magenta"]Download [WWW] firefox-1.5.tar.gz from [WWW] mozilla.com[/COLOR] ", But I don't understand this part of the instructions "[COLOR="Blue"]and change to the directory you downloaded it to[/COLOR]", or this "[COLOR="Blue"]Install it to /opt/firefox:[/COLOR]" can anyone please explain it?
Thanks
Lex

---

### Post by byen on 2006-01-05
why not try Automatix
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

Firefox 1.5 is in the list and choose it during download if that is the only prog that you want.
Hope that helps.goodluck.

---

### Post by lex on 2006-01-05
[quote=byen]why not try Automatix
[http://ubuntuforums.org/showthread.php?t=66563]("http://ubuntuforums.org/showthread.php?t=66563")


I tried Automatix yesterday and it wouldn't work!!
I followed some instructions on how to fix it but i didn't know what the correct ip and ports where, "Replace proxy.yoyodyne.com:18023 with the correct ip and port numbers.
save and exit. now run automatix.". any suggestion on how to make this work as well?

---

### Post by byen on 2006-01-05
i really do not know where to take you from here as all i did was:
wget [http://beerorkid.com/automatix/automatix-ubuntu_4.3-1_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.3-1_i386.deb)
sudo dpkg -i automatix-ubuntu_4.3-1_i386.deb
and then ran automatix and it worked like a charm.. try posting your problem in that thread. Arneyboy is pretty dedicated to his project and might help you out.
Sorry. Hope you find a way.Goodluck.

---

### Post by lex on 2006-01-05
[QUOTE=byen].. try posting your problem in that thread. Arneyboy is pretty dedicated to his project and might help you out.
Sorry. Hope you find a way.Goodluck.[/QUOTE]


Thanks for your help.
I sent him a message yesterday, no reply as yet.
I may have stuffed something up along the way.

---

### Post by diggs on 2006-01-05
Why not try Opera? It's nicer, uses less resources and has a few more features.

---

### Post by byen on 2006-01-05
i stongly suggest opera too. its fast and pretty good. (just a suggestion)

---

### Post by lex on 2006-01-05
[QUOTE=diggs]Why not try Opera? It's nicer, uses less resources and has a few more features.[/QUOTE]

I just reinstalled ubuntu to try automatix again, (caus i dont know how to do anytihng else yet). so ill run that. Then ill try oprea, 
Thanks again.
Lex

---

### Post by lex on 2006-01-05
automatix still didnt work, mmm.
not sure what to do. Sounds like a great thing if i could get it to work.

---

### Post by kont.raen on 2006-01-05
[QUOTE=lex]I've been trying to install Fire Fox 1.5, following the instructions from here, "[COLOR="Magenta"]https://wiki.ubuntu.com/FirefoxNewVersion[/COLOR]". I've downloaded Fire Fox 1.5 from "[COLOR="Magenta"]Download [WWW] firefox-1.5.tar.gz from [WWW] mozilla.com[/COLOR] ", But I don't understand this part of the instructions "[COLOR="Blue"]and change to the directory you downloaded it to[/COLOR]", or this "[COLOR="Blue"]Install it to /opt/firefox:[/COLOR]" can anyone please explain it?
Thanks
Lex[/QUOTE]

Ok, here is how I have done it with several different linux distributions :

1. Download the archive from [www.mozilla.org](www.mozilla.org)
2. Open a terminal and extract the archive with the following commands :

cd $HOME
tar xvfz /path/to/the/downloaded/archive/firefox-1.5.tar.gz

This should extract Firefox 1.5 to a directory called firefox, residing in your home-directory.

3. change into this directory and start-up firefox with the following commands :

cd firefox
./firefox

If everything went fine, Firefox 1.5 should come up and you're ready to use it.  Make sure though to have libstdc++5 (easy to accomplish, using synaptics) installed as firefox will not start on Breezy if you have'nt - iirc.

4. Create a user-defined starter-button on the panel of your choice and label it Firefox 1.5, setting the entry for the command option like this :

/home/your-username/firefox/firefox

Okay - hope I did not forget anything important and this does the trick for you.

---

### Post by TeeAhr1 on 2006-01-05
That's exactly what I did, it worked like a charm and seemed much simpler than the virtual linking described in the wiki.  Two things I would add:

1. Once you're sure that Firefox 1.5 is up and running, change the launchers in your panel and Applications menu to point to the new version.  Like so:
   a. For the panel launcher, just right-click on it, select "properties."  You will see a line called "command."  Change this to "/path/to/firefox/firefox", and close.  Click on it and open up Firefox just to be sure it works.  If it doesn't, there's a typo in your path.
   b. For the Applications menu launcher go Applications > System Tools > Applications Menu Editor.  In the menu editor, click "Internet" on the right side.  A list of your internet applications comes up on the left.  Right-click Firefox and follow the steps above.

2. (this is important) **Do not remove the old version of Firefox, or your computer will explode!**  Okay, not really.  But removing Firefox will break a ton of other things (yeah, I just dealt with this, can you tell?), and is generally a Bad Thing.

Happy browsing!  -p.

---

### Post by R3linquish3r on 2006-01-05
i used your way kont, when i went to install it i got this error:

> ed@ubuntu:~$ cd /home/ed/firefox
ed@ubuntu:~/firefox$ sudo ./firefox

(firefox-bin:11237): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:11237): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:11237): Gdk-WARNING **: cannot set locale modifiers

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(firefox-bin:11237): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:11237): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:11237): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:11237): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:11237): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:11237): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:11237): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:11237): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:11237): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:11237): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:11237): Pango-WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(firefox-bin:11237): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
Warning: locale not supported by Xlib, locale set to C
Warning: X locale modifiers not supported, using default
./run-mozilla.sh: line 131: 11237 Aborted                 "$prog" ${1+"$@"}

---

### Post by hen3rz on 2006-01-05
> /path/to/the/downloaded/archive/firefox-1.5.tar.gz

how do i find out what the path is to the file??? I have the archive on my desktop what path is that?????

---

### Post by R3linquish3r on 2006-01-05
can anyone answer my prob?

---

### Post by TeeAhr1 on 2006-01-05
[QUOTE=hen3rz]how do i find out what the path is to the file??? I have the archive on my desktop what path is that?????[/QUOTE]
The path will be /home/*your-user-name*/Desktop/firefox-1.5.tar.gz

---

### Post by TeeAhr1 on 2006-01-05
[QUOTE=R3linquish3r]can anyone answer my prob?[/QUOTE]
I hope so.  Couple of questions:
1. Do you have libstdc++5 installed?  If you're not sure, go to System > Administration > Synaptic Package Manager, press ctrl-f, and enter libstdc++5.  Five entries come up.  If the first one does not have a green box, install it.
2. When you got the error, was it before, after, or during this command:
*tar xvfz /path/to/the/downloaded/archive/firefox-1.5.tar.gz*

---

### Post by lex on 2006-01-06
[QUOTE=kont.raen]Ok, here is how I have done it with several different linux distributions :

1. Download the archive from [www.mozilla.org](www.mozilla.org)
2. Open a terminal and extract the archive with the following commands :

cd $HOME
tar xvfz /path/to/the/downloaded/archive/firefox-1.5.tar.gz

This should extract Firefox 1.5 to a directory called firefox, residing in your home-directory.

3. change into this directory and start-up firefox with the following commands :

cd firefox
./firefox

If everything went fine, Firefox 1.5 should come up and you're ready to use it.  Make sure though to have libstdc++5 (easy to accomplish, using synaptics) installed as firefox will not start on Breezy if you have'nt - iirc.

4. Create a user-defined starter-button on the panel of your choice and label it Firefox 1.5, setting the entry for the command option like this :

/home/your-username/firefox/firefox

Okay - hope I did not forget anything important and this does the trick for you.[/QUOTE]



HI kont.raen, thanks for your advice.
I opened a terminal and copied and pasted the commands. this is what happened.
"lex@ubuntu:~$ cd $HOME
lex@ubuntu:~$ tar xvfz /path/to/the/downloaded/archive/firefox-1.5.tar.gz
tar: /path/to/the/downloaded/archive/firefox-1.5.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
lex@ubuntu:~$"
I couldn't paste it as one command. i tried writing it as one also but that didn't  work. I entered them one line at a time also, no joy.
Where should firefox have downloaded to? desktop? i moved.
I also tried moving it to home file and tried the commands.
No joy.
Any ideas?
Thanks
Lex

---

### Post by lex on 2006-01-06
Do I need to reboot after installing libstdc++5?

---

### Post by Qrk on 2006-01-06
You shouldn't.

This is getting too confusing... my suggestion is to type in:

```
gksudo nautilus
```

and move the firefox tar.gz to either your /home or /opt directory.

You can make a folder labled firefox, and extract the tar.gz file in that folder my simply right clicking it. 

Then simply find the runfirefox file, (or better yet, read the readme) and double click. (Gnome gives you a dialog to run) If i remember correctly, the file is runfirefox.sh.

Once you run can firefox from that file, its a simple matter of changing your launchers around.

I did it by this method before 1.5 final was released and (quite honestly) can't understand why it became so complicated. Although, this is doing graphically what people have already said via command line. But I think everyone is more comfortable with point and click anyway. Command line is great for giving help because of cut and paste, but sometimes there is an easier, graphical way that isn't mentioned.

---

### Post by lex on 2006-01-06
[COLOR=Red]_**THANKS**_[/COLOR] everyone who offed suggestions. I finally got automatix to work (great program). I think learning Linux for me is a long process.  So now I have FF1.5 and Opera.
Anyway thanks again!!
Lex:smile:

---

### Post by kont.raen on 2006-01-06
[QUOTE=lex]HI kont.raen, thanks for your advice.
I opened a terminal and copied and pasted the commands. this is what happened.
"lex@ubuntu:~$ cd $HOME
lex@ubuntu:~$ tar xvfz /path/to/the/downloaded/archive/firefox-1.5.tar.gz
tar: /path/to/the/downloaded/archive/firefox-1.5.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
lex@ubuntu:~$"
I couldn't paste it as one command. i tried writing it as one also but that didn't  work. I entered them one line at a time also, no joy.
Where should firefox have downloaded to? desktop? i moved.
I also tried moving it to home file and tried the commands.
No joy.
Any ideas?
Thanks
Lex[/QUOTE]

Hello Lex,

my answer is pretty much what TeeAhr1 already posted before me :) The command

tar xvfz /path/to/the/downloaded/archive/firefox-1.5.tar.gz

was not meant to be taken literatly; you rather have to substitute the "/path/to/the/downloaded/archive/" part with the path to the place where the downloaded firefox archive is. So if e.g. the firefox archive is on your desktop and you are known to ubuntu as user lex, then the command would look as follows :

tar xvfz /home/lex/Desktop/firefox-1.5.tar.gz

Sorry, if I did not make myself clear on that point in my original posting.

---

