---
title: "Disabling the Desktop Icon, and adding a &quot;Filesystem&quot; Icon"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by Ameeya on 2006-12-19
Hello!

I have been using Ubuntu for a few months now, and absolutely love it!  I have been lucky enough to not have had too much trouble enabling my Wireless Connection, or Beryl (Amazing that my computer which will not be capable of Aero effects in the new Windows, is super smooth while running the same transparency effects in Ubuntu!)

Anyways, I just have two simple questions.  Firstly, I find the behavior of the Desktop icon a little confusing.  When I double click on the desktop icon, I am led to  two icons that I have on my desktop, Home, and Terminal.  When I double-click on the Home Icon, I have my home folders, and...the Desktop Icon!:-k   How does that work?  Is there any way that I can stop the icon from appearing in Nautilus when I am in the home directory?  Like simply hiding the icon or disabling some option.

Secondly, I have Ubuntu installed on my hard drive along with Windows.  The "root" or however it is called, Filesystem.  I would like to have the icon for this on my Desktop.  Is there a way for me to get my Icon for Filesystem on the Desktop?

Thanks for any help in advance.:D

---

### Post by jrib on 2006-12-19
1) You can create a .hidden file in a directoy and list anything you want hidden in there.  Then nautilus won't display it.

For example to hide the Desktop folder when I am viewing HOME, I would:
```
echo "Desktop" >> ~/.hidden
```

Or use your favorite text editor.  The end result should be a file (~/.hidden) that contains the word "Desktop" on a single line.

2) Anything you mount in /media should show up on your desktop by default.  Here's the guide on mounting windows partitions: [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by Ameeya on 2006-12-20
Great!  Thanks for the help.

---

