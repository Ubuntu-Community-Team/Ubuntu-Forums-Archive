---
title: "Kubuntu will not boot"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by mudflap5 on 2007-07-19
Well, after several weeks of working great, Kunbunu will not boot up all the way, it hangs on the splash screen.  The last thing I did before this problem occurred was to connect a second monitor, go into the display properties, enable 2 monitor support and click " apply ". It said to restart, so I did. It shut down, but would no boot back up.  I can get to the recovery mode, but not sure what to do next.  Thanks for any help.

---

### Post by Sandlst on 2007-07-19
I would do a ```
sudo dpkg-reconfigure xserver-xorg
```In this situation.  If you have never done it before, the default options are usually safe.  If you don't know which video driver to use, "vesa" is the one I believe is guaranteed to work, with the trade-off of bad performance.  Still, doing this should allow you to log in again, and fix your system from there.  After you do this typing ```
exit
```will bring you to the KDM I think.  Good luck, post back if you have any problems.

---

### Post by mudflap5 on 2007-07-20
Thanks, that took care of the problem.
In a effort to better understand the inner workings of this OS,  would you care to briefly explain what happened when I entered in the command you suggested?

Thanks Again !!!

---

### Post by Lord_Dicranius on 2007-07-20
"dpkg-reconfigure" allows you to reconfigure an already installed package.

**UPDATE**
And as luck would have it, Linux.com had this article up today!

[Editing basics for the xorg.conf file](http://www.linux.com/feature/118108)

---

