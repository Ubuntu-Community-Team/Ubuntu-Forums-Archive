---
title: "Icon"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by Bahal on 2006-09-28
Wazzap people ;)
I just downloaded Realplayer10 from its site and then executed it from a Folder in my /home . 

The problem is: why dont I get any icon av realplayer under my applications.  dont have any thing to click on, unless I go to the folder and click on some icon with the following format : "x-shellscript". Then this question comes up : "Do you want to run "realplay", or display its contents?"

I cant move "this" icon from its folder, because it simply wont run realplayer.

somebody help me](*,)

---

### Post by Marsolin on 2006-09-28
If you install [RealPlayer]("http://linuxappfinder.com/package/realplayer") from the dapper-commercial repository it will have a menu entry.

Here is the line for the /etc/apt/sources.list file.

deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) dapper-commercial main

---

### Post by Bahal on 2006-09-28
thx...
so if got you right, you wont me to install it again...then I need to ask....
will it be a executable file or I should run the command <chmod a+x "blabla">

:confused:

---

### Post by Marsolin on 2006-09-28
You should be able to add the source through Synaptic.  Here's a [link]("http://linuxappfinder.com/addrepo") to show how.

deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) dapper-commercial main

Once you do that click Reload then search for realplay and select the package. Choose Apply to download and install the program.

Does that help?

---

