---
title: "Installing ATI driver"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by aslam92 on 2008-01-19
Hi First time poster. As well as first 3 hours using Ubuntu.
I'm currently trying to update my ATI driver for my x1300 mobility on my laptop.
I've found the driver online, and tried to install the file.
I ran it through the terminal window, but it says I need to run the installer as the super-user.

Can anyone help plz?

---

### Post by asmoore82 on 2008-01-19
if you are on a newer version of Ubuntu,
you can just use "System -> Administration -> Restricted Drivers Manager"

---

### Post by aslam92 on 2008-01-19
I tried that now it says 
"The software source for the package
 x-org-driver-fglrx 
is not enabled."

---

### Post by thelatinist on 2008-01-19
1.  System > Administration > Software Sources.
2.  Select all but the bottom check box (the one next to "Source").
3.  Close. It should ask you to update, click okay. *
4.  Try the restricted drivers manager again.

If it does not ask you to update in step 3, then go to Applications > Accessories > Terminal and type the following command at the prompt:

```
sudo apt-get update
```

Then try the restricted drivers manager again.

---

### Post by sloggerkhan on 2008-01-19
For you, it might be well worth having the latest driver.
The super user represents a user who is able to change his authority to that of root, or complete system administrator. This will be the first user you created on your system.
To run a command as super user, type 'sudo' previous to the command.
Otherwise your user will not have permission to write or access admin stuff on your computer.

Properly installing the latest ATI driver can be a slightly more complex process than just running the installer, though.

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) may help, thought I think some of the things listed for manual install are a little overboard.

---

### Post by asmoore82 on 2008-01-19
I highly recommend sticking with the ATI drivers provided by the Restricted Manager...

1. While the newer version from ATI  has added AIGLX/Composite support, overall performance has decreased.
2. If you install the package from ATI by hand; every subsequent update to your
kernel or xorg may well break ATI's package and cause you to re-install or config it.
This is _not_ a bug, this is _you_ venturing outside of the package manager;
you need to know the consequences before doing so.
3. Last time I checked, _neither_ the newest ATI _nor_ the Ubuntu package will allow
my laptop to suspend properly(the open source "radeon" drivers do though, so I know it's
an ATI problem); so no advantage there

---

