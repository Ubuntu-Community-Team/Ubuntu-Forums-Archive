---
title: "Setting the time"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by vanderkerkoff on 2008-01-09
Hello everyone

I've just installed a fresh version of gutsy gibbon.  I chose UTC as I live in the GMT time zone.

The time if I input date is giving me is incorrect.

How do I change the time from the command line?  We can't use ntp, our network guys wont allow it

:(

The date adn time zone is correct.

Thanks in advance.

---

### Post by bumanie on 2008-01-09
I am on a windows machine at present, but I think if you go to System 
--> Administration, there should be a date/time selection available in the GUI.

---

### Post by vanderkerkoff on 2008-01-09
Hi Bumanie

I need to know how to do it from the command line.

"How do I change the time from the command line? We can't use ntp, our network guys wont allow it"

Thanks for trying anyway.

V

---

### Post by mikeyphi on 2008-01-09
Right-click on the time. Left-click on Preferences - make sure UTC box is deselected
Right-click on time. Left-click on just date & time - set Time zone to GMT, set configuration to manual.

You should then be able to set the time by Left-click on the time.

---

### Post by vanderkerkoff on 2008-01-09
Hi mikeyphi.

From the command line mate, thanks anyway.

---

### Post by vanderkerkoff on 2008-01-09
I got it

sudo date -s "01/09/2008 15:02:00"

---

### Post by eolson on 2008-01-09
man date

there's a bunch of options

---

### Post by bumanie on 2008-01-09
This thread may help [http://ubuntuforums.org/showthread.php?t=448935](http://ubuntuforums.org/showthread.php?t=448935)
If not, do as suggested and look up the man pages.

---

### Post by vanderkerkoff on 2008-01-09
Thanks everyone, but I worked it out and posted the solution in this thread.

Thanks again.

---

