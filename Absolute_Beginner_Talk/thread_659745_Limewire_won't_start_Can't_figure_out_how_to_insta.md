---
title: "Limewire won't start? Can't figure out how to install Java? This is for you!"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2008-01-06
[COLOR=Blue][B][COLOR=Red]This is the perfect thing for you if you want the EASIEST way EVER to install Java, or if Limewire/Frostwire won't start (if the cause is old Java)[/COLOR]
[COLOR=Black]
How to work this script:[/COLOR][/B]
[/COLOR][LIST]
[*]Download
[*]Extract
[*]Run
[*]Enter password when prompted
[*]Answer "yes" to Java license agreement
[*]DONE![/LIST]For a "live" demonstration of this script in action see below:
 
[COLOR=DarkGreen]I've attached a little [screen recording]("http://www.mediafire.com/?exxj2omtmeb") (7Mb, 1:20 minutes) to show how it works and prove that the file is clean.  I apologize for my large screen and the long wait in the middle as it downloads...[/COLOR]

---

### Post by bwtranch on 2008-01-06
Hmm kay. Might try it. Just for fun. Don't have it on this computer. Seems a little scary. But, here goes...

---

### Post by ryanVickers on 2008-01-06
just thought of something... you will have to make it executable before running it;)

---

### Post by Martje_001 on 2008-01-06
How can I check what it does? And why do you install Limewire? Frostwire will do!

---

### Post by ryanVickers on 2008-01-06
It doesn't install limewire... it just installs java, which it needs to run ;)

the code it somewhat a disaster and therefor rather embarrassing ;) so I locked it up so people can't read it, but I assure you I have tested it thoroughly and the gist pf what it does is - makes folder "/usr/java", downloads installer, installs to folder, removes installer. done.

---

### Post by c-m on 2008-01-10
wheni run it i get:

>  &#9228;&#9618;&#9148;&#9484;@&#9228;&#9618;&#9148;&#9484;-&#9229;&#9226;&#9149;&#9488;&#9500;&#9146;&#9147;:·$ &#8804;
&#9225;&#9618;&#9149;&#9252;: &#8804;: &#9228;&#9146;&#9492;&#9492;&#9618;&#9532;&#9229; &#9532;&#9146;&#9500; °&#9146;&#9508;&#9532;&#9229;
&#9228;&#9618;&#9148;&#9484;@&#9228;&#9618;&#9148;&#9484;-&#9229;&#9226;&#9149;&#9488;&#9500;&#9146;&#9147;:·$ &#9228;&#9500;&#9474;&#9524;
&#9225;&#9618;&#9149;&#9252;: &#9228;&#9500;&#9474;&#9524;: &#9228;&#9146;&#9492;&#9492;&#9618;&#9532;&#9229; &#9532;&#9146;&#9500; °&#9146;&#9508;&#9532;&#9229;
&#9228;&#9618;&#9148;&#9484;@&#9228;&#9618;&#9148;&#9484;-&#9229;&#9226;&#9149;&#9488;&#9500;&#9146;&#9147;:·$ 



---

### Post by ryanVickers on 2008-01-10
Are you sure its running and not just opening in the text editor? No mater how you run it, by clicking or in the terminal, it works for me, hence the video... 

did you get the one in the bz2 archive or the tar.bz2?  the bz2 one (old) needs you to make it executable yourself, the new one does not...

---

### Post by durand on 2008-02-03
In hardy here, frostwire won't start because of the java version but I have 1.6 installed:

```
durand@Carbon-14:~$ java -version
java version "1.6.0_04"
Java(TM) SE Runtime Environment (build 1.6.0_04-b12)
Java HotSpot(TM) Client VM (build 10.0-b19, mixed mode)
```
Any ideas? Thanks

---

### Post by ryanVickers on 2008-02-03
Hardy is still a work in progress, so I can't really say what's the problem, and there's a good chance it will be fixed before the final release.

This is only to install Java 1.5, and thus fix the problem of Frostwire not starting - [B]when the cause is old/non-existent Java.

[/B]Point is, I would love to help, but I don't know what's wrong; I would not be too upset about something not working in hardy because like I said, it's still in testing; it's not done yet.

---

### Post by rich.bradshaw on 2008-02-03
You shouldn't lock up code.

Why not show the source here so we can decide whether to trust it or not?

---

### Post by ryanVickers on 2008-02-03
Sure... It's just a real mess so I didn't want to have people seeing it :p
It also makes it easier to just have one binary - that way you don't have to worry about getting it to run vs. display in gedit.
```

#!/bin/bash
zenity --question --text "This will install the latest version of Java.\n\nContinue?"
until [ "$?" -eq "0" ]; do
zenity --error --text "Don't install it? OK, check out my other scripts instead! :)"
exit 0
done
zenity --info --text "You will need to run as root for this to work, possibly several times...\n\nPlease enter the root password below, or contact your system administer."
gksudo mkdir /usr/java
cd /usr/java
zenity --notification  --window-icon="/usr/share/icons/Human/24x24/actions/dialog-apply.png"  --text "create installation directory... [ OK ]" &
zenity --info --text "Now downloading Java... please wait (on high-speed, takes about 30 seconds or less)" &
gksudo wget http://javadl.sun.com/webapps/download/AutoDL?BundleId=12791
path=$(find "/usr/java" -name "jre-6u3-linux-i586.bin?*");
gksudo mv "$path" "/usr/java/jre-6u3-linux-i586.bin"
gksudo chmod a=rwx "/usr/java/jre-6u3-linux-i586.bin"
zenity --notification  --window-icon="/usr/share/icons/Human/24x24/actions/dialog-apply.png"  --text "download and configure installer... [ OK ]" &
zenity --info --text "beginning installation..." &
gksudo xterm "/usr/java/jre-6u3-linux-i586.bin"
zenity --notification  --window-icon="/usr/share/icons/Human/24x24/actions/dialog-apply.png"  --text "Java installer has quit... [ ?good/bad? ]" &
gksudo rm "/usr/java/jre-6u3-linux-i586.bin"
zenity --notification  --window-icon="/usr/share/icons/Human/24x24/actions/dialog-apply.png"  --text "clean up residual files... [ OK ]" &
zenity --info --text "Did everything go OK? If so, Java is now installed! :)"
exit 0

```

In addition, if you need proof it's good, I show a video recording of me using it (top of page), starting at the download on the page to the proof that frostwire now runs at the end.

---

