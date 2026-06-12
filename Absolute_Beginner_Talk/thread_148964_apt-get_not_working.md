---
title: "apt-get not working?"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by Ancalagon on 2006-03-23
Thanks ahead of time for your patience.

I'm not sure if I'm using apt-get correctly.  I've tried it a couple times and each time I get the same response:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package imwheel

This particular time I was trying to follow this how-to:

[https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons](https://wiki.ubuntu.com/IntellimouseMousemanBackForwardButtons)

When this didn't work I tried:

apt-get update

A bunch of sources were found, but this didn't change the results of my attempt to install imwheel.  What's strange is I found the package imwheel here:

[http://packages.ubuntu.com/breezy/utils/imwheel](http://packages.ubuntu.com/breezy/utils/imwheel)

Am I doing something wrong?  Why wasn't apt-get able to find this package on Ubuntu's package site?

Thanks all!

---

### Post by pitr on 2006-03-23
I'm guessing the problem is that you don't have universe enabled. 
To enable it do the following


> Adding *universe* to your Ubuntu system will give you access to many more packages.[LIST=1]
[*]Select the **System** menu at top of screen, then **Administration** then **Synaptic Package Manager**.
[*]When the program starts, click on the **Settings** menu, and select **Repositories**.
[*]In the new dialog that opens, click the **Add** button on the right side of the dialog.
[*]The **Edit Repository** dialog will come up. Check the box that says **Community maintained (Universe)**.
[*]Click **OK** to add the new repository
[*]Click **OK** to close the Repositories dialog and save your change.
[*]Synaptic will then prompt you to refresh your package database. Once this is complete, you will be able to install packages from *universe* on your system.[/LIST]

---

### Post by Ancalagon on 2006-03-23
Sweet!  Thanks much!!

---

