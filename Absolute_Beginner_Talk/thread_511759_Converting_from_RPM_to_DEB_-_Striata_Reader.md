---
title: "Converting from RPM to DEB - Striata Reader"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by psainsbury on 2007-07-28
I'm in the process of waving goodbye to Windows, and I'm hitting a few issues.  One of them is that a bunch of the places where I have accounts send me my statements using the Striata reader.  So my only way to decode and view them is to have the striata reader installed on my Ubuntu 7.04 installation.

It has an RPM install that can be found here:
   [http://www.striata.co.za/_africa/downloads.php](http://www.striata.co.za/_africa/downloads.php)

I'm installing the Linux GUI version, and if I run:
  sudo alien -k striata-reader-1.0-27-linux-2.4-intel.rpm

I get the warnings:
Warning: Skipping conversion of scripts in package striata-reader: postinst preinst prerm
Warning: Use the --scripts parameter to include the scripts.

So I then tried to run it as:
  sudo alien --scripts -k striata-reader-1.0-27-linux-2.4-intel.rpm 

and then I got no errors or warnings so I ran the following:
 sudo dpkg -i striata-reader_1.0-27_i386.deb 

and I got the following error:
   dpkg: syntax error: unknown user `hplip' in statoverride file 

Can someone help me with how to get this package converted and installed?

Thanks

From
  Paul

---

### Post by goatflyer on 2007-07-28
hplip is a system user account for the HP Linux Printing and Imaging System (HPLIP) which (I thought) was automatically included when Ubuntu is installed.

If you type
```

 cat /etc/passwd | grep hp

```
  you should a response looking something similar to:
```

hplip:x:107:7:HPLIP system user,,,:/var/run/hplip:/bin/false

```

If not then open Synaptic and make sure the hplip package is installed.  Do this even if you don't have a printer.

Hope this works for you.

---

### Post by psainsbury on 2007-07-28
I checked the users as you suggested and found the hplip user.   So I'm not sure what the installation was complaining about.   I then removed the striata package (via synaptic), and reinsalled as per my original message and it seemed to work fine. (There were no error messages)

Unfortunately the striata reader doesn't seem to open up at all...  I guess I'll have to mail the striata guys directly to see if they have any solution.

Thanks.

---

### Post by infoseeker on 2008-02-17
I have the same problem in Ubuntu, but........

If I save the *.emc attachment I can open it without any problems using SUSE 10.3 which I have installed for test purposes.  The Striata reader was installed in Suse from the rpm file  without any problems and immediately recognises the *.emc file as a striata encoded/encrypted file.

Under Ubuntu I converted the same rpm file to a deb using 'alien' and installed it - no luck although i can right click it and select 'open with Striata Reader", but does not open.

EDIT: I see Java is involved here somewhere.

---

### Post by bumanie on 2008-02-17
Not sure if this will help you, but there is a program called alien that converts .rpm to .deb This tutorial shows you how to do it
[http://www.howtoforge.com/converting_rpm_to_deb_with_alien](http://www.howtoforge.com/converting_rpm_to_deb_with_alien)
Hope this helps.

---

### Post by infoseeker on 2008-02-17
> If you are using an i386 computer install the 'sun-java6-plugin' package from the &#8220;Multiverse&#8221; repository.

This worked for me :D

I can now open the *.emc file from Nautilus (I placed my files in 'Places -> Documents -> striata').

EDIT: In fact you can open it directly from Evolution Mail :D

Summary
=======

Download the striata-reader-1.0-27-linux-2.4-intel.rpm file (Linux GUI)
[http://www.striata.co.za/_africa/downloads.php](http://www.striata.co.za/_africa/downloads.php)

Create folder for storage under your user (or anywhere accessible) example '~/striata'
Move the downloaded rpm file into this folder and 'cd' to this folder.

Install 'alien' (to convert *.rpm to *.deb)
```
sudo apt-get install alien
```

Convert the package.rpm into a package.deb (creates 'striata-reader_1.0-28_i386.deb' from 'striata-reader-1.0-27-linux-2.4-intel.rpm')
```
sudo alien -d striata-reader-1.0-27-linux-2.4-intel.rpm
```

To install the *.deb file
```
sudo dpkg -i striata-reader_1.0-28_i386.deb
```

install the 'sun-java6-plugin' package
```
sudo apt-get install sun-java6-plugin
```

Continued 2 posts down :D

---

### Post by maljaros on 2008-05-03
Thank you Infoseeker.  I can now open my statements, but only through the terminal.  You say that this should be possible directly from Evolution - can you explain a bit further.
My *.emc arrives attached to an email but Evolution only allows me to save the attachment.  Now that I have striata-reader installed (it even appears in my XFCE-menu, but clicking on it doesn't seem to produce a useful result) should I be able to open the attachment instead of saving it?

---

### Post by cookieforyou on 2008-05-10
Attempted to use the reader with Hardy Heron and ended up getting errors, and asking for login/password (or something) in a Java console it seems. See attached.
Then tried command line and received:
```
~/Documents/striata$ striata-reader MultiChoice_Statements_20080115.emc
striata-reader: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```
So, I went to Adept and after some searching found 'libstdc++5' in the repos (libstdc++6 was currently installed) which I installed, and now Striata Reader works fine again. YAAAAY
This applies to KDE of course. Synaptic should do the trick in Ubuntu.  GL

---

### Post by infoseeker on 2008-05-10
With Hardy Heron I can save the attached *.emc file, which can then be opened from Dolphin, but I cannot open it from Evolution.

EDIT:
Opening from within Evolution seems to work fine when using Ubuntu, but unfortunately the same does not apply to Kubuntu.  Obviously the differences between Gnome and KDE are sufficient to cause this.

maljaros.......it seems as tho XFCE and KDE respond the same way to *.emc files :)

EDIT:
The *.emc attachment can be opened in Kmail simply by clicking it (within KDE of course)

---

