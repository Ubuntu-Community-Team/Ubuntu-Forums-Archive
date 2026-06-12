---
title: "Cannot get Gogh to run under 8.04"
date: 2008-05-29
forum: Art &amp; Design
---

### Post by sjones411 on 2008-05-29
Howdy, I absolutely love the drawing program Gogh ( [http://www.goghproject.com/](http://www.goghproject.com/) ).  I used to use it a ton on my old Tablet PC running 7.10.  However, I upgraded to a newer Tablet PC, and it is running 8.04.  I cannot seem to get Gogh to start now.  I rely heavily on this program and was hoping someone could share some insights.

Here's the code I get when I launch it:

```
Traceback (most recent call last):
  File "./gogh", line 31, in <module>
    from goghmain import GoghWindow
  File "/home/stu/Gogh-0.1.2.1/goghmain.py", line 35, in <module>
    from brushmanager import BrushManager
  File "/home/stu/Gogh-0.1.2.1/brushmanager.py", line 30, in <module>
    from settingmanager import *
  File "/home/stu/Gogh-0.1.2.1/settingmanager.py", line 27, in <module>
    import xml.dom.ext
ImportError: No module named ext

```

Thanks in advance!

---

### Post by meborc on 2008-05-29
i get the same problem... there used to be .deb files available in getdeb.net, but i checked and nothing for hardy :(

---

### Post by sjones411 on 2008-05-30
No one else has come across this problem?  I'd really like to get Gogh running again, it's a great piece of software.

---

### Post by ::: on 2008-06-01
Some quick googling turned up this: [http://blog.mypapit.net/2008/05/ubuntu-hardy-python-xml-error.html](http://blog.mypapit.net/2008/05/ubuntu-hardy-python-xml-error.html)

I dunno if this will help since I haven't updated to 8.04 myself, yet.

---

### Post by sjones411 on 2008-06-01
I found a solution!  Whoo!  There was indeed a problem in the Python XML code in Gogh.  To fix it, open up settingsmanager.py.  First, you'll want to comment out the line:

```
import xml.dom.ext
```

By adding a # sign in front of it.  Next, you need to go to the lines that read:

```
f = open(path, "w")
xml.dom.ext.PrettyPrint(doc, f)
f.close()
```

And then change it to read:

```
f = open(path, "w")
f.write(doc.toxml())
f.close()
```

That's all. ^_^;  Enjoy your tablet drawing once more.

---

