---
title: "Installing the latest Firefox woes..."
date: 2006-04-04
forum: Absolute Beginner Talk
---

### Post by coopns on 2006-04-04
I see synaptic is friendly but...
I go to Help..About..Firefox and I am at 1.0.7. The latest is 1.5 or 1.7. I downloaded firefox-1.5.0.1.tar.gz. On the desktop icon it has tz on it.

In synaptic, I go to Package...Force Version but it is greyed out.

So do I have to use the make and install commands? If so, could you clarify the commands. 

And, exactly when can I just use Apt-get and when to have have to do make, install commands?

Thanks.

---

### Post by LKRaider on 2006-04-04
Try this wiki guide to get the new Firefox: [FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")

The **tar.gz** files are compressed archives, like zip and rar. On apt-get (aka. *dpkg*), or synaptic, the files in question are debian packages (extension is **.deb**), which contain instructions on how the files should be installed on the system (among other things), and help the system keep track of what was installed.

Programs that need to be installed with _make_, _make install_, etc. are programs distributed in *source-code* format, and _make_ turns them into executable code (*binary format*).

Debian Packages already come in binary format, and are easier to install.

Some programs, like Firefox 1.5 are also distributed in binary format, but compressed inside tar.gz archives, and since they don't have specific instructions on how to install into an Ubuntu desktop, they need some manual work to do so.

---

### Post by catlett on 2006-04-04
Make your life easy. Follow this link and install Automatix. It will give you Firefox 1.5, all it's plugins and Opera 8.5. [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

