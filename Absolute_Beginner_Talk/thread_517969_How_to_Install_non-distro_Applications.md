---
title: "How to Install non-distro Applications?"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by bettyhills on 2007-08-05
I downloaded the most recent version Azureus3 to my Linux box, but how to install?  4 hours last night reading and trying, but still clueless.  I could not find out the l_ocation_ to place the software or how to tell Ubuntu where it is.

I extracted the Azureus tar by doubleclicking, but it did not ask me where to place it, so it sits in a Download directory.  Clicking on the extracted azureus script as instructed, does nothing.

Is there some way to import  into Synaptic Manager and do it from there?  

Must I uninstall the earlier (slow as death) version of Azureus first?

Or is there another simple way?

I will be grateful for step-by-step instructions.

---

### Post by felicity on 2007-08-05
I don't use Azureus, but these are the directions from their website:

1) Install JRE from [here]("http://java.sun.com/j2se/1.5.0/download.jsp").

2) Extract latest linux package (choice of GTK or Motif) from [here]("http://sourceforge.net/project/showfiles.php?group_id=84122")

    * To extract the program files from the package, type
          o tar xvjf Azureus_x.x.x.x_linux...tar.bz2
      where Azureus_x.x.x.x_linux...tar.bz2 is the name of the downloaded package. 

3) Change to the azureus directory and run ./azureus to start

    * cd azureus
    * ./azureus

If you get an error message, or want to configure the java exec path, just open the azureus script file with your favorite text editor and edit the given configuration options.

If Azureus does not show up after a minute, you can try starting it manually:

    * GTK:
          o java -cp swt.jar:swt-pi.jar:Azureus2.jar -Djava.library.path=./ org.gudy.azureus2.ui.swt.Main

    * Motif:
          o java -cp swt.jar:Azureus2.jar -Djava.library.path=./ org.gudy.azureus2.ui.swt.Main

4) Please give feedback, if any exceptions were thrown.

---

### Post by bettyhills on 2007-08-05
Been there, and tried that over and over again for **hour**s.  

I am presuming they want me to "run" from Terminal?
I cannot figure out how to CD to the 'azureus' directory... It is in a 'Download'" directory.

How do I change directories to get to it?  I understand the CD command, but CD **FROM** where TO where?  When I open Terminal, WHERE am I?

---

### Post by Nekiruhs on 2007-08-05
> **bettyhills said:**
> Been there, and tried that over and over again for **hour**s.  

I am presuming they want me to "run" from Terminal?
I cannot figure out how to CD to the 'azureus' directory... It is in a 'Download'" directory.

How do I change directories to get to it?  I understand the CD command, but CD **FROM** where TO where?  When I open Terminal, WHERE am I?
You're in your home directory. When you open the terminal you get an odd looking line, yours should look similar to mine```
nekiruhs@Ubuntu:~$ 

```
nekiruhs is my username
Ubuntu is the name of my computer
and the :~ tells me I'm in my home directory (~ just means your home)
$ means I'm running as a user, not root (Root's is #)
cd doesn't need a from, just a to.
cd ~/Downloads, to go to a folder named downloads in my home folder.

---

### Post by testube_babies on 2007-08-05
There is an installer binary for Azureus Vuze at [http://www.kde-apps.org/content/show.php/Vuze?content=60273](http://www.kde-apps.org/content/show.php/Vuze?content=60273)

Just extract the file and double-click on Vuze.bin to install.

---

### Post by talby on 2007-08-05
For an introduction to the terminal, check out [https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal") it should help out w/ the basics.  Any non-distro app will need some manual intervention.

There is a mini-linux-howto from azureus.sourceforge.net, but it's not specific.  Similiar to what felicity posted but mentions the SWT / eclipse environment to run it.

[quote="["How do I run Azureus on Linux?"@azureus.sourceforge.net](http://azureus.sourceforge.net/faq.php#1)"]To get Azureus to start on linux you need to download SWT.
Make sure you choose the right version, GTK or Motif (cf. PS).
Extract the contents of the zip file somewhere, then move all .jar files and .so files to the same directory as Azureus.jar.
Then run it with the following command line:

java -cp swt.jar:Azureus2.jar -Djava.library.path=. org.gudy.azureus2.ui.swt.Main

If you extracted SWT to another directory, change the paths in the command line accordingly.

If you would rather use .tar.gz2, it's this way : Azureus for Linux.

PS: are you experiencing GUI freezes? If you are running Azureus from eclipse, try without it. If not, try with SWT-Motif instead of GTK.[/quote]

So, here is my mini Azureus3 howto:   get the Eclipse SWT from [Here]("http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.2.2-200702121330/swt-3.2.2-gtk-linux-x86.zip")
Since I put all non-distro apps in /opt, just...
```
sudo su -
mkdir /opt/swt
cd /opt/swt
unzip /*download-dir-here*/swt-3.2.2-gtk-linux-x86.zip
```
Get the Azureus3 .jar file from [here]("http://azureus.sourceforge.net/download.php"), why not put that in /opt also ;)
```
sudo su -
mkdir /opt/Azureus3.0.1.6
cd /opt/Azureus3.0.1.6
chown *username:username* .
cp /download-dir-here/Azureus3.0.1.6.jar .
```
You'll need to chown it since it creates sub-dirs, and use your username in place of "username" :)
Oh don't forget java itself, enable [the extra repos]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") then
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
to copy the swt .jar and .so files to /opt/Azureus3.0.1.6 run this
```
sudo su -
cd /opt/Azureus3.0.1.6
find /opt/swt -name "*.jar" -exec cp {} . \;
find /opt/swt -name "*.so" -exec cp {} . \;
```
That should be it, we now have all pre-reqs :)
to test it run (as your standard user):
```
cd /opt/Azureus3.0.1.6
java -cp swt.jar:Azureus3.0.1.6.jar -Djava.library.path=. org.gudy.azureus2.ui.swt.Main
```
and it was working for me.  you should be able to run it by creating a script in /usr/local/bin with the above maybe /usr/local/bin/azureus3 should do it then create a custom launcher with that script so you can add to the toolbar.

hope this helps, cheers

---

