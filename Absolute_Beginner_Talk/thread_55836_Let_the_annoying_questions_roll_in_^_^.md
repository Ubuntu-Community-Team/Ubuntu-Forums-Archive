---
title: "Let the annoying questions roll in ^_^"
date: 2005-08-10
forum: Absolute Beginner Talk
---

### Post by akechi on 2005-08-10
is there a tutorial or a place i can get info on how to create a Http webserver (i think thats what they are called) like this: [http://cdimage.debian.org/pub/weekly/](http://cdimage.debian.org/pub/weekly/)
i want to be able to host files for my network security class where they can put files on it too, like our labs and notes.  and for my own personal use of course.  and i just really want to know how to do things like this.  after i get this one down im going with wikis next. or i may do that first, dunno yet.

Once again, thanx all. this is a great community and one of the best distros i've used yet!!

---

### Post by akechi on 2005-08-10
Hmmmm...... seems this post has already been started on cleaning useless files:  [http://www.ubuntuforums.org/showthread.php?t=55433](http://www.ubuntuforums.org/showthread.php?t=55433)

---

### Post by KingBahamut on 2005-08-10
Sounds like you need to read up on Apache. That the first part. 

[http://www.apache.org](http://www.apache.org) 
[https://wiki.ubuntu.com/HelpOnInstalling/ApacheOnLinux?highlight=%28Apache%29](https://wiki.ubuntu.com/HelpOnInstalling/ApacheOnLinux?highlight=%28Apache%29)

The Put files into to deal....can do that though a deal like this -- 
[http://freshmeat.net/projects/smbwebclient/](http://freshmeat.net/projects/smbwebclient/)

But first need to get apache running and configured properly.

---

### Post by akechi on 2005-08-10
nice!  thanks!  will read up on that soon as im outta work.

---

### Post by KingBahamut on 2005-08-10
[QUOTE=akechi]nice!  thanks!  will read up on that soon as im outta work.[/QUOTE]
 No Problem. 
=)

---

### Post by az on 2005-08-10
Well, if you want to upload stuff too, you are probably thinking of FTP.  There are several FTP servers in Ubuntu.  But they are completely insecure as they use plaintext passwords.

Perhaps you want to set up a CMS?  (Content Management System?)  Often you can set up a wiki in a CMS by installing a module (or an extension or a plugin, depending on what CMS you chose).

A CMS is database driven.  You would need to install Apache, Mysql, PHP, and the CMS. (cmsmatrix.org -  Great list!  Check out drupal.org.  I find it pretty good all-round)

You should also set up a firewall.  I have done the above using shorewall and dnsmasq.  The box was my home router as well as the webserver for the website.

---

