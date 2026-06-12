---
title: "No Administration"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by dgreenu on 2007-01-18
Administration Under System Is No A Choice.  I Am Logged In As The Person Who Install The Os.  I Need To Install Printer Etc.

---

### Post by taurus on 2007-01-18
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by welshboy on 2007-01-18
Hey buddy, 

I'm not sure I've got the jist of what you've said, but I'll bravely soldier on.  You don't need to be an admin user to install a printer. 

I'm going to assume you're using Ubuntu.  (The Gnome version)

To install a printer you do the following.

On the top menu bar, click on System, and then Administration.

Then click on Printing.

Now a window will pop up, click on add new printer, and the cups data base should load up all the printer drivers. 

You then need to tell the program if it's a local printer, that is, is the printer connected directly to your computer. (I'm assuming it is).

Once you've done that, there will be an option on the bottom to specify another port.  You want to point the printer port to LPT1.

Then click on OK or Next, and then select the printer you wish to install.  There'll be a manufacturer list on the top, click on that and find who made the printer, then in the main list, select the model number.

Once you've done that, at the bottom of the screen there will be another drag down list box, with a list of drivers.  Select the appropriate driver from that.  (If there's more than one choice, select the one that has the model number of the printer on it.)  Then click Forward.  

It will then ask you to give your printer a name and a description.  Give it a useful name, and click on Apply, and Voila, one printer installed (I hope)

Any troubles, drop me a line :)

---

### Post by jvc26 on 2007-01-18
Its to do with the fact that linux does not as default log you in as the administrator that stops things like viruses running havoc with admin privileges as is often the case in the old scheme of windows logins. See taurus' post for more information on how to use sudo or gksudo to allow you to install things as the root without logging in as the admin.
Il

---

