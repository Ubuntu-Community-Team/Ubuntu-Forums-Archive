---
title: "[SOLVED] Could not launch menu item"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by rahul_bhise on 2007-07-13
when i launch adobe reader from application>office>adobe reader
an error window shows up saying
> Could not launch menu item
Failed to execute child process "acroread" (Permission denied)

---

### Post by loserboy on 2007-07-13
does it say the same thing if you open a terminal and type: acroread

---

### Post by KIAaze on 2007-07-13
Please post the output of these commands:
```

which acroread
which acroread | xargs ls -l
which acroread | xargs ls -lH
cat /usr/share/applications/AdobeReader.desktop

```
Hopefully it's just a permission problem.
Did acroread work before?
Or did you have this problem directly after installation? How did you install Acrobat reader?

edit:
And yes, try running it from the terminal to see what error messages (if any) you get there.

---

### Post by rahul_bhise on 2007-07-13
> brahul@uhome:~$ acroread
bash: /usr/bin/acroread: Permission denied
brahul@uhome:~$ which acroread
brahul@uhome:~$ which acroread | xargs ls -l
total 12
drwxr-xr-x 5 brahul brahul 4096 2007-07-14 02:52 Desktop
drwxr-xr-x 8 brahul brahul 4096 2007-07-13 00:13 jre1.6.0_01
-rw-r--r-- 1 brahul brahul   85 2007-07-06 09:33 Unsaved Document 1
brahul@uhome:~$ which acroread | xargs ls -lH
total 12
drwxr-xr-x 5 brahul brahul 4096 2007-07-14 02:52 Desktop
drwxr-xr-x 8 brahul brahul 4096 2007-07-13 00:13 jre1.6.0_01
-rw-r--r-- 1 brahul brahul   85 2007-07-06 09:33 Unsaved Document 1
brahul@uhome:~$ cat /usr/share/applications/AdobeReader.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Adobe Reader
MimeType=application/pdf;application/vnd.fdf;application/vnd.adobe.pdx;application/vnd.adobe.xdp+xml;application/vnd.adobe.xfdf;
Exec=acroread 
Type=Application
DocPath=
GenericName=PDF Viewer
GenericName[da]=PDF-fremviser
GenericName[de]=PDF-Betrachter
GenericName[es]=Visor de documentos PDF
GenericName[fi]=PDF-Näyttäjä
GenericName[fr]=Afficheur PDF
GenericName[it]=Visualizzatore PDF
GenericName[ja]=PDF&#12499;&#12517;&#12540;&#12450;
GenericName[ko]=PDF &#48372;&#44592;
GenericName[nl]=PDF-weergaveprogramma
GenericName[nn]=PDF-lesar
GenericName[pt_BR]=Visualizador de arquivos PDF
GenericName[sv]=PDF-visare
GenericName[zh_CN]=PDF &#26597;&#30475;&#22120;
GenericName[zh_TW]=PDF &#27298;&#35222;&#31243;&#24335;
Terminal=false
Icon=AdobeReader.png
Caption=PDF Viewer
X-KDE-StartupNotify=false

Categories=Application;Office;Viewer;X-Red-Hat-Base;
Name[de]=Adobe Reader
Name[de]=Adobe Reader
Name[es]=Adobe Reader
Name[fi]=Adobe Reader
Name[fr]=Adobe Reader
Name[it]=Adobe Reader
Name[ja]=Adobe Reader
Name[ko]=Adobe Reader
Name[nl]=Adobe Reader
Name[nn]=Adobe Reader
Name[pt_BR]=Adobe Reader
Name[sv]=Adobe Reader
Name[zh_CN]=Adobe Reader
Name[zh_TW]=Adobe Reader
Name[nb_no]=Adobe Reader
GenericName[nb_no]=PDF-visning
InitialPreference=7
brahul@uhome:~$
output on my terminal

---

### Post by KIAaze on 2007-07-13
Ok, there seems to be a problem with the "which" command. It probably can't display the path to an executable for which you don't have permission.

These commands should list the permissions then:
```
ls -l /usr/bin/acroread
ls -lH /usr/bin/acroread
```

(Some info: The "-H" option is in case /usr/bin/acroread is just a link. That way the "ls" command will list the permissions for the real executable.)

If the problem is due to permissions, this might solve the problem:
```
sudo chmod 755 /usr/bin/acroread
```

