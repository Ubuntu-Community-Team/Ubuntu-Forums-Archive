---
title: "Adobe Reader installation help"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Rob_EP on 2007-06-26
I'm trying to install Adobe Reader on Ubuntu (PS3) using the tar.gz file. I've extracted it and run the INSTALL file in terminal and followed the steps through, including using the sudo command to create a directory inside /usr. It says at the end that the installation is completed succesfully but I can't open Adobe Reader. It's on the applications menu under Office, but nothing happens when I try to run it.

Can someone help me, please?

---

### Post by Shutdownrunner on 2007-06-26
> **Rob_EP said:**
> I'm trying to install Adobe Reader on Ubuntu (PS3) using the tar.gz file. I've extracted it and run the INSTALL file in terminal and followed the steps through, including using the sudo command to create a directory inside /usr. It says at the end that the installation is completed succesfully but I can't open Adobe Reader. It's on the applications menu under Office, but nothing happens when I try to run it.

Can someone help me, please?

Why would you need Adobe Reader? Try installing **evince **under Gnome or **kpdf **(it's probably called like this) under KDE. Both of them use the same pdf engine so it's only a matter of your preference which one you choose.

---

### Post by moshuptrail on 2007-06-27
for Rob_EP - I thought Shutdownrunner's response was inappropriate.  Maybe he was asking a serious question, but it didn't come off that way when I read it.

There are numerous reasons to use the reader from Adobe.  I use it because it can search the internal text of the PDF.  I don't think Evince does that.  Adobe Reader also has easy-to-use controls for magnification and support for the tabs on the left that give access to the table of contents embedded in some PDF documents.

Having said that;
first, check in /usr/local/Adobe/Acrobat7.0

there should be 4 files there:
bin  Browser  Reader  Resource

If not, you had a problem with the install.
your command should have been:
$ sudo ./INSTALL

by default it installs to the directory above - you shouldn't have had to create it manually.  I think it asked me if it should create it and I said yes.

Try this command to verify that the version you are using was installed when you installed it and not at some time previous:
$ ls -l `which acroread`

Next, try running it from the command line:
$ acroread

see if you get any output in the terminal.  I don't - but mine works.

Still not working?  I'd try to re-install it.
I can start it from the Office menu and it starts right up.

repost with results

---

### Post by DSn0wMan on 2007-06-27
I just installed it from add/remove programs on the applications menu.

---

### Post by moshuptrail on 2007-06-29
That's odd.  Adobe is not listed on my Add/Remove programs.

---

### Post by seetho on 2007-06-29
> **moshuptrail said:**
> That's odd.  Adobe is not listed on my Add/Remove programs.

I think you have to activate the Multiverse repository for it to appear.

---

### Post by RomeReactor on 2007-06-29
Hi. The **acroread** package is available through the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories.

---

