---
title: "Newbie Install question"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by willbur on 2007-01-24
I'd like to install the chess program Jose from here:

[http://jose-chess.sourceforge.net/index_download.html](http://jose-chess.sourceforge.net/index_download.html)

I get a jose-144-linux.zip file on my desktop after the download. The instructions on the website then say:

# Unpack the tar file into a directory of your choice, e.g. tar xzf jose-13-linux.tar.gz -C /usr/share/games

# Start jose with the script jose.sh

# Or start jose from the command line with java -jar jose.jar

Does the first command work with .deb files or do I need to modify it?

Must the install be to /usr/share/games, or can I put it anywhere?

can I miss out the 'script' stage?

Does 'java -jar jose.jar' complete the install or run the program?

How would I uninstall this program afterwards?

Many thanks in advance...

---

### Post by dbbolton on 2007-01-24
just right-click on the folder and click "extract here"

to run the program, you probably just need to do 'sh /path/to/jose.sh'

to uninstall, just delete the folder that you extracted from the zip.

---

### Post by jd65pl on 2007-01-24
If you downloaded from the website posted there is no .deb file included therefore you will need to run the .jar file or the .sh to use the program.

>  Does 'java -jar jose.jar' complete the install or run the program?

This will run the program, the other file jose.sh just checks to see if you have jre available. Running either will be fine provided you have jre.

---

### Post by willbur on 2007-01-24
Thanks very much! :D

---

### Post by willbur on 2007-01-24
Thanks, dbbolton. Could you please tell me how to move the unzipped folder from my desktop to /usr/share/games? I can't simply drag and drop of course, as I don't have the right permissions. Or can you think of a more appropriate place to put it?

---

### Post by jd65pl on 2007-01-24
Just putting the folder in your home directory should be fine. As another point to make a launcher for your desktop or menu do the following....

[LIST=1]
[*]Right Click the desktop
[*]Select create launcher
[*]Choose the type as file
[*]Browse for the file jose.sh[/LIST]

---

### Post by willbur on 2007-01-24
Thanks jd65pl, but you've lost me with the launcher info - sorry! I was planning on putting the folder somewhere sensible, and putting an appropriate entry in the applications menu of my GNOME desktop to run it. Could I pls ask you to explain?

Many thanks

---

### Post by jd65pl on 2007-01-24
There is no problem with it being in your home directory but if you insist it goes some where else do this.

```
mv -r /thefile/path /usr/share/games
```

You will need to run the command as root [sudo]

---

### Post by willbur on 2007-01-24
Update to my last post - I've put the unzipped folder into /home and created an application menu entry with 

java -jar jose.jar

in the command box. Nothing happens when i run it. I've tried putting the same into the run application (alt/F2) box with the same result. I've also tried jd65pl's launcher trick. No joy. Permissions? Sorry...

---

### Post by jd65pl on 2007-01-24
Do this command in the terminal and note the error messages, are you sure you have JRE installed?

```
java ~/jose/jose.jar
```or

```
~/jose/jose.sh
```

You will only be able to run the launcher if the application is able to run properly

---

### Post by willbur on 2007-01-24
If I run the text in the first box, I get:

Exception in thread "main" java.lang.NoClassDefFoundError: .home.willbur.jose.jose.jar
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: .home.willbur.jose.jose.jar not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)

---

### Post by willbur on 2007-01-24
Another update - java -version reports:

java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

and the jose instructions state JRE 1.4 or later is required. Is this any help?

---

### Post by willbur on 2007-01-24
Can anyone please help me with this? I can't face going back to xboard :wink:

Regards

---

