---
title: "Java"
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by _simon_ on 2006-03-16
I think version 1.5 is installed, at least automatix told me it was. However the menus list java 1.4 control panel (or something - at work can;t check)

How can I:

A) Check the version I have?
B) Remove 1.4 from the menu and add 1.5 in it's place?

---

### Post by Perfect Storm on 2006-03-16
Try this:

```
sudo update-alternatives --config java
```

and pick the java you want.

---

### Post by _simon_ on 2006-03-16
Thank you

```

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/lib/jvm/java-gcj/bin/java
*     3        /usr/lib/j2re1.5-sun/bin/java
 +    4        /usr/lib/j2se/1.4/bin/java

```

How do I remove the following?

"Java Plugin Control Panel (1.4)"
"Java Policy Tool (1.4)"

These are both in System -> Preferences

---

### Post by Perfect Storm on 2006-03-16
How did you install j2se? If you remove j2se that should solve the problem.

---

### Post by _simon_ on 2006-03-16
I don't remember but I have just removed it via Add Applications - thank you, it was obvious but I didn't think of it!

---

### Post by Perfect Storm on 2006-03-16
If you want a control center for java 1.5:

```
sudo gedit /usr/share/applications/java.desktop
```

add:

> [Desktop Entry]
Name=Java Control Center
Comment=Control of Java 1.5
Exec=sh /usr/lib/j2re1.5-sun/bin/ControlPanel
Icon=
Terminal=false
Type=Application
Categories=Application;System;


It will appear in Applications ---> System Tools

I've attached an icon if you want it to use with the control center.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=6318&d=1140529352[/IMG]

Save the icon and in the "Icon=" you give the link to it. eg. /home/<username>/my-icons/Java.png

Just remember that linux is case sensitive.

---

