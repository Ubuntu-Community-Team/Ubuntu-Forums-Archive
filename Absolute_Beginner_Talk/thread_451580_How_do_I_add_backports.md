---
title: "How do I add backports?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by bcasanov on 2007-05-22
Hi,

I have just recently found out that a new version of Opera was released, version 9.21.  I was wondering, since Kubuntu/Ubuntu does not have it in its repositories, how I might get the deb repository for Opera without having to constantly download the deb from the Opera site whenever a new version is released. I also would like to have my programs updated to new versions, not just security updates and bug fixes for those programs.  In other words, I would like something like backports, which I heard can do feature and version updates for your programs.  If that is so, how do I implement backports or something similar that will allow me to update the versions of my programs from a central location like adept/synaptic?

---

### Post by bmartin on 2007-05-22
Try this [page]("http://www.debianadmin.com/adding-ubuntu-repositories.html").

If you don't want to edit the text file by hand, scroll down to the section **Adding repositories Using Synaptic package management**.

---

### Post by bcasanov on 2007-05-22
That page lists the backports repositories for dapper, not feisty.  What would be a more updated repository list for feisty?

---

### Post by bmartin on 2007-05-22
I don't think Feisty has backports. It's the current version.

Backports are packages that are built to support older versions of the OS, if I'm not mistaken.

---

### Post by irish_flu on 2007-05-22
Here's how to turn on backports using Synaptic in Feisty (7.04)

Go to System ---> Administration menu and open up Synaptic Package Manager.

When it opens, go to settings ---> Repositories.

Click the "Updates" tab.

There, you'll see a section called "Ubuntu Updates".  Click the checkbox next to "Unsupported Updates (feisty-backports)".

That's it, you're done!

---

