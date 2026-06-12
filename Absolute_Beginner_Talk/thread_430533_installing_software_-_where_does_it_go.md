---
title: "installing software - where does it go"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Preserved_Killick on 2007-05-02
When I install some software package, where does it all go? 

You know, in Windows, the application will put stuff everywere:  Registry, folders here and there, files in the Win32 directory... 

Then, when uninstalling the apps, sometimes not everything is removed. Do this often enough and Windows gets very messy.

With Ubuntu, where does everything go? Can I safely try out software packages, remove them and  be sure nothing remains? 

Thanks,

Preserved

---

### Post by GrueTamer on 2007-05-02
> **Preserved_Killick said:**
> When I install some software package, where does it all go? 

You know, in Windows, the application will put stuff everywere:  Registry, folders here and there, files in the Win32 directory... 

Then, when uninstalling the apps, sometimes not everything is removed. Do this often enough and Windows gets very messy.

With Ubuntu, where does everything go? Can I safely try out software packages, remove them and  be sure nothing remains? 

Thanks,

PreservedI'm not sure if where your current directory is when you get things from apt matters (if you don't know what that means, then this probably doesn't apply to you) but all of my stuff is in my /home directory.  Press ctrl+h to unhide the folders that have these applications in them.

Oh, and deleting things should be fine

I hope that helped!

---

### Post by Sef on 2007-05-02
> With Ubuntu, where does everything go? Can I safely try out software packages, remove them and be sure nothing remains?


If you install via Add/Remove or Synaptic or the terminal, everything can be removed.

---

### Post by 3rdalbum on 2007-05-02
Linux programs do install all over the place - usually many subfolders inside /usr, but very often in /var and /etc as well. When you start the program, it is likely to put its preferences inside hidden folders in your home directory.

Deleting programs is easy too; just go into Synaptic and tell it to "Mark for Complete Removal". On the terminal, you'd put "--purge" into the command.

---

### Post by Tomosaur on 2007-05-02
Yes, if you add things via Add/Remove or Synaptic, then you can remove anything that is installed.

If you install things from source (ie, compile them yourself), and make them system-wide, then you need to keep the source directory around so you can type 'sudo make uninstall' in the command line, which uninstalls the program. However, if you only installed the program to it's own directory, you can just delete that directory. There's no registry in linux, so you don't have to worry about that.

---