---

### Post by rahul_bhise on 2007-07-13
> brahul@uhome:~$ ls -l /usr/bin/acroread
-rw-r--r-- 1 root root 0 2007-01-06 01:27 /usr/bin/acroread
brahul@uhome:~$ ls -lH /usr/bin/acroread
-rw-r--r-- 1 root root 0 2007-01-06 01:27 /usr/bin/acroread
brahul@uhome:~$ sudo chmod 755 /usr/bin/acroread
Password:
brahul@uhome:~$ 

i did that
now when i click application>office>adobe reader
nothing happens also the error window does not show up

---

### Post by KIAaze on 2007-07-13
The permissions were definitely wrong.
But now after the chmod command, if you run this again:
```
 ls -l /usr/bin/acroread
```

You should get "rwxr-xr-x".

What do you get now when you run acroread from the terminal?

---

### Post by rahul_bhise on 2007-07-13
brahul@uhome:~$ ls -l /usr/bin/acroread
-rwxr-xr-x 1 root root 0 2007-01-06 01:27 [COLOR="Lime"]/usr/bin/acroread[/COLOR]
brahul@uhome:~$ acroread
brahul@uhome:~$


but nothing happened

---

### Post by rahul_bhise on 2007-07-13
in synaptic when i searched rwxr-xr-x it shows libstat-lsmode-perl
do you mean this

---

### Post by rahul_bhise on 2007-07-13
i installed that to but nothing happened

---

### Post by KIAaze on 2007-07-13
No, "rwxr-xr-x" is a description of the permissions:
r=read
w=write
x=execute

first set=user
second set=group
third set=other

"user" and "group" are the two names that follow it.
"rwxr-xr-x root root" means that the user root has all permissions, all users belonging to the group root can read&execute, all others can read&execute.

--------------------
Back to the main problem now:
My guess would be that acroread is either wrongly installed or that it has some dependency problems.
Try reinstalling it.
All you need to do is download the linux installer from [http://www.adobe.com/products/acrobat/readstep2.html]("http://www.adobe.com/products/acrobat/readstep2.html")

There are two available. Choose the tar.gz.

_Installation of the tar.gz:_
Extract it and then double-click on INSTALL.
Choose "run in terminal" and follow the instructions.
When it asks for paths, just press enter and it will use the default values which should be ok.

---

### Post by KIAaze on 2007-07-13
_If it still doesn't work, try installing from the .rpm:_
Install alien:
```
sudo apt-get install alien
```
Convert the .rpm into a .deb:
```
sudo alien -k AdobeReader_enu-7.0.9-1.i386.rpm
```
Install the .deb:
```
sudo dpkg -i AdobeReader_enu-7.0.9-1.i386.deb
```

And if it still doesn't work, I'll have to do some research because I have no idea what the problem could be right now.
But remember that there are also Free Open-Source pdf viewers available like **evince** for example. ;)

edit:
Oops, I made a mistake previously I think. You'll need root privileges to install acroread, so it should be:
_Installation of the tar.gz:_
> cd <directory where you downloaded the tar.gz>
tar -xzvf AdobeReader_enu-7.0.9-1.i386.tar.gz
cd AdobeReader/
sudo ./INSTALL


---

### Post by rahul_bhise on 2007-07-14
> brahul@uhome:~$ cd Desktop
brahul@uhome:~/Desktop$ tar -xzvf AdobeReader_enu-7.0.9-1.i386.tar.gz
tar: AdobeReader_enu-7.0.9-1.i386.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
brahul@uhome:~/Desktop$ cd
brahul@uhome:~$ sudo alien -k AdobeReader_enu-7.0.9-1.i386.rpm
Password:
File "AdobeReader_enu-7.0.9-1.i386.rpm" not found.
brahul@uhome:~$ cd Desktop
brahul@uhome:~/Desktop$ sudo alien -k AdobeReader_enu-7.0.9-1.i386.rpm
Warning: Skipping conversion of scripts in package AdobeReader_enu: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
adobereader-enu_7.0.9-1_i386.deb generated
brahul@uhome:~/Desktop$ sudo dpkg -i AdobeReader_enu-7.0.9-1.i386.deb
dpkg: error processing AdobeReader_enu-7.0.9-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 AdobeReader_enu-7.0.9-1.i386.deb
brahul@uhome:~/Desktop$ tar -xzvf AdobeReader_enu-7.0.9-1.i386.tar.gz
tar: AdobeReader_enu-7.0.9-1.i386.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
brahul@uhome:~/Desktop$ cd AdobeReader/
bash: cd: AdobeReader/: No such file or directory
brahul@uhome:~/Desktop$ 
still same problem persist

