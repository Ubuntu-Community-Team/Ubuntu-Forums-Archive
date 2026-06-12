---
title: "Error while copying"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by cheezit on 2006-02-20
Error while copying to  "/media/cdrom0"

You do not have permissions to write to this folder.

I would like to know how to enable permissions for this folder - and hopefully any other folder where this message pops up:-k 

Thank you

Randy

---

### Post by el3ktro on 2006-02-20
Ehm how do you want to copy files to your CD-ROM? Do you want to burn a CD? Or burn an ISO? That won't work this way, you need a burning program for this to work!

Tom

---

### Post by cheezit on 2006-02-20
Tom

I want to burn data to a CD.  You are right I do not have a program.  Any suggestions would be appreciated.  My computer (linux os) is not connected to the internet: I have been downloading to ms windows; burning, and trying to install a few simple programs and modem driver(s) (to Ubuntu) with no success.

I began to copy my terminal failure messages to a text file so I could get help installing modem drivers.  Since I am the newest newbie on the block, I would be pleased if you could give me a burning program source, and baby steps to the finish-line.

Randy

---

### Post by el3ktro on 2006-02-20
Well luckily, Gnome has a burning app built-in. Go to "Places->Home folder" and then click on "Go to->CD/DVD burner". You'll have an empty file manager window then. Open a second file manager window (Places->Home folder) and drop the files you want to burn into the empty window. The empty window has a toolbar button to write the CD. If you want to burn an ISO, right-click on it and select "Burn to CD".

P.S: I don't know the exact English menu names, my desktop is in German, but I hope you'll still find them :-)

Tom

---

### Post by cheezit on 2006-02-20
Tom

Thank you very much the CD burning help.  Now that I have that in place.  I downloaded and tried to install Conesxant's modem driver.  This is what I did:

These are Conexant's instructions:  

* Download the installation program (cnxtinstall.run)
* Open a terminal window. (If you don't know how to do this, press ALT-F2 and in the dialog box      that will appear, try entering one of the following commands: xterm or konsole or gnome-terminal)
* Use the cd command to access the directory where the cnxtinstall.run file was downloaded.
* Finally, enter the sh cnxtinstall.run command to run the installer.

I copied the file from my CD to Desktop then...

root@ubuntu:/home/randy# bash install cnxtinstall.run
/usr/bin/install: /usr/bin/install: [COLOR="Red"]cannot execute binary file[/COLOR]
root@ubuntu:/home/randy#

Randy

---

### Post by BoyOfDestiny on 2006-02-21
[QUOTE=cheezit]Tom

Thank you very much the CD burning help.  Now that I have that in place.  I downloaded and tried to install Conesxant's modem driver.  This is what I did:

These are Conexant's instructions:  

* Download the installation program (cnxtinstall.run)
* Open a terminal window. (If you don't know how to do this, press ALT-F2 and in the dialog box      that will appear, try entering one of the following commands: xterm or konsole or gnome-terminal)
* Use the cd command to access the directory where the cnxtinstall.run file was downloaded.
* Finally, enter the sh cnxtinstall.run command to run the installer.

I copied the file from my CD to Desktop then...

root@ubuntu:/home/randy# bash install cnxtinstall.run
/usr/bin/install: /usr/bin/install: [COLOR="Red"]cannot execute binary file[/COLOR]
root@ubuntu:/home/randy#

Randy[/QUOTE]

sudo chmod u+x cnxtinstall.run

./cnxtinstall.run

Does that do the trick?

---

### Post by cheezit on 2006-02-21
Tom

I have a copy of this file in 2 places: one is on a CD and the other is on my Ubuntu Desktop.  


sudo chmod u+x cnxtinstall.run
chmod: cannot access 'cnxtinstall.run": no such file or directory

./cnxtinstall.run
bash: ./cnxtinstall.run: No such file or directory

Randy

---

### Post by el3ktro on 2006-02-21
You have to cd (change dir) into the directory where you downloaded the file. You said you have the file on your desktop, so open a Terminal and type this:

cd Desktop
sudo chmod u+x cnxtinstall.run
./cnxtinstall.run

A note about the second command: "chmod" is used to change the permissions of a file. Other than in Windows, executable files are not magically executable, you have to set the "execute" permission first. This is done with the chmod command. The "u+x" means that the user which this file belongs - you - should be allowed to eXecute this file.

The third command tells the shell to execute the command in the current directory, thats why you have to put a ./ in front of it.


Tom

---

### Post by cheezit on 2006-02-24
Tom

Thank you for your excellent instruction, I was able to install "cnxtinstall.run. Unfortunately this program did not contain the drivers needed to get my modem working. (It is a web installer tool)

I went back to the website and dowloaded the necessary driver and placed the .deb file on my Desktop and...:

randy@ubuntu:~/Desktop$ sudo chmod u+x hsfmodem_7.43.00.01full_k2.6_12.9_386_ubuntu_i386.deb
randy@ubuntu:~/Desktop$ ./hsfmodem_7.43.00.01full_k2.6_12.9_386_ubuntu_i386.deb
./hsfmodem_7.43.00.01full_k2.6_12.9_386_ubuntu_i386.deb: [COLOR="Red"]line 1: syntax error near unexpected token `newline'[/COLOR]
./hsfmodem_7.43.00.01full_k2.6_12.9_386_ubuntu_i386.deb: line 1: [COLOR="Red"]`!<arch>'[/COLOR]

I think a "dpkg" suggestion came up after a few tries (I really can't say how since it has been a few days).  So I tried this:

roo@ubuntu:/home/randy/Desktop# dpkg hsfmodem_7.43.00.01full_k2.6_12.9_386_ubuntu_i386.deb
deb: [COLOR="Red"]neeed an action option[/COLOR].


Randy

---

### Post by el3ktro on 2006-02-24
Deb files have to be installed with the "dpkg" tool. Any action that alter the system - as installing drivers - ALWAYS have to be executed as root, so first of all you have to put "sudo" in front of it. The correct syntac for dpkg is "dpkg -i", the "-i" option stands for "install", thats what you want to do right ;-) ?

Tom

---

### Post by cheezit on 2006-02-24
Tom,

Thanks again for information put to good use.  You are very skilled at articulating the "how and why" of exactly what I needed.  I am on-line and downloading applications at this time.:D

Randy

---

