---
title: "Widgit symbol writer"
date: 2009-03-06
forum: Assistive Technology &amp; Accessibility
---

### Post by Movingon on 2009-03-06
Hi all,

I have recently swapped over to Ubuntu 8.10 from Vista and am well pleased with Ubuntu's stability and security.  I would be grateful if anyone knows if there is a Linux version of Widgit Symbol Writer for Windows like the one from [www.widgit.com](www.widgit.com)

I have tried running the Widgit setup.exe from within Wine emulator but that keeps failing with an invalid registration code.  If I use the same code on a Windows machine it installs with no problem.

I volunteer for a charity looking after adults with learning difficulties.  They have been given an over inflated quote for a Windows server etc. by an IT consultancy firm.  I would like to save them money by setting up an Ubuntu network on their existing hardware but it is the Widgit software that is currently holding me back as that will be required on most of the PC's. 

I dearly hope someone can help me here.

---

### Post by notlistening on 2009-03-07
A few options to try:

Wine can be very tricky. The best thing to try is going into your wine configuration and on the first page you have the windows version dropdown at the bottom of the page. This becomes a little bit of trail and error when your doing this but you can change it to each one and try to install. Usually the best result come from going backwards. From my experience the best results come from Win2k and win98 but do try them all.

The other thing to do is run wine from a terminal and see the output as this does give you good clues as to what the problem might be, sometimes.

eg $wine setup.exe

The next option depending on the frequency of use of this application. You can have a windows box running remote desktop and have one user at a time login from ubuntu and use the software, or there is the option to run a termnal server and have multiple user logins for as many concurent users as you might need at any one time running a Windows Server edition.

Lastly find an open source alternative. Which is ideal but i do not know of sorry.

Also if you wanted to get users familar with using a Ubuntu system before making the change from their winddows systems you can create a portable cygwin USB pendrive that can run a remote xserver login with sound. Making the move a little less gut wrenching for those win kiddies as they can drop back into windows at any time. This means that you have to have a semi good server running ubuntu depending on your concurrent users count.   

Tom

---

