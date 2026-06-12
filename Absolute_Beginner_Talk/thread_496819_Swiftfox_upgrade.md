---
title: "Swiftfox upgrade"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by Resistance on 2007-07-09
Hello,

This is question as much about Swiftfox as it is about installing software from sites and not through Synaptic. 

Here goes:

I have an AMD 64 processor, and I use Swiftfox in its 2.0.0.3 incarnation. Through a Google search, I found that the latest version is 2.0.0.4, and I would like to upgrade. Apparently, 2.0.0.4 is not present in the repositories, so I downloaded it from the Swiftfox site itself. ([http://getswiftfox.com/rel-athlon64.htm]("http://getswiftfox.com/rel-athlon64.htm")

I unpacked the file, which is now sitting nicely on my desktop. Being a newbie though, I do not know how to install stuff that way, since it is different from Windows, where you just double click and that's it. 

Can anyone help? 

Thank you!

---

### Post by Inxsible on 2007-07-09
On the same website, if you go to the [Installers]("http://getswiftfox.com/installer.htm") link, they have a bunch of scripts to install the software depending on your processor architecture.

---

### Post by Rui Pais on 2007-07-09
> **Resistance said:**
> 
I unpacked the file, which is now sitting nicely on my desktop. 

just go to that folder and click on swiftfox file :)

you may be interested in this (instead of swiftfox):
[http://swiftweasel.sourceforge.net/about.php](http://swiftweasel.sourceforge.net/about.php)

hth

---

### Post by KIAaze on 2007-07-09
You should have downloaded the installer instead of the tar.bz2 package.
Download the installer here:
[http://getswiftfox.com/installer.htm]("http://getswiftfox.com/installer.htm")

And then just run it like this:
Command-line way:
```
cd <directory where you downloaded it>
chmod +x install-swiftfox.sh
./install-swiftfox.sh
```

Or through the GUI:
-Right click the .sh file, go into properties, permissions.
-Turn the "executable" checkbox on.
-Double-click the .sh file.
-Click run.

You might want to read one of these articles too:
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")
[http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")
[https://help.ubuntu.com/community/SoftwareManagement]("https://help.ubuntu.com/community/SoftwareManagement")

---

