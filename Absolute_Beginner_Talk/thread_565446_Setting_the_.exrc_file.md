---
title: "Setting the .exrc file"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by avip22 on 2007-10-02
Hey!

I have created a .exrc file on my Ubuntu 7.04 Desktop so that any files I edit using vi picks up those settings. But vi doesnt do it for me. I can set it within vi though. For e.g. :set nu
I also dont find any other .exrc file for VI

Is there a way this can be done on Ubuntu?

Thanks
Avi

---

### Post by dwhitney67 on 2007-10-04
Place your 'vi' (vim) configuration settings within ~/.vimrc.  These will be referenced each time 'vi' is started.

Btw, the "master" resource configuration file used by all users on the Ubuntu system is located at /etc/vim/vimrc.tiny (or vimrc if you are running the "full" vim).

If you do not already have it, I would suggest getting the "full" vim installed on your system using this command:

$ sudo apt-get install vim-full

And if you require a graphical interface:

$ sudo apt-get install vim-gnome

---

