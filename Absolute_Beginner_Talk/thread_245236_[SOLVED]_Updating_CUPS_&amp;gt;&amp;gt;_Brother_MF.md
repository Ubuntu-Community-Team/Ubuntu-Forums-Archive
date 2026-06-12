---
title: "[SOLVED] Updating CUPS &amp;gt;&amp;gt; Brother MFC-8440"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by altonbr on 2006-08-27
I just recently bought a Brother MFC-8440 printer, but CUPS only has the MFC-8300 and MFC-9050... how can I put in a request for this driver or find out if there actually is one available?

---

### Post by jmrweb on 2006-08-27
hi
have you tried the brother website there is a complete list of lpr and cups wrappers for many printers there.

heeres the url

[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

hope that helps 
take care john in sheffield uk

---

### Post by altonbr on 2006-08-27
:S

now what do I do when I have 'cupswrapperMFC8440-1.0.2-1.i386.deb.deb' or 'cupswrapperMFC8440-1.0.2-1.i386.rpm.bin'

---

### Post by ajgreeny on 2006-08-27
Not certain but if it is like most deb packages you just need to 
sudo dpkg install cupswrapperMFC8440-1.0.2-1.i386.deb.deb
I don't understand why there are two ".deb"s at the end of the package name but give it a try to see which is the correct one.  I use kubuntu and can do this with the gui but I'm not sure about gnome if you use that, perhaps you can double click it or something.

---

### Post by altonbr on 2006-08-31
I tried the 

```
sudo dpkg install cupswrapperMFC8440-1.0.2-1.i386.deb.deb
```

function but it returned with

```

dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

```

so I tried 

```
sudo dselect install cupswrapperMFC8440-1.0.2-1.i386.deb.deb
```

and this happened:

```

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Do you want to erase any previously downloaded .deb files? [Y/n] y
Press enter to continue.

dselect: unknown action string `cupswrapperMFC8440-1.0.2-1.i386.deb.deb'

Type dselect --help for help.

```

So then I tried going through the 'Add Printer' function in the System > Administration > Printing diologue... but that was to no avail... 


Can anyone help?

---

### Post by bigken on 2006-09-17
Take a look [here ]("http://www.ubuntuforums.org/showthread.php?t=105703&highlight=brother+mfc")Im sure this will solve your problems ;)

---

### Post by altonbr on 2006-09-27
@bigken

Thanks for the tutorial. It was much needed. For anyone else using a MFC-8440, follow the tutorial above and here are the links to the LPR and CUPS drivers.

**LPR:** [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc8440lpr-1.1.2-1.i386.deb&lang=English_lpr]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/lpr_debian/mfc8440lpr-1.1.2-1.i386.deb&lang=English_lpr")
**CUPS:** [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC8440-1.0.2-1.i386.deb&lang=English_gpl]("http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://solutions.brother.com/Library/sol/printer/linux/rpmfiles/cups_wrapper/cupswrapperMFC8440-1.0.2-1.i386.deb&lang=English_gpl")

---

### Post by bigken on 2006-09-27
pleased you got it sorted 8)

---

### Post by altonbr on 2006-09-28
Well I haven't yet... the LPR driver doesn't seem to be working. But I'll keep you updated :)

Can't believe I couldn't put 2 and 2 together a search for 'MFC driver' instead of 'MFC-8440'.. sorry.

---

### Post by altonbr on 2007-09-16
The brother MFC-8440 isn't supported that well in Linux; only printing works, and it works 3x slower than the Windows driver while scanning doesn't work at all and the drivers bugger up your system sometimes.

Marking this thread as solved nonetheless.

---

### Post by smilingfrog on 2008-07-16
Although I am still working on this, I do have print and scan functionality with Ubuntu 8.04 and MFC-8440

1. scanner drivers brscan-0.2.4-0.i386.deb [ here]("http://solutions.brother.com/linux/sol/printer/linux/sane_install.html") from brother. I ran all the commands as root instead of sudo.

2. edit the /etc/udev/rules.d/40-basic-permissions.rules file per 
[http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq.html#9")

3. restart the system.

Seems to work!

---

