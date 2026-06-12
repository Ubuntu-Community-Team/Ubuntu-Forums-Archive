---
title: "Newbie &amp; Synaptics Package Manager"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by jazzbo88 on 2008-03-30
I used Synaptics Pakage Manager to download a package titled "the Hardware Book," but cannot find the file anywhere on my system. Used Terminal to search directories; used Synaptics Mgr to view installed packages, but, despite having completely removed the package and re-installing, I still do not see it listed in the "Installed" category of Synaptics Mgr. Any suggestions as to how and where  to find this package??

---

### Post by pseudo-random on 2008-03-30
Have you tried typing ```
hwb
``` into a terminal?

---

### Post by jazzbo88 on 2008-03-30
Yes, but terminal cannot find the file no matter what search I try??

---

### Post by oldos2er on 2008-03-30
In Synaptic, right-click on the package and choose Properties, Installed Files, to show where files in the package are.

---

### Post by mali2297 on 2008-03-30
You can also see the file list [here]("http://packages.ubuntu.com/gutsy/all/hwb/filelist"). 

Try to open /usr/share/doc/hwb/html/index.html in a web browser.

---

### Post by jazzbo88 on 2008-03-30
:KS

Thank-you! I found the directory and will go from there.
\\:D/

---

### Post by jazzbo88 on 2008-03-30
> **mali2297 said:**
> You can also see the file list [here]("http://packages.ubuntu.com/gutsy/all/hwb/filelist"). 

Try to open /usr/share/doc/hwb/html/index.html in a web browser.

I was finally able to locate and load the file with your help--thanks a million!\\:D/

---

### Post by forrestcupp on 2008-03-30
Now you can make a menu item for it by going to System->Preferences->Main Menu.  You can make a menu item for it and point it to the file you found to open.

---

### Post by jamieboy on 2008-03-30
I have had a problem trying to update the recent tzdata08a file automatically. I get the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I then tried to enter synaptic manager and got the same error message.0

any thoughts :confused:

thanks

---

### Post by forrestcupp on 2008-03-30
> **jamieboy said:**
> I have had a problem trying to update the recent tzdata08a file automatically. I get the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I then tried to enter synaptic manager and got the same error message.0

any thoughts :confused:

thanks

Did you do what it says and open up a terminal and type
```
sudo dpkg --configure -a
```

---

### Post by jamieboy on 2008-03-30
thanks very much - I missed the 'sudo', I am very new to ubuntu. Even getting the syntax for the terminal program is taking me time.

---

### Post by forrestcupp on 2008-03-31
Yeah, I don't know why it doesn't say that in the error output.  Just know that almost any time you do something that has to do with the system, it's going to require sudo privileges.

---

