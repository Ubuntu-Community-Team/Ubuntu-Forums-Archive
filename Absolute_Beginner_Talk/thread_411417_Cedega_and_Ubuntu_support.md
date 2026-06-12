---
title: "Cedega and Ubuntu support"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by tcebak on 2007-04-16
i installed cedega 6.0 and i disliked it. so i wanted to go back to an older version. so i went to synaptic package manger. i did a complete removal. then i went to install 5.2.3 with a .deb file. so it installed using the package manger. then i go to my applications and run cedega. .... a min later nothing happens. cedega won't open. i tryed running   
cedega
in the command line. and i get this error:

Traceback (most recent call last):
  File "/usr/lib/transgaming_cedega/Point2Play_gui.py", line 2371, in ?
    Point2Play_gui_ref = Point2Play_gui( Point2Play.Point2Play( config_file) )
  File "/usr/lib/transgaming_cedega/Point2Play.py", line 360, in __init__
    raise badConfigFile( _("Missing options %s") % e.value )
AttributeError: NoOptionError instance has no attribute 'value'


any clue how i can run cedega. or complety remove it?  thanks for the time!

---

### Post by paradoxchild on 2007-04-16
One thing to do is make sure you have the right package as it could be cedega-small, if so remove that using synaptic. Another way is this 

sudo dpkg -r package.name

put specific location for package.name if you still have the package on your computer.

Also I suggest for the future just to search the forums before making a post, i searched uninstall cedega and got multiple things with the same or almost same question. Hope this helps, if not just search the forums.

---

### Post by zixzix on 2007-08-25
try this
```
rm -f ~/.cedega*
```

---

