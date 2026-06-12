---
title: "Help!!! Icon Theme Problem"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by richyrich on 2007-01-27
Hello all,

I made the stupid, stupid, stupid mistake of accidentally installing a X11 mouse cursor theme set where one would normally install Gnome Desktop Themes.  I restarted the system, and now Gnome will not even run (I'm assuming because of the icon theme problem).  Would anybody know how to change the icon theme set from a command prompt in safe mode?  Alternatively, I just need to copy one set of files to a usb key chain drive that is stored on my desktop (i.e. what commands should I type to move /home/rootuser/Desktop/ZZZ to a USB key chain device).  If you could tell me how to make that copy, I could reinstall ubuntu and obviously be a lot more careful in the future.  Thank you in advance for your help!!!

Rich

---

### Post by BarfBag on 2007-01-27
I don't see how installing a mouse cursor the wrong way could cripple your XORG, but things happen.

Insert your USB drive and reboot (I'm not sure whether or not it will auto mount it or not - but it should pick it up on a reboot).  CD to the media directory.  This is done like this:

> cd /media

Then, type:

> ls

That will list the contents of the directory.  Since the media directory has your mounted drives in it, it will list those.  I'm not sure exactly what your USB drive will be called, but you should know it when you see it.  Write it down.  Then, CD to your desktop, like so:

> cd /home/yourusername/Desktop

Then, one last command:

> mv ZZZ /media/nameofusb

That should do the trick.

---

### Post by richyrich on 2007-01-27
Thanks, will give it a shot!

---

### Post by richyrich on 2007-01-27
Ok, tried your suggestion, but when I inserted the usb device didn't light up (and didn't show up as a device in cd /media)...  Do you know of any way of copying a file from /usr/share/icons to GTK theme manager?  I have a feeling if there was a way of just putting a different icon set in GTK, I would fix my problem.  Thanks again for your help!

Rich

---

### Post by ComplexNumber on 2007-01-27
or you could just change the icon theme here:
/home/<your-username>/.gconf/desktop/gnome/interface. edit the icon_theme in there. change it to something like 'Human'.

---

### Post by richyrich on 2007-01-27
ComplexNumber,

Thanks.  I think that's the solution I'm looking for.  What would you suggest in terms of edits (sorry I am really new to this) to get things functioning again?

Thanks again,

Rich

---

### Post by ComplexNumber on 2007-01-27
>   What would you suggest in terms of edits (sorry I am really new to this) to get things functioning again?
i don't understand what you mean. edits for what, exactly?

---

### Post by richyrich on 2007-01-27
Sorry, I'm completely incompetent working in terminal or from the command line.  You suggested editing the icon theme, but I don't know exact what that would entail.  In other words, I could navigate to that directory from the command line, but then would have no idea of how to change things over to another icon theme.  Is there some chain of commands you could suggest for actually editing the icon_theme file to something else (i.e. the human icon set)?

Thanks,
Rich

---

### Post by ComplexNumber on 2007-01-27
i know its not the most friendly editor of all, but you could use an editor called nano to edit it. it will be on your system. just type in 'nano'.

---

### Post by richyrich on 2007-01-27
Ok, back in action, I'm writing this from Ubuntu so all is well for now!  Thanks again for your help...

---

