---
title: "alien problem"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Franswa_CS on 2007-04-19
i have installed alien on my ubuntu, and when i tried to convert a rpm package, i got the following message (i suppose it is error message):

   [FONT=&quot]chown: changing ownership of `kernel-module-hsfmodem-5.03.27//lib/modules/2.4.22-1.2115.nptl/misc/hsfali.o': Operation not permitted
chown: changing ownership of `kernel-module-hsfmodem-5.03.27//lib/modules/2.4.22-1.2115.nptl/misc/hsfbasic2.o': Operation not permitted
chown: changing ownership of `kernel-module-hsfmodem-5.03.27//lib/modules/2.4.22-1.2115.nptl/misc/hsfengine.o': Operation not permitted
chown: changing ownership of `kernel-module-hsfmodem-5.03.27//lib/modules/2.4.22-1.2115.nptl/misc/hsfich.o': Operation not permitted
chown: changing ownership of `kernel-module-hsfmodem-5.03.27//lib/modules/2.4.22-1.2115.nptl/misc/hsfosspec.o': Operation not permitted
chown: changing ownership of `kernel-module-hsfmodem-5.03.27//lib/modules/2.4.22-1.2115.nptl/misc/hsfserial.o': Operation not permitted
chown: changing ownership of `kernel-module-hsfmodem-5.03.27//lib/modules/2.4.22-1.2115.nptl/misc/hsfvia.o': Operation not permitted
chown: changing ownership of `kernel-module-hsfmodem-5.03.27//lib/modules/2.4.22-1.2115.nptl/misc/hsfyukon.o': Operation not permitted
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_clean: Compatibility levels before 4 are deprecated.
dh_installdirs
dh_installdirs: Compatibility levels before 4 are deprecated.
dh_installdocs
dh_installdocs: Compatibility levels before 4 are deprecated.
install: cannot change owner and/or group of `debian/kernel-module-hsfmodem/usr': Operation not permitted
dh_installdocs: command returned error code 256
make: *** [binary-arch] Error 1
find: kernel-module-hsfmodem-5.03.27: No such file or directory[/FONT]
  

please help as this program is critical to me. (and to every one using ubuntu i suppose).

---

### Post by petersjm on 2007-04-19
Not sure about the chown error, but alien needs administrator privileges. Did you try "sudo alien..."?

EDIT: Actually, if the "package build failed" maybe alien isn't installed correctly? Try "sudo aptitude --purge remove alien" and then "sudo aptitude install alien" and try converting the rpm again...

---

### Post by x1a4 on 2007-04-19
Hi,

*sudo chown* as well.

---

### Post by max.diems on 2007-04-19
> **petersjm said:**
> Not sure about the chown error, but alien needs administrator privileges. Did you try "sudo alien..."?

EDIT: Actually, if the "package build failed" maybe alien isn't installed correctly?

I think they're all related: if alien wasn't run with sudo, that would usually make the chown fail, which would probably make the package build fail.

---

### Post by petersjm on 2007-04-19
> **max.diems said:**
> I think they're all related: if alien wasn't run with sudo, that would usually make the chown fail, which would probably make the package build fail.

Ah. Thanks. You learn something new every day! :D

---

### Post by Franswa_CS on 2007-04-20
i tried aptitude and it didn't work.
please any one help me this program is very critical to me.

thanks

---

### Post by Cypher on 2007-04-20
How didn't aptitude work? The more info you provide the sooner you can get a response. Giving more information than necessary is better than being vague..

Regards

---

### Post by Franswa_CS on 2007-04-20
i used aptitude to uninstall alien then install it again but when i use alien program the same error message i provided in post #1 appears.

---

### Post by max.diems on 2007-04-20
> [FONT=&quot]kernel-module-hsfmodem-5.03.27
HSFModem is available as a .deb, so if you can find it (look at the ThinkPad R50e article on ThinkWiki, its in the modem info), use it.
[/FONT]

---

### Post by Franswa_CS on 2007-04-21
i have downloaded the file thanks.

but what if i had downloaded a program that is only available in rpm format (for example) what should i do.

this is why i need alien.
thanks again, and help me if you can

---

### Post by max.diems on 2007-04-21
I've never had a problem with alien, so it could just be this one package. If it doesn't work with an RPM-only package, then there's something to worry about.

---

### Post by Franswa_CS on 2007-04-21
if you can provide me with the version of your alien program and a list of the dependency files to download , this will be a great help from you.

thanks for you information

---

### Post by max.diems on 2007-04-22
I always uninstall it when I'm done with it, it seems pointless to keep it around (I had to deal with 1GB drives for quite a while in the recent past (until last fall). I also haven't had any reason to use it for awhile.

---

### Post by Franswa_CS on 2007-04-29
how can i overcome the problem of chown of the files

---

### Post by kevinlyfellow on 2007-04-29
To be perfectly clear, you have been using sudo with alien right?

```
sudo alien --to-deb packagename.rpm
```

---

### Post by keithpeter on 2007-04-29
> **Franswa_CS said:**
> i have downloaded the file thanks.

but what if i had downloaded a program that is only available in rpm format (for example) what should i do.

this is why i need alien.
thanks again, and help me if you can

I have done this once to install OpenOffice 2.2 on my Xubuntu 6.06.1 LTS computer. The basic process is

[LIST=1]
[*]install alien
[*]use alien to convert the RPMs to .deb packages
[*]install the .deb packages on your computer by using the dpkg command
[/LIST]

I installed alien

```
sudo aptitude install alien
```

Then I downloaded the archive with the RPMs in it, and I unpacked the archive (to my Desktop as it happened). You can double click on the package icon on the Desktop and I think Ubuntu will ask if you want to unpack the archive.

Unpacking left a folder on my desktop. Somewhere in that folder were the RPMs with .rpm file extension. In the case of OpenOffice, the RPMs folder is a couple of folders down.

Then I started a terminal window and changed directory to the directory with the .rpm files. I ran the alien command as sudo,

```
sudo alien --keep-version *.rpms
```

That takes some minutes. You may have to research the correct command line to use with the software you are trying to install as some software needs the --script option set so that installation scripts are converted correctly.

Once the command has completed, you have .deb files in the .rpm folder along with the .rpm files. These .deb packages need to be installed on your computer, and aptitude is not the command for installing .deb packages. Use the dpkg command;

```
sudo dpkg -i *.deb
```

dpkg should spit out a few messages and then complete, and you should have your software installed. It can take a while to find which menu the software is in!

---

### Post by Franswa_CS on 2007-04-29
yes i used sudo and tries to run the program as a root
but the same problem appears : "chown: ......... : operation not permitted"

---

### Post by Franswa_CS on 2007-05-02
can any one tell me how to overcome the chwon problem in using alien.
i tried sudo command but it doesn't work
please help

---

### Post by kevinlyfellow on 2007-05-04
> **Franswa_CS said:**
> can any one tell me how to overcome the chwon problem in using alien.
i tried sudo command but it doesn't work
please help

Can you point us to file your trying to convert?

---

### Post by Franswa_CS on 2007-06-16
every time i try to use the alien program , i encounter the problem of chown of the files

---

### Post by kevinlyfellow on 2007-06-16
Honestly, the only thing I can say is that it is broken on your computer.  You can try to reinstall
```
sudo apt-get autoremove --purge alien
sudo apt-get install alien
```
but I'm not sure if that will work.  It is rare to find something just in rpm (unless its a really old proprietary driver like you started off with).  

Another thing is to try is the sudo su trick
```
sudo su
alien --to-deb kernel-module-hsfmodem-5.03.27-1.i386.rpm 

```

I think the best thing for you to do is to file a bug report if you really feel like it really is a bug with alien and not the packages you are converting (I tried some rpms, and I did not get the same errors you did).  [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

---

### Post by cisk4me on 2008-01-12
I had the same problem. I had the rpm on an external FAT formatted hard disk and this is the problem. I moved the file to a Linux formatted disk and then alien worked.

---

