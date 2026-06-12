---
title: "Many problems..Cant install anything"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2008-03-07
I have Several problems, all errors that refuse to let me install any programs:

A.  Get an error saying /usr/share/icons/high constrast large print is not a directory
B.  DPKG: error processing epiphany browser data-remove subprocess-post removal script returned error exit 2
C.  Subprocess returned an error code 1

Is it as bad as I think where the os must be reinstalled?  I just have the Mac to linux theme saved

---

### Post by sports fan Matt on 2008-03-07
Also, a Sudo apt-get install -f gets those errors

It seems like i have a broken epiphany package and need to get rid of it, but when I try to correct it it doesnt work...

Any other ideas?

---

### Post by sports fan Matt on 2008-03-07
Would a DPKG -- configure -a do anything?

---

### Post by spiderbatdad on 2008-03-07
```
sudo dpkg --purge -a
``` should remove packages and configuration files of packages you've marked for removal or attempted to remove unsuccessfully.

---

### Post by sports fan Matt on 2008-03-07
that command returned the same set of errors...got me this one: 
 /usr/share/icons/high contrast large print is not a directory

---

### Post by Mud.Knee.Havoc on 2008-03-07
The spaces in the directory name are probably messing it up.

---

### Post by bodhi.zazen on 2008-03-07
You could try making a directory and see if that is sufficient :

```
sudo mkdir "/usr/share/icons/high contrast large print"
```

---

### Post by Mud.Knee.Havoc on 2008-03-07
I've got a /usr/share/icons/HighContrastLargePrint directory.

---

### Post by sports fan Matt on 2008-03-07
Why then would it bork installing all my programs? And am i right about the fact i cannot install Firefox /remove epiphany correctly?  

The good news:  All my files/extensions/themes in the mozilla Firefox directory are entact, cant install Firefox though cause of the /usr/share/icons/high contrast large print is not a directory
B. DPKG: error processing epiphany browser data-remove subprocess-post removal script returned error exit 2
C. Subprocess returned an error code 1..errors..Somehow (Im not sure) but are they all related/do i have 3 seperate issues?

Am i on the right track and how bad is it?

Thanks for all the help!

---

### Post by spiderbatdad on 2008-03-07
sounds like you tried to install a source package designed for a different linux distro...like using alien to install an RPM. Sounds like the theme or icons package is referencing a directory that goes by another path/name in Ubuntu. I'm just guessing. That's what you get for trying to make a beautiful Ubuntu installation look like a mac! Just kidding. there are other commands you can try to fix the problem: ```
sudo dpkg -C 
```might help. This should run an audit of packages and offer solutions. Read ```
man dpkg
``` to get an idea of other possibilities, such as dpkg -R on the package name to configure with directories. Also learn about checkinstall for the future, to make packages you can easily remove when you are installing source instead of deb.[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by sports fan Matt on 2008-03-07
I'll just reinstall i think..Doesnt take long and i have everything backed up so its easy...:)

---

### Post by daze77 on 2008-03-08
hi 
i have found a great site where you can download most disc ie for a re install... boot disc and recovery cds
 [http://www.user-guides.co.uk/](http://www.user-guides.co.uk/)
hope this helps

---

### Post by handy on 2008-03-08
> **daze77 said:**
> hi 
i have found a great site where you can download most disc ie for a re install... boot disc and recovery cds
 [http://www.user-guides.co.uk/](http://www.user-guides.co.uk/)
hope this helps

They want money!

---

### Post by AndyCooll on 2008-03-08
> **daze77 said:**
> hi 
i have found a great site where you can download most disc ie for a re install... boot disc and recovery cds
 [http://www.user-guides.co.uk/](http://www.user-guides.co.uk/)
hope this helps

Interesting, but not really necessary for Linux I wouldn't have thought since you can do most recovery and reinstall tasks using the original Ubuntu Live CD. And if you really need extra assistance there's always something like the systemrescuecd. However, I gather from the OP's wording that they don't consider this to be drastic enough for such measures to be necessary.

:cool:

---

