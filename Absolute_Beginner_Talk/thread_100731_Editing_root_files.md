---
title: "Editing root files"
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by Evilchicken on 2005-12-08
Is there a way to edit files owned by root by using sudo?

---

### Post by ChrisTheGeek on 2005-12-08
Yes, that's the purpose of sudo.  Check here for more info:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Chris.

---

### Post by canadianwriterman on 2005-12-08
There are two ways to edit a file with root privileges:

Open a terminal window and type **sudo gedit nameoffile**

This will open the file in a text editor and allow you to save the file when your editing is complete.

The second method is to use the **Open as a different user **utility under **Applications > System Tools **and enter **Nautilus**. This will allow you to navigate to the file using Nautilus, open, edit and save the file.

Hope this is helpful

---

### Post by Evilchicken on 2005-12-08
Thanks. All I had done with sudo is attempt to install XMMS.

---

### Post by Evilchicken on 2005-12-08
[QUOTE=canadianwriterman]There are two ways to edit a file with root privileges:

Open a terminal window and type **sudo gedit nameoffile**

Hope this is helpful[/QUOTE]
Thats what I was looking for :D Thanks!

---

### Post by 23meg on 2005-12-08
You may be interested in [this trick]("http://www.ubuntuforums.org/showthread.php?t=24008").

---

### Post by Evilchicken on 2005-12-08
Actually, I saw this thismorning and im planning on trying it when I get home!

---

