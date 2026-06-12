---
title: "blacklisting?"
date: 2006-10-16
forum: Absolute Beginner Talk
---

### Post by thewatts on 2006-10-16
so im in the process of trying to get my wusb54g v4 wireless adapter working. i found a thread that gives step by step instructions on how to do so, the first instruction being to edit the blacklist file,

code:

$sudo gedit /etc/modprobe.d/blacklist

---

then add "blacklist rt2570" to the blacklist file.

the problem i'm running into - is that i cannot save the blacklist file. ubuntu tells me i do not have the access to save the file. i made a clean ubuntu install an hour or so ago -- and have admin privs on my user profile.

any suggestions?

thanks

---

### Post by jordanmthomas on 2006-10-16
I don't know what the deal with that is.
Try
```
gksu gedit /etc/modprobe.d/blacklist
```
When running GTK apps, using gksu instead seems to help a lot.

(just as another hint, if you're just adding one line to a file, use an editor like nano because it is a lot faster)

---

### Post by morequarky on 2006-10-16
I would:

"sudo joe filename" and see if I could save it that way.

---

### Post by jordanmthomas on 2006-10-16
joe is not installed by default in Ubuntu.

---

### Post by chuckyp on 2006-10-16
You need to edit the file as a system administrator or "root".  The easiest way to do this would be via terminal or Alt+F2 to open a run dialog and type in "sudo gedit /name/of/file" .  Make the necessary changes and save the file.

---

### Post by jordanmthomas on 2006-10-16
```
sudo gedit /name/of/file
```
in the Alt + F2 box would not work because there would be nowhere to enter your password.
gksu is the way to go if using the Alt + F2 box.

(also, he was already editing using sudo according to his post)

---

