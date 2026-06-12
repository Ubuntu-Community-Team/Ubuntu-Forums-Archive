---
title: "HPLIP 2.7.9 Install on Ubuntu"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by Miss Marvel on 2007-10-02
I am new to Linux so I need help badly.  I can usually find my answers on the forum.
Anyway below are the instructions from the HP site.  It sounds very easy, but!!!
I downloaded the file to my desktop.  How do I cd to my desktop and get this to work?
I downloaded the self extracting archive with installer

HPLIP Self Extracting Archive With Installer

This is an experimental release that packages a self-extracting installer together with the regular tarball. The self installer is know to work on the following distributions (see note 2):

    * SUSE Linux (10.0, 10.1, 10.2)
    * Fedora (3.0, 4.0, 5.0, 5, 5.92, 6.0, 6, 7.0)
    * PCLinuxOS (2006.0, 2007.0)
    * IGOS (1.0)
    * Ubuntu (5.04, 5.1, 6.06, 6.10, 7.04, 7.10)
    * Debian (2.2, 3.0, 3.1, 4.0, 4.0r0)
    * Mepis (6.0, 6.5)
    * Mandriva Linux (2006.0, 2007.0, 2007.1)

To use the self-extracting file, follow these steps:

   1. Download the file to a convenient location (e.g., home directory or desktop, etc).
   2. Open a console/terminal and cd to the download directory.
   3. Type in and run this command: 'sh hplip-2.7.9.run'

---

### Post by phidia on 2007-10-02
I wonder if that driver is already available..but to cd to the Desktop do >  cd Desktop/
You can type > ls 
to view the Desktop directory and then run the command as you've posted it.
(after each command is typed you need to press the <enter> key)

---

### Post by mhenriday on 2007-10-05
The [ **HPLIP 2.7.9**]("http://hplip.sourceforge.net/downloads.html") driver is, in fact, available, and after several attempts, I was able to use the «**Self-Extracting Archive with Installer**» to install it on my 64-bit machine, after running «**sh hplip-2.7.9.run**» in a terminal. What is more, my machine was able to recognise my **HP Photosmart 3210 All-in-One**, so I now have no difficulty printing documents directly from **Feisty** pages or, what to me is still more important, scanning in them to a file in a map. Thus, I no longer have to hop into my **XP** setup whenever I want to print or scan something, which feels wonderful indeed ! But I must admit the way **Xsane** handles the scanning process is not precisely the most intuitive I've ever encountered....

Henri

---

### Post by matchstich on 2007-10-06
i used that self installing option.

i guess it installed the way it was supposed to.

but, where did it go?

i can't find hplip any where.

shouldn't it show up under--system--admin?

thanks

---

### Post by fotno on 2007-10-06
You have to add it to the main menu with add/remove.then go to main menu and check it so it will show in administrator.Hope that helps,I had the same problem.

---

### Post by matchstich on 2007-10-06
thanks.

i went there .   on my next night off 

will have to search my system and find something to 

put in the command box to make it run.

---

### Post by mhenriday on 2007-10-08
**Matchstick**, after going to **add/remove**, checking the box next to **HPLIP Toolbox**, and then closing **add/remove**, click **System** &#8594; **Settings** &#8594; **Main Menu**. scroll down to and click **Settings** on the left, once again check the box next to **HPLIP Toolbox** on the right, and then close the **Main Menu**. A **HPLIP Toolbox** icon will now appear on the menu that opens when **System** &#8594; **Settings** is clicked. After clicking that icon, follow the prompts to setup a new device. When this has been done, you will gain access to a **HP Device Manager** for your **HP** printer/scanner. Note that (in my setup, at least) the scanning function is performed via **X-sane** ; i e, if one clicks «scan» under «Function» in the **Device Manager**, **X-sane ** opens and the scanning process is controlled via that programme....

Hope the above helps !...

Henri

---

### Post by cutlerite on 2007-10-10
my computer won't handle .run, how do I get that to go?

---

### Post by mhenriday on 2007-10-12
**Cutlerite**, do you mean that your computer couldn't execute «**sh hplip-2.7.9.run**» ? Just what happened when you tried to get it to do so ?...

Henri

---

