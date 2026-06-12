---
title: "Ubuntu Freezing Up (again)"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by Jimmy9pints on 2008-02-10
Hello, I know this is a well documented problem, but I have searched the forums and still not found the answer. The biggest problem is I do not understand how to carry out the actions in the advice they give (sorry - I am an absolute beginner). 

And I have to be quick otherwise it will freeze again.

I have a GeForce 7300 LE graphics card and NVIDIA accelerated graphics card driver installed (according to the restricted drivers manager). 

Some questions:

1.In the answers to similar questions, people say to use the previous drivers. I guess this is the equivalent of roll-back in Windows - and but how do I do that in Ubuntu?

2.The also talk about RenderAccel and that it should be disabled in Xorg.config. Again, what is that and where can I access it?

3. What is 'X'?

I apologise as I know these are very basic questions - but I will learn because I really want to make a go of a windows free computing system. Point me to the relevent tutorials and I will learn myself. 

Thank you for any assistance!

Jimmy

---

### Post by spiderbatdad on 2008-02-10
[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

you can use the search tool to find files in your system. Places>>Search for Files. If you enter xorg.conf and select look in file system, you will get more than one entry, but clicking the files will help you get some relevance. In this case you would want /etc/X11/xorg.conf  all file names are case sensitive.

To edit basic text configuration files, the graphical text editor is fine. So, once you know the path to the file, you open the text editor with super user privileges: **gksu.** Gedit is the gnome graphical text editor. The command to edit /etc/X11/xorg.conf would then be:```
gksu gedit /etc/X11/xorg.conf
``` after making changes, save the file by clicking the little disk image. You usually would reboot for the new configuration to take effect. Although there are other ways to restart a session.

---

### Post by Jimmy9pints on 2008-02-10
Thank you for your advice! I will try that.

---

