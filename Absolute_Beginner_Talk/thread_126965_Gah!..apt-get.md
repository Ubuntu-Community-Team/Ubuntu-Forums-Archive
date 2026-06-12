---
title: "Gah!..apt-get"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by darkbullet87 on 2006-02-07
This is probably more of a question for "Ubuntu Repository Support" but I kinda need a walk through on how this works, so I figured I'd get a more detailed awnser here. 

To make it simple, I don't get how apt-get works. I have basic knowledge of "yum" but it doesn't seem to be helping me any with apt-get. I tried to install AVG antivirus (free.grisoft.com) and I couldn't find a download package that worked. I've gone through the tutorials and postings in the Repository secontion, and I'm getting a good idea of the commands, but I still cant add repositories or download programs. Could anyone tell me what I'm doing wrong (specificly with AVG)

---

### Post by Kyral on 2006-02-07
[quote=darkbullet87]This is probably more of a question for "Ubuntu Repository Support" but I kinda need a walk through on how this works, so I figured I'd get a more detailed awnser here. 

To make it simple, I don't get how apt-get works. I have basic knowledge of "yum" but it doesn't seem to be helping me any with apt-get. I tried to install AVG antivirus (free.grisoft.com) and I couldn't find a download package that worked. I've gone through the tutorials and postings in the Repository secontion, and I'm getting a good idea of the commands, but I still cant add repositories or download programs. Could anyone tell me what I'm doing wrong (specificly with AVG)[/quote]

Perhaps this would be most useful
[http://www.ubuntuforums.org/showpost.php?p=468342&postcount=33](http://www.ubuntuforums.org/showpost.php?p=468342&postcount=33)

---

### Post by cwaldbieser on 2006-02-07
[QUOTE=darkbullet87]This is probably more of a question for "Ubuntu Repository Support" but I kinda need a walk through on how this works, so I figured I'd get a more detailed awnser here. 

To make it simple, I don't get how apt-get works. I have basic knowledge of "yum" but it doesn't seem to be helping me any with apt-get. I tried to install AVG antivirus (free.grisoft.com) and I couldn't find a download package that worked. I've gone through the tutorials and postings in the Repository secontion, and I'm getting a good idea of the commands, but I still cant add repositories or download programs. Could anyone tell me what I'm doing wrong (specificly with AVG)[/QUOTE]
The idea of apt-get is pretty simple.  There are huge centralized repositories that have all the packages for a particular distribution and version.  The repositories are typically mirrored so you can choose the best one to connect to.

You configure your apt-get client program by editing your /etc/apt/sources.list and adding the lines for the repositories.  The entries look like URLs plus the names of various sections (e.g. main, universe, security, etc.).

You issue an "apt-get update" sub-command to cause the client to refresh its index of the packages from the repository.  You can browse the index to select what packages you want.  You issue an "apt-get install <package>" command to install a particular package.

apt-get isn't particularly useful for installing programs that are *not* in the repositories.  I am not sure if the program you are trying to install is in one of the repositories or not, as you did not specify exactly how you tried to install the software.

---

