---
title: "Firefox extensions errors - Howto fix"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Matty2006 on 2007-05-07
A while back I was running OpenSuse linux and later went and formated my linux partitions except my home directory. The trouble with this is that there is some slight differences on how the user data is stored between these two distros so problems like this come up...

I am big fan of the firefox extensions and I was at a loss when I found that the addon wizard was not working.If you did something similar here is How to fix it:

1. Open konqueror file manager

2 Browse to your /home directory if not there already

3. find the directory .firefox/<your profile>/ where the profile may be a bunch of random numbers letters
Note: after correcting this. I found that the directory was no longer here after adding new extensions and later rebooting.

4. Look for the file called extensions.rdf and move it to trash.

5. dont worry you can undelete it if you need it back.. but I think firefox actually makes a new one if its missing.

6. close firefox and reopen it.

7. Try adding an extension :)

Hope this helps :)

Off topic..
One other thing.. If you get an error every time you open konqueror then its likely you have a bad files shortcut. Suse adds its own to this by default so you may need to remove it. I had to remove the system shortcut.

---

### Post by Tundro Walker on 2007-05-07
Nice work, Matty!  I like it when folks figure something out, and post the knowledge so it can help others.

Forum Admins should probably move this to the "Tutorials & Tips" section.

---

### Post by NickHollingsworth on 2008-05-26
Thanks Matty, it worked for me too.

I have described the whole process of removing firefox3, reinstalling version 2 and enabling the extensions in [**_Ubuntu 8.04: Downgrading Firefox and Enabling Extensions_**]("http://notatplay.blogspot.com/2008/05/ubuntu-804-downgrading-firefox-and.html").

---

