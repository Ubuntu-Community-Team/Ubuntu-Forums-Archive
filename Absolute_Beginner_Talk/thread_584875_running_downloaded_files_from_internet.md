---
title: "running downloaded files from internet"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-21
hi,

I am sorry i'm repeating a started thread. Well anyways, i'm a ubuntu7.10 user and i don't really know for certain how to manually download a file from the internet. And i also need to know the extensions that gutsy doesn't have a problem running. I looked in other threads but no info was helpful for gutsy. and after downloading from the internet what the next step will be towards running it ,and the next, then the next step. i know I started a similar thread before but no info was really that helpful for gutsy so i'm just looking for new ones. 

Ty in advance.

:confused:

---

### Post by Qwerty_ on 2007-10-21
By manually download do you want to download a file from the terminal and not through your web browser?

you can do this simply with ```
wget
``` then the address to the file you wish to download.

---

### Post by mikeyphi on 2007-10-21
> **limac said:**
> hi,

I am sorry i'm repeating a started thread. Well anyways, i'm a ubuntu7.10 user and i don't really know for certain how to manually download a file from the internet. And i also need to know the extensions that gutsy doesn't have a problem running. I looked in other threads but no info was helpful for gutsy. and after downloading from the internet what the next step will be towards running it ,and the next, then the next step. i know I started a similar thread before but no info was really that helpful for gutsy so i'm just looking for new ones. 

Ty in advance.

:confused:

Normally clicking on the file starts the process and the file is downloaded to the Desktop. If it's Ubunto compatable - double click will install.
If you can state which files you are interested in - more specific advice about installing would be possible!
You should get answers to most questions here:[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

It's still applicable!!

---

### Post by beerfan on 2007-10-21
> **limac said:**
> And i also need to know the extensions that gutsy doesn't have a problem running.:

Ubuntu (and Linux in general) doesn't execute files based on their extension, like Windows does. Files which are executable have an attribute which allows them to be executed. If you right-click on a file and choose the "Properties" menu you will see a permissions tab. Click the "Execute" box for "Owner" and then the file will be executable.

If a file is not executable, Ubuntu will examine the file (both its contents and it's name) when you double-click it to try to guess what you want to do with it but it's best to make a file executable if you want to run it.

---

