---
title: "Battery always shown as charging"
date: 2011-03-11
forum: Apple Hardware Users
---

### Post by wweeks on 2011-03-11
My iBook G3/600 running Ubuntu 10.10 always says the battery is charging and plugged in even when its not. Any ideas? Its really getting annoying when it just dies because it runs out of battery.
I've tried batmon but the whole system thinks it's plugged in so that doesn't help at all. :( I'm stuck guessing from the charge gauge on the bottom of the battery.:cry::cry::cry:

---

### Post by linuxopjemac on 2011-03-13
do you have the line
```
pmu_battery
```
in /etc/modules ?

---

### Post by wweeks on 2011-03-13
No, is that what I need to add? gedit has loaded it as read only, how do I edit if I need to?

---

### Post by linuxopjemac on 2011-03-13
```
gksudo /etc/modules
```

---

### Post by wweeks on 2011-03-13
So I did that and nothing happens? I just copied and pasted it.
I went ahead and opened it again and its still read only.
I also tried sudo bash with no luck.

---

### Post by linuxopjemac on 2011-03-14
In a terminal:

```
su
```
(login as root with root password)
then
```
nano /etc/modules
```
add the line
CTRL-X and "y" to save

---

### Post by wweeks on 2011-03-14
Thank you so much! I ended up having to set a root password using the instructions I found here: [http://www.debuntu.org/2006/04/24/34-ubuntu-default-root-password-or-the-sudo-way](http://www.debuntu.org/2006/04/24/34-ubuntu-default-root-password-or-the-sudo-way) and then was good to go.

---

### Post by rsavage on 2011-03-17
Just in case there are any new users reading this thread, it probably should be pointed out that the approach taken in the above posts is frowned upon in Ubuntu.  See the sticky post in the security section [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

You should of typed "sudo gedit /etc/modules" to open the file with write permission.

If you had done a search on the battery problem before posting then you would have found a solution quicker and a more 'correct' approach.  When doing a search it is not a good idea to take the first answer you find, but try and work out the 'best practise' solution by finding other posts on the subject.  Also, I would limit the search to within a year otherwise the advice will be dated and probably wrong.

---

