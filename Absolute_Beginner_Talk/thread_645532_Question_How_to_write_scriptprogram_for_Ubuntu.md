---
title: "Question: How to write script/program for Ubuntu"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by suomalainen on 2007-12-20
Ubunteros,

I wanted to ask the following about creating a program/script..

Each morning I launch Firefox and go to an ABC News and NBC News website and download 1 file from each site. Same site, same location, same file each morning.

The files are downloaded to a folder on my desktop.

How would I go about finding out what it would take to create a program/script that could simply be clicked upon and the following actions I noted above reacted upon with no further effort from me....

Thanks

---

### Post by JillSwift on 2007-12-20
easy peasy. A simple shell script would manage that.

One of my fave sites for referencing shell commands:
[http://linuxcommand.org/](http://linuxcommand.org/)
also:
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)

The script would look like:
```
#!/bin/bash
cd /location/to/save/files/to
wget http://first.file/to.get
wget http://second.file/to.get
exit 0
```Of course, those paths are made up, you'd have to replace them with the real ones. =^_^=
Then you'd make the file executable, and make a launcher on your desktop. Bing-badda-boom! Time saved.

---

### Post by daimaru on 2007-12-20
> **JillSwift said:**
> 
Then you'd make the file executable, and make a launcher on your desktop. Bing-badda-boom! Time saved.
And if you want it to run automatically you create a cron job for it so it executes at 7am in the morning or something like that.

---

### Post by rich.bradshaw on 2007-12-20
Yep, use that. wget downloads files if you were wondering!

---

### Post by g2g591 on 2007-12-20
simple, just create a file with gedit or kate containing the commands to be run. In this case it would be somthing like this.
#!/bin/bash
wget location_of_file1
wget location_of_file2

the #!/bin/bash tells it to use the bash shell (not having it doesn't make much of a differance)
wget is a program that downloads stuff from the web. In order to make it executable you need to run sudo chmod +x file_you_just_created . you can even use kcron (not sure about a gnome equivalant) to set it to automaticcly run.

---

