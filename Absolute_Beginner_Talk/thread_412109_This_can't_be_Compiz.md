---
title: "This can't be Compiz"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by OpEn_SoUrCe_RoCkS on 2007-04-17
I installed compiz.

It messed up my KDE !

It removes the titlebar !

Am I doing something wrong ?

---

### Post by compmodder26 on 2007-04-17
What video card do you have?

---

### Post by H.E. Pennypacker on 2007-04-17
Have you tried switching to Beryl?  Beryl is more up to date, and it also offers its own support forums.

---

### Post by OpEn_SoUrCe_RoCkS on 2007-04-17
Beryl isn't in my package manager. Do i have to downlaod it ^

I have a nVidia.

---

### Post by kodoku on 2007-04-17
I do believe that the compiz in the default repositories (you're running edgy, I'm assuming) is very outdated.

I second the suggestion for beryl.

First you have to install your nvidia drivers (I suggest [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"))

After that's over with, pull up a terminal and run 

glxinfo | grep direct

If the result is "Direct Rendering: Yes", then move on to this [guide]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX")

---

### Post by compmodder26 on 2007-04-18
This problem shouldn't have anything to do with Beryl vs. Compiz.  The OP would most likely have the same problem with Beryl as well.  A quick search on the foums should reveal many users having the same problem with their Nvidia cards.  This problem should be fixable by following the instructions here: [http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#My_windows_don.27t_have_any_decorations_.28title_bar.2C_resize_handles.2C_minimize.2Fmaximize.2Fclose_buttons.29](http://wiki.beryl-project.org/wiki/Troubleshooting_nVidia#My_windows_don.27t_have_any_decorations_.28title_bar.2C_resize_handles.2C_minimize.2Fmaximize.2Fclose_buttons.29)

The one that has always worked for me is number 5.

---

