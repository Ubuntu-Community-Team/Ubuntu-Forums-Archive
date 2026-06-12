---
title: "graphical file manipulation"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by jmilane on 2006-07-26
Hi,

I dont like the command line so much (yet) so I have been ftp'ing files around on my machine. I can also change permissions this way. It is as close to Explorer as I can get right now, and until I learn Linux I am forced to use methods familiar to me. Usually. I am trying not to, but I have deadlines and need to get some stuff done. 

Problem is, unless I run gftp as su, I dont have the permissions I need to do most things.

When I *sudo gftp*, I get an error... **Cannot Open Display**.
*gksudo gftp *is supposed to work - I will try when I get home. Apparently there is a bug related to this. 

Someone asked why I would want to run gftp as sudo. The aforementioned is why.

But is there a better graphical way to move and manipulate files?

Thank you.

J

PS - maybe if someone could point me towards that list of Linux aps that is mapped to their M$ relative, it would be helpful.

---

### Post by moma on 2006-07-26
Hello,

I use Nautilus filemanager to browse files. It can also connect to FTP-sites as shown in this picture.
[[img]http://bildr.no/thumb/7112.jpeg[/img]](http://bildr.no/view/7112)

Start Nautilus from Places -> Home_Folder menu and select 
File -> Connect to Server...

You can drag & drop files between ftp and local folder.


// moma
   [http://www.futuredesktop.com/ubuntu6.06.html]("http://www.futuredesktop.com/ubuntu6.06.html")

ps. take a look at this linux vs. windows app list.
[http://ubuntuforums.org/showthread.php?t=33183]("http://ubuntuforums.org/showthread.php?t=33183")

---

### Post by ahaslam on 2006-07-26
I used to use **gksudo nautilus**

You can make a launcher with that command or use it from terminal.

It's the same as above but with root privileges , caution is required.


Tony.

---

### Post by jmilane on 2006-07-26
Fantastic. Thank you very much.

---

