---
title: "Configuring cups-pdf.conf for &quot;Save to..&quot; dialog"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by mph66 on 2006-10-24
OK.  I want to print to PDF, so I followed the directions here: [http://ubuntuos.com/2006/03/howto-set-up-a-pdf-printer](http://ubuntuos.com/2006/03/howto-set-up-a-pdf-printer) and they work just fine.  But I'd like to configure the /etc/cups/cups-pdf.conf file so that when I print to PDF, I'm greeted with a dialog asking me where to save my print job to.  By default, the current method only allows for .pdf print jobs to go to a folder in my home folder called "PDF".  I've got cups-pdf.conf open and I'm looking at the line I need to edit:

Out ${HOME}/PDF

But I don't know the command is to call a save dialog.  If anyone can lend assistance, I'd be grateful.

Thanks,

-Marc

---

### Post by mph66 on 2006-10-25
any help out there?

::bump::

---

### Post by oleksa on 2008-06-16
> **mph66 said:**
> any help out there?

::bump::

Cups cannot provide the dialogue, the dialogue can be given by Gnome/KDE/XFCE or other graphic environment manager. So you can only use the string Out or directly saying to save the output to the file in the print pop-up window.

Here you can find some discussion regarding this cups-pdf so-called 'bug' [https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/158406](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/158406) :-)

---

### Post by PmDematagoda on 2008-06-16
oleksa:- While your post would have been helpful, you are replying to a thread that is more than 2 years old in which case it would be worthless.

This thread is closed.

---

