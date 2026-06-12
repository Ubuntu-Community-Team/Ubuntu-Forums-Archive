---
title: "Wxmaxima not working need help"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Randy133 on 2007-07-23
I am new to ubuntu, I have been using it for about a week now.  I installed Maxima and it works.  I did not have to make the file. Good thing I dont know how,yet.  anyway I then installed Wxmaxima.  when I run it I get the error " while loading shared libraries: libwx_gtk2u_xrc-2.6.so.0: cannot open shared object file: No such file or directory"  I can not find any info on this lib file.
Can some one help?

---

### Post by ddrichardson on 2007-07-23
Where did you install from? I only ask because wxMaxima and associated libraries is in the repository and can be installed through synaptic.

---

### Post by Randy133 on 2007-07-23
I got the deb files from a link for the Maxima web page.  Can you tell me how to install from synaptic?  Also how can I uninstall what I have now?
Thanks
Randy

---

### Post by ddrichardson on 2007-07-23
To remove the old ones:

```
sudo dpkg -r packagename
```

However if it's only the libwx you might get away with just installing that.

Synaptic is located in System/Administration. Once run you'll see a pane on the top right. Click in this and type the name of what you need, in this case libwx and you should see the package you need.

Click on the box to the left and select install. If any other files are needed, you'll be told it needs to select other packages.

This is one of the two advantages of synaptic/apt-get:
1. Control is provided to allow a system that supports updates.
2. All the packages needed to run a given application are installed.

---

### Post by Randy133 on 2007-07-23
Thanks I un-installed the package I had and installed using Synaptic.  Maxima works though Wxmaxima, no problems.  Thanks for your help. :)

---