---

### Post by KIAaze on 2007-07-14
Sorry if I didn't get the commands perfectly right so that they work for you.
Pay attention to the error messages you get. It helps. :)
> 
 brahul@uhome:~$ cd Desktop
brahul@uhome:~/Desktop$ tar -xzvf AdobeReader_enu-7.0.9-1.i386.tar.gz
tar: AdobeReader_enu-7.0.9-1.i386.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

[B]This means that the tar.gz isn't there, so obviously he can't extract it.
Type "ls" to see the available files in the directory where you are.
Are you sure you downloaded it to the desktop?
[/B]
brahul@uhome:~/Desktop$ cd
brahul@uhome:~$ sudo alien -k AdobeReader_enu-7.0.9-1.i386.rpm
Password:
File "AdobeReader_enu-7.0.9-1.i386.rpm" not found.
brahul@uhome:~$ cd Desktop
brahul@uhome:~/Desktop$ sudo alien -k AdobeReader_enu-7.0.9-1.i386.rpm
Warning: Skipping conversion of scripts in package AdobeReader_enu: postinst postrm
Warning: Use the --scripts parameter to include the scripts.
adobereader-enu_7.0.9-1_i386.deb generated

[B]Ok, with those warnings I guess it's a bad start already.
I think you might be more successful with the tar.gz package.
But you can still try the rpm one too of course.
[/B]
brahul@uhome:~/Desktop$ sudo dpkg -i AdobeReader_enu-7.0.9-1.i386.deb
dpkg: error processing AdobeReader_enu-7.0.9-1.i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
AdobeReader_enu-7.0.9-1.i386.deb

[B]As you can see the previous command said: "adobereader-enu_7.0.9-1_i386.deb generated"
So obviously you should run:
"sudo dpkg -i adobereader-enu_7.0.9-1_i386.deb"
instead of:
"sudo dpkg -i AdobeReader_enu-7.0.9-1.i386.deb"
[/B]
brahul@uhome:~/Desktop$ tar -xzvf AdobeReader_enu-7.0.9-1.i386.tar.gz
tar: AdobeReader_enu-7.0.9-1.i386.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

[B]Same thing as before:
File not found=>File not extracted [/B]

brahul@uhome:~/Desktop$ cd AdobeReader/
bash: cd: AdobeReader/: No such file or directory

**Since the contents of the tar.gz weren't extracted, there's no "AdobeReader/" directory to go into.**

brahul@uhome:~/Desktop$

I strongly suggest you read this: [https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")


_Now here's a new set of commands that will hopefully work this time:_

1)Download the tar.gz and the .rpm Adobe reader installers to your Desktop.

2)
```
cd ~/Desktop
tar -xzvf AdobeReader_enu-7.0.9-1.i386.tar.gz
cd AdobeReader/
sudo ./INSTALL
acroread

```
If it launches acrobat reader, all should be ok now.

3)If not:
```
cd ~/Desktop
sudo alien -k --scripts AdobeReader_enu-7.0.9-1.i386.rpm
sudo dpkg -i adobereader-enu_7.0.9-1_i386.deb
acroread

```

Note: Extracting contents of a tar.gz can of course also be done by right-click/exctract here. ;)
"tar -xzvf <package>" is just the command-line way of doing it.

---

