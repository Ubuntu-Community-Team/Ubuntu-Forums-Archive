---
title: "Wrong keyboard layout (Danish Macintosh)"
date: 2011-09-02
forum: Apple Hardware Users
---

### Post by Jach0 on 2011-09-02
I'm running Ubuntu 10.04 in a Virtual Machine on a Mac and I'm struggling with the keyboard layout called "Macintosh Danish".

I've tried every possible layout that has anything to do with danish and apple/mac within the keyboard settings but all the layouts are more like a danish windows-keyboard.

The danish keyboard layout on a Mac looks like this:
[IMG]http://www.gadgetguy.dk/mbadk.jpg[/IMG]

If you try to add the danish keyboard on your own system the differences should be obvious (i.e. "$")

A keys like "\" are accessed by alt+shift+7 and {} are accessed by alt+shift 8 and 9. 

Is there any way to fix this without needing to spend three days learning to manually remap the layout?

Thanks

---

### Post by bapoumba on 2011-09-02
You'll probably get more help in the Apple Users forum. So moved :)

---

### Post by linuxopjemac on 2011-09-03
in a terminal you might want to try (this is Debian way of doing things):
```
sudo dpkg-reconfigure keyboard-configuration
```

---

### Post by Jach0 on 2011-09-03
It says the keyboard-configuration is not installed and no info is available?

---

### Post by linuxopjemac on 2011-09-04
I am not an Ubuntu guy but I think there is a setting in the Menu somewhere to set the keyboard.

[https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)

---

### Post by kpete on 2011-10-04
This is not a reply, but a new request for a solution. I am running a pure Ubuntu machine, but since the Apple keyboard is by far the best, both aesthetically and functionally, that is what I want to use. My Unbuntu computer not only recognizes it as a Danish Apple Keyboard, it correctly informs me that it is the aluminum model. And then it could not care less and gives me a PC-keyboard anyway!
The system that does this must read a settings file that tells it what each key is supposed to do. I do not mind editing it manually, if only I knew where and how. 

I will appreciate help, thanks,

kpete

---

### Post by pfrandsen on 2012-01-01
I had the same issue. I found a solution here:

[http://howto.praqma.net/ubuntu/keyboard](http://howto.praqma.net/ubuntu/keyboard)

Remember to remove the .Xmodmap already in your home directory (I do not know if .Xmodmap or .xmodmap is the correct name - the guide above uses .xmodmap).

See also bug 910174
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/910174](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/910174)

---

### Post by Jach0 on 2012-01-02
Thank you pfrandsen.

I've tried saving the .xmodmap to my home folder but nothing happens after a reboot. I couldn't find a previous .xmodmap in my home folder either. Am I missing something obvious?

---

### Post by pauljwells on 2012-01-02
The file should be called .Xmodmap the upper case X is important!

See my answer to a previous poster...

[http://ubuntuforums.org/showpost.php?p=11473559&postcount=2]("http://ubuntuforums.org/showpost.php?p=11473559&postcount=2")

---

### Post by pfrandsen on 2012-01-02
My experience is that you can use .xmodmap, but if there is an .Xmodmap it takes priority.

---

