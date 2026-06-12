---
title: "Ubunto 6.06: Apache, PHP"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Srirangan on 2007-02-02
I just installed Ubuntu 6.06 Desktop on my laptop (Lenovo CoreDuo).

How do I configure/install apache, php and mysql so that I can begin work? :confused: 

Thanks!

---

### Post by kingmonkey on 2007-02-02
Applications > Add /remove, search for the packages you need and click install.

---

### Post by lamego on 2007-02-02
Or read [http://www.howtoforge.com/lamp_installation_ubuntu6.06](http://www.howtoforge.com/lamp_installation_ubuntu6.06)

---

### Post by Srirangan on 2007-02-02
I might risk sounding like an idiot, but I installed Ubuntu Desktop instead of Ubuntu Server. Is there any way I can run LAMP in my current installation?

---

### Post by kingmonkey on 2007-02-02
Yes, should be no different.

> For those who would like to run the LAMP stack on their personal desktops(for development and testing purposes for example), selecting a few packages will get all the required components installed. There is an easier way though: Select the LAMP task from the Synaptic Package Manager and install everything with a single selection:

    * Start Synaptic Package Manager, go to Edit -> Mark Packages by Task&#8230; and select LAMP Server from the list of options. Click OK and then click the &#8220;Apply&#8221; button on the toolbar.

This will install the default list of packages that are part of LAMP installation. I prefer to install additional packages too, like GUI tools to work with the databases. The following two commands will install LAMP and some additional packages related to it:

From [http://beans.seartipy.com/2006/11/14/installing-complete-lamp-stack-on-ubuntu-610edgy-eft/](http://beans.seartipy.com/2006/11/14/installing-complete-lamp-stack-on-ubuntu-610edgy-eft/)

---

### Post by Srirangan on 2007-02-02
Thank you. I managed a LAMP installation. God has been kind, so has Ubuntu! :)

---

### Post by waveslider on 2007-02-03
I followed all of the instructions referenced above up to the basic LAMP installation. Apache2 works fine, but PHP does not. When I click on a link to a PHP file/page, Ubuntu tries to open it with Gedit.

Is there additional configuration required?

---

### Post by Buck2348 on 2007-02-03
I don't know anything about PHP, but to choose which app opens a file, right-click the file, select Properties, Open With tab, Add, and select the new app.

Buck

---