### Post by rahul_bhise on 2007-07-14
> brahul@uhome:~$ cd Desktop
brahul@uhome:~/Desktop$ sudo alien -k --scripts AdobeReader_enu-7.0.9-1.i386.rpmadobereader-enu_7.0.9-1_i386.deb generated
brahul@uhome:~/Desktop$ sudo dpkg -i adobereader-enu_7.0.9-1_i386.deb
dpkg - warning: downgrading adobereader-enu from 7.0.9-2 to 7.0.9-1.
(Reading database ... 125951 files and directories currently installed.)
Preparing to replace adobereader-enu 7.0.9-2 (using adobereader-enu_7.0.9-1_i386.deb) ...
Unpacking replacement adobereader-enu ...
Setting up adobereader-enu (7.0.9-1) ...
ln: creating symbolic link `/Reader/intellinux/lib/libldap.so' to `/usr/lib/libldap.so.2': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/liblber.so' to `/usr/lib/liblber.so.2': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libORBit-2.so' to `/usr/lib/libORBit-2.so.0': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libbonobo-2.so' to `/usr/lib/libbonobo-2.so.0': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libbonobo-activation.so' to `/usr/lib/libbonobo-activation.so.4': No such file or directory
ln: creating symbolic link `/Reader/intellinux/lib/libgnomespeech.so' to `/usr/lib/libgnomespeech.so.7': No such file or directory
dpkg: error processing adobereader-enu (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 adobereader-enu
brahul@uhome:~/Desktop$ acroread
then the adobe startup logo showed up and then an error window  (tho this window did not look like error window)popped up saying
**there was an error while loading the plug-in 'PPKLite.api' the plug-in failed to initialize**
then it asked me to sine the terms and condition and then as usual.
**[SIZE="3"]but [/SIZE]** (sorry for that as we came so far in solving this problem) there are two adobe loncher in application>office>
they both show above error window. they both asked me to sign up the term's and condition.
(only for first time)
what i want to ask is that are there two software install OR there are only two lonchers

---

### Post by KIAaze on 2007-07-14
You can check this by looking at the command they use:
-Right click on applications
-select edit menus
-select office on the left
-search for the launchers in the items box
-right-click on them and select properties

This should display a "Launcher properties box" in which the command they use is listed.
If they have the same command, it means they launch the same program.

---

### Post by rahul_bhise on 2007-07-15
yes they show the same command. thanks for the help you offered. 
Yes... and anything about the 'PPKLite.api' error.

---

### Post by rahul_bhise on 2007-07-16
KIAaze 
just help me on this last one

---

### Post by KIAaze on 2007-07-16
Well, from google:
> It's in the ReadMe.htm:

PPKLite.api fails to load:
PPKLite requires the installation of the OpenLDAP package and fails to
initialize in its absence. If you get this error when acroread starts,
you need to install the LDAP libraries (OpenLDAP package). If PPKLite
still fails to load, make a link to the installed libldap.so.X and
liblber.so.X in <INSTALL_PATH>/Reader/intellinux/lib with the names
'libldap.so' and 'liblber.so'.

[http://www.fedoraforum.org/forum/archive/index.php/t-109602.html]("http://www.fedoraforum.org/forum/archive/index.php/t-109602.html")

So translated to Ubuntu, this means:
```
sudo apt-get install libldap2-dev
```
If PPKLite still fails to load:
```
sudo ln -s /usr/lib/libldap.so /usr/local/Adobe/Acrobat7.0/Reader/intellinux/lib/libldap.so
sudo ln -s /usr/lib/liblber.so /usr/local/Adobe/Acrobat7.0/Reader/intellinux/lib/liblber.so

```

Note: If you installed Adobe elsewhere than the default path (/usr/local/Adobe/Acrobat7.0), you'll have to adapt those last 2 commands accordingly of course.

edit:
If the second set of commands doesn't work, you could try this altough I doubt it will change anything:
```
sudo ln -s /usr/lib/libldap.so.2.0.130 /usr/local/Adobe/Acrobat7.0/Reader/intellinux/lib/libldap.so
sudo ln -s /usr/lib/liblber.so.2.0.130 /usr/local/Adobe/Acrobat7.0/Reader/intellinux/lib/liblber.so

```

And if you ever want to use a Free as in freedom PDF viewer, try kpdf:
```
sudo apt-get install kpdf
```

---

### Post by rahul_bhise on 2007-07-17
yes that did the job
> ln -s /usr/lib/libldap.so /usr/local/Adobe/Acrobat7.0/Reader/intellinux/lib/libldap.so
ln -s /usr/lib/liblber.so /usr/local/Adobe/Acrobat7.0/Reader/intellinux/lib/liblber.so
after typing the above it gave authorization error so i just typed sudo before each command and that worked
thanks KIAaze for your kind help

---

### Post by KIAaze on 2007-07-18
Ah, yes, forgot the sudo again. At least you figured it out. :)
(It's corrected now. ^^)

---

