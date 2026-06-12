---
title: "Starting FRESH! Need LAMP!"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Nutopia on 2008-01-21
Hi,

i've spent the past few days getting acquainted with Ubuntu. One PC had a successful install, the other didn't and I reverted back. On the successful install I started to try to get a LAMP build going but ran into more problems along the way. I original downloaded the sourceballz myself and tried for manual install instead of through the packages, so I fear I made mistakes along the way which corrupted the package installs I've been trying for lately.

Now that I know somewhat what's going on, I want to wipe out and start over. But this time, I don't want to screw everything up first then ask for  help. I want to do it the right way from the start.

I've got my Ubuntu CD in the drive. I'm ready to start a fresh install. I want to be able to develop in a LAMP environment locally and then (using subversion) send my code to our servers for QA and Production. Ideally, no more windows!

I now beg the vast Ubuntu knowledge base for the simplest, most straightforward way to do this. I think someone referred to the ability to install Ubuntu with LAMP pre-configured from the forefront. i want to do that if I can. Is that correct and how do I do it? I don't want to find out later I made another mistake!

If anyone can help I would be much appreciated and sing the praises of Ubuntu and its community every time someone tries to get me to use a MAC...!

---

### Post by tgalati4 on 2008-01-21
[http://www.apachefriends.org/en/xampp.html](http://www.apachefriends.org/en/xampp.html)

---

### Post by sumguy231 on 2008-01-21
The easiest thing to do would be to get the Ubuntu Server install CD and use the 'Install a LAMP Server' option.

---

### Post by mcduck on 2008-01-21
Here's the easiest (graphical) way to get LAMP installed:

1. Go to System/Administration/Synaptic Package Manager
2. Next, select File/Select packages by task
3. Mark 'LAMP server' and click ok.
4. Click 'Apply'

This will download, install and configure LAMP server for you.

Even easier way is to open a terminal (Application/Accessories/Terminal) and run "sudo tasksel install lamp-server".

edit: You'll probably also want a browser-based tool for MySQL. "phmyadmin" is a nice one, you can also install it with Synaptic, or by running 'sudo apt-get install phpmyadmin". After that you can access it with your browser in address  [http://localhost/phpmyadmin/]("http://localhost/phpmyadmin/").

---

### Post by mcduck on 2008-01-21
Since you tries to install LAMP from downloaded source you might find reading this quite helpful: [How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Nutopia on 2008-01-21
Haha.. Ya, being a total noob I had no idea about that package thing - it's really cool. 

I've got my newest install of Ubuntu updating now. I will then install the LAMP package as described. If there are any errors I'm coming back at you!! ;)

Otherwise i will confirm the install and celebrate with a lunch break.... corned beef sounds good :)

---

### Post by Nutopia on 2008-01-21
Ok, it looks like everything is installed correctly this time - which is good. 

I must be missing one thing though - I created a simple php file to try and execute, but when I direct browser to it it is trying to download the file instead of running it.

I was hoping the install would have made those changes because I'm not sure what to do?

---

### Post by mcduck on 2008-01-21
> **Nutopia said:**
> Ok, it looks like everything is installed correctly this time - which is good. 

I must be missing one thing though - I created a simple php file to try and execute, but when I direct browser to it it is trying to download the file instead of running it.

I was hoping the install would have made those changes because I'm not sure what to do?
Actually I had the same problem when I installed LAMP on my laptop. I think a simple reboot solved the issue, although I also installed the 'phpmyadmin' before rebooting. Anyway either one of these did the trick..

---

### Post by Nutopia on 2008-01-21
we'll i'll be a penguin...!

restart worked! and i thought the corned beef was gonna get cold!

Thanks for the help! Everything is looking good. The last piece I need before I start rocking is to get subversion working. Any recommendation on a package to grab? I was using tortoise svn on windows before the switch...

---

### Post by az on 2008-01-21
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

If you installed all the packages and it still offers to download the file instead of executing it, try refreshing your borwser's cache (CTRL-F5 to reload the page).

I would sugges you avoid installing LAMP from tarballs or XAMPP.  Use the package manager - it's the only sane option for a production system.

---

### Post by Nutopia on 2008-01-21
As far as a package for versioning, I'm going to just download subversion in package manager. I arbitrarily picked this because it has a the Ubuntu logo next to it. 

If anyone has a better option or reason why I shouldn't download it, let me know!

---

