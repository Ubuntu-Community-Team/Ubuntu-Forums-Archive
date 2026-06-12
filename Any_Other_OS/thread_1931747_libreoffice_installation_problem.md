---
title: "libreoffice installation problem"
date: 2012-02-26
forum: Any Other OS
---

### Post by jakelong00 on 2012-02-26
i wanted to have libre office instead of openoffice on my mint 10 so i dwonloaded the deb file from its site.
i  removed openoffice and installed libre just liike the way they have  told on their site. but now none of the office application opens up and  whenever i try to remove it or install anything new i get the msg
-----------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package libreoffice3.5-dict-en needs to be reinstalled, but I can't find an archive for it.
-----------------------------------
how to get rid of it??

---

### Post by rewyllys on 2012-02-26
> **jakelong00 said:**
> i wanted to have libre office instead of openoffice on my mint 10 so i dwonloaded the deb file from its site.
i  removed openoffice and installed libre just liike the way they have  told on their site. but now none of the office application opens up and  whenever i try to remove it or install anything new i get the msg
-----------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package libreoffice3.5-dict-en needs to be reinstalled, but I can't find an archive for it.
-----------------------------------
how to get rid of it??
I suggest, first, adding the LibreOffice PPA to your list of repositories.  

To do this, open the Synaptic Package Manager, and click on Settings > Repositories > Other Software > Add.  Then enter the following in the "Add" window:
```
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu oneiric main
```
replacing, if necessary, "oneiric" by your version.  

When you've done that, you can use the Synaptic Package Manager to remove LibreOffice 3.5.

---

### Post by pickarooney on 2012-06-10
I'm having this problem since trying to update to LibreOffice 3.5 today. The same error message about dict-en appears.

I've tried reinstalling, uninstalling, purging, adding the PPA, but I just keep getting the same error and synaptic will not start up.

---

