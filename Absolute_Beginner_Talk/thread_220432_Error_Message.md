---
title: "Error Message"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by demon_devon on 2006-07-21
When I attempt to open any of the office applications like OpenOffice.org Database I get an error message stating:

Could not launch menu item

Details: Failed to execute child process "ooffice" (No such file or directory)


What does that mean exactly and what can I do to fix this error?

---

### Post by tuxinvader on 2006-07-21
It means that nautilus can't find the helper application associated with that file format.

Check you have open-office installed either in synaptic or by running:

sudo dpkg -l openoffice.org

you should see a line like:

+++-==============-==============-============================================
ii  openoffice.org 2.0.2-2ubuntu1 OpenOffice.org Office suite version 2.0

If it oesn't have ii at the begining there's something wrong with your installation of OO. You caould try running:

sudo apt-get install openoffice.org

HTH

---

### Post by Tamib on 2006-07-21
> **tuxinvader said:**
> It means that nautilus can't find the helper application associated with that file format.

Check you have open-office installed either in synaptic or by running:

sudo dpkg -l openoffice.org

you should see a line like:

+++-==============-==============-============================================
ii  openoffice.org 2.0.2-2ubuntu1 OpenOffice.org Office suite version 2.0

If it oesn't have ii at the begining there's something wrong with your installation of OO. You caould try running:

sudo apt-get install openoffice.org

HTH


How do I run sudo dpkg -l openoffice.org?  I am very unfamiliar with this system so I am unclear on how to run what you perscribed.  Thank you.

---

### Post by nickpaton on 2006-07-21
Hi Demon_Devon & Tamib & Welcome to the Ubuntu Forums!

You need to type the commands into a Terminal, which can be opened as follows:

Click on Applications (By default at top left hand corner of the Desktop).

Select Accessories > Terminal

When the Terminal screen opens you will see a single command.  Mine is:

```
nick@nick-laptop:~$
```

After the "$" symbol type (or better to copy / paste from the post):

```
sudo dpkg -l openoffice.org
```

Note that a lot of your work will be via the Terminal, so I would suggest creating a shortcut for it onto your Desktop.

Once again navigate to it, and right click and select "Add this launcher to Desktop"

Hope this helps & let us know how you get on.  By doing this you help others.

(Edit spelling and Name omission - apologies Demon_Devon!)

---

### Post by Tamib on 2006-08-10
Thanks it worked wonderfully.  :)

---

