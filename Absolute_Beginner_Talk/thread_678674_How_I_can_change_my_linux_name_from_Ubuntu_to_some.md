---
title: "How I can change my linux name from Ubuntu to something else?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-01-26
Hi
I need to install some software in Ubuntu 7.10 and these software only install into Suse enterprise Linux, 
long ago I saw that a linux name (brand?, version..) are stored into a file and if we change that file, all installers that look for the operating system name inside that file will install properly.


Can some one let me know whether this file exists in Ubuntu and if it exists what is its address?

Thanks.

---

### Post by gvartser on 2008-01-26
Hmm i guess that it is easier to check the config file for the application that you want to build/install and change it the or out comment the "OS test" in the script. What application is it?

Best regz,
/G

---

### Post by legolas_w on 2008-01-26
Thank you for reply.
The application That I am going to install is a bin file, after i execute the file it opens an installer which will stops because of the OS version.


Thanks.

---

### Post by ugm6hr on 2008-01-26
> **legolas_w said:**
> Thank you for reply.
The application That I am going to install is a bin file, after i execute the file it opens an installer which will stops because of the OS version.


I think you have entirely misunderstood how packages come in Linux.  One made for Suse will not work directly with Ubuntu without some editing.

If you let us know which package, and where you got it from, someone should be able to help.  Most packages are available as "Source" in a tar format that can be installed on any Linux.

This is a good link to info on packages in Linux in general: [http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

---

### Post by gvartser on 2008-01-26
I guess that it isn't a open source application..

Or can you get a hold of the source and compile it yourself?

Best regz,
/g

---

### Post by bumanie on 2008-01-26
I think what you are looking at is converting a rpm file to a deb file. Rpm files are used in red hat and suse. To convert to a deb you need a program called alien. In terminal type
sudo apt-get install alien
Then follow this guide
[http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-rpm-files-in-debian-and-ubuntu.html)
Good Luck.

---

### Post by legolas_w on 2008-01-26
Hi
Thank you all for your reply, and sorry for posting an misleading question.

Some non-open source applications like "DB2 Data studio" are meant to be installed into an Enterprise Linux like Redhat Enterprise or Suse enterprise. They are .bin file or tar.gz which has an installer script inside them.
I want to install IBM data studio into Ubuntu instead of Redhat enterprise or Suse enterprise. I think it is possible to do this because my friend installed Oracle Database into slackware linux using and also the following tutorial shows how we  can change OS name in SUSE linux desktop edition in order to fool the installer to treat it as an enterprise linux.

I thought maybe a file like that is present in Ubuntu.

Following link shows how we can fool oracle installer to treat Suse desktop Linux as Suse enterprise linux.

[http://www.novell.com/coolsolutions/appnote/17778.html](http://www.novell.com/coolsolutions/appnote/17778.html)

Thanks.

---

### Post by gvartser on 2008-01-26
> **legolas_w said:**
> Hi
. I think it is possible to do this because my friend installed Oracle Database into slackware linux using and also the following tutorial shows how we  can change OS name in SUSE linux desktop edition in order to fool the installer to treat it as an enterprise linux.


When it comes to oracle there are several ways of doing this,one of them is to start runinstaller with an argument.

```
./runinstaller --ignoresysPrereqs
```

Or another way as your friend probably did was to edit the oraparam.ini file that is read by the runinstaller while installing oracle.
Adding the following information:
```
Linux=redhat-2.1,UnitedLinux-1.0,redhat-3,[COLOR="Red"]SuSE-Desktop[/COLOR]
```

That was why I asked you in a previous post if there were any config files, but in your case no such luck.. :(

/g

---

