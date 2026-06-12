---
title: "Why do I have to sudo Gnomebaker to get it to make CD's"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by CujoQuarrel on 2006-10-03
When burning a CD I get errors unless I start the CD burning app with sudo.

Is this intended? If so it's sorta counterintutive.

---

### Post by Mark_in_Hollywood on 2006-10-03
I'm a newbie, so this response should be taken with a grain of salt:

you need to change the ownership of Gnomebaker. Please google:

wiki ubuntu file ownership

---

### Post by dannyboy79 on 2006-10-03
Don't listen to Mark_in_Holly. Sometimes you want the writer to have limited privalages. if you have a multi-user box than you may not want others to be able to burn stuff. Ubuntu and most linux distro are very secure, they aren't like Windows were you automatically get admin rights right off the bat. WHat I did was go to alacarte menu editor and then find gnomebaker, then go to the properties, and I added gksudo in front of the command, that way when I click on it from the drop down menu, it'll ask me for the sudo password and I good to go. or if you wanted to, you could do it the way Mark_in_Holl but kind of goes against what linux is all about.

---

### Post by Super King on 2006-10-03
Was this something new in Dapper? I didn't have to do this in Breezy, and I agree with the topic creator, that would get annoying fast.

---

### Post by endorfin on 2006-10-09
Why should someone use gksudo and not sudo command alone???

---

### Post by endorfin on 2006-10-09
I did change the command in the alacarte menu, but it still isn't working even though I open gnomebaker as root. What's wrong?

---

### Post by CujoQuarrel on 2006-10-09
I did a 
**chmod +s /usr/bin/gnomebaker**
 so that I didn't have to fire it off with sudo each time so it's not a problem for me. Just curious as to why this would be necessary. I would have thought that the standard would be for everyone to have access to the burner.

I would like to do something for nautilus in the same vein but the chmod +s causes nautilus to fail with 

******************************************************
(nautilus:11576): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

Refusing to initialize GTK+.
******************************************************

Anyone know what it means by "helper program"?

---

### Post by bswilson on 2006-10-09
> **endorfin said:**
> Why should someone use gksudo and not sudo command alone???

One uses **gksudo** to run GTK/GTK+ applications with root privileges. Using sudo to start these graphical applications can cause problems with user account permissions.

---

### Post by dannyboy79 on 2006-10-10
> **endorfin said:**
> I did change the command in the alacarte menu, but it still isn't working even though I open gnomebaker as root. What's wrong?

what isn't working? you have errors when trying to burn a cd? if you are starting gnomebaker using gksudo then it should be asking you for a password. when you enter it you should have root capabilities within gnomebaker.

---

