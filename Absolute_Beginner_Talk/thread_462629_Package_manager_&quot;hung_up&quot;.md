---
title: "Package manager &quot;hung up&quot;"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by the_rajah on 2007-06-02
By that I mean that I attempted yesterday to install VirtualBox virtual machine by simply clicking on [http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_feisty_i386.deb](http://www.virtualbox.org/download/1.3.8/VirtualBox_1.3.8_Ubuntu_feisty_i386.deb) and when the window came up to ask me what I wanted to do with it, I said to open it using the Gdebi package installer. 

It started the installation process and I went off to do other things. When I came back later it was still installing. I thought, "OK, this is just a long process." and went to bed. It was still doing it this morning so I "X"ed out of the installer and went on about my business online.  Later, I noticed the little icon indicating that there were updates, but when I attempted to do updatess, I got a message that said,

"[I][B]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.[/B][/I]' "

I attempted to restart the installation, but got the same message again. I'm stumped, which at this point in my Linux career is not hard to do.

BTW, I'm running 7.04 on a shiny new Dell E520N with Ubuntu pre-installed that arrived at my doorstep yesterday!  I've been running it previously on some old P-IIIs so this is really slick...up until now.  HELP!! :confused:

---

### Post by Seisen on 2007-06-02
Try this in the terminal

```
sudo dpkg -i VirtualBox_1.3.8_Ubuntu_feisty_i386.deb
```

its the same thing as using Gdebi but it is how to install a .deb file through the command line.

---

### Post by the_rajah on 2007-06-02
Thanks, Seisen.  I tried that and got:

[I][B]dpkg: error processing VirtualBox_1.3.8_Ubuntu_feisty_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 VirtualBox_1.3.8_Ubuntu_feisty_i386.deb[/B][/I]

That file is in /tmp where it downloaded when I did the first attempt. I just looked to make sure it's still there.  Should it be somewhere else? This has me hung up so I can't even do normal updates. At this point, I'd be happy to forego VirtualBox and get my update manager working.

---

### Post by Seisen on 2007-06-03
When you tried that did you to it from the /tmp directory?

---

### Post by the_rajah on 2007-06-03
OK, that worked after sweating a little over some error messages along the way that I worked through. 

Thanks!   Isn't a community a great thing?

---

### Post by Seisen on 2007-06-03
That seems to be a common problem with VirtualBox and the only solution that seems to work.

---

