---
title: "Major screen Issues help."
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by superarmy on 2008-01-03
When I boot up Ubuntu, I've been doing so with out problems for nearly a month now, the login screen is now, blurred beyond readability. I can login in using memory but I will not be able to access any menus, due to the fact I can not see a legible word on the screen. If I'm going to make changes to the system, (i think its a graphics card problem), I will have to do it in recovery mode, unless their is a key combination I can press at the login screen to make it legible. Any help would be much appreciated.

---

### Post by superarmy on 2008-01-03
Bump please help.

---

### Post by metalpancake on 2008-01-03
are you sure you have the right drivers for your video card?

---

### Post by superarmy on 2008-01-03
Like I said, I have been using Ubuntu for about a month now, and it all worked fine.

---

### Post by superarmy on 2008-01-03
Bump please help, is tehre anyway, while in recovery mode, I can restore my graphics card to its normal settings, I had been trying to get the desktop effects working, maybe I made an error in the values, can I do anything in recovery mode to correct this.

---

### Post by zhouxing on 2008-01-03
> **superarmy said:**
> Bump please help, is tehre anyway, while in recovery mode, I can restore my graphics card to its normal settings, I had been trying to get the desktop effects working, maybe I made an error in the values, can I do anything in recovery mode to correct this.

Try to use latest Envy to reinstall your display card driver, if you have a Nvidia or ATI card.

But if you are with ATI AND you installed latest ATI driver 8.44.3, you are likely to have screen resolution problem.

---

### Post by superarmy on 2008-01-03
How do I go about installing the latest ATI driver, I would have to do it in recovery mode.

---

### Post by superarmy on 2008-01-03
Bump please help

---

### Post by dotexe on 2008-01-03
Did you try using Envy?

What is Envy?:

"Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (only ATI and Nvidia cards are supported) and install the appropriate driver. However automatic detection can be overridden with the "Manual installation"
2) package the driver that comes with ATI or Nvidia's installer (from their respective websites)
3) install all you need to package and install the driver
4) configure the Xserver for you

Envy features both a GUI (which you can launch only inside a Desktop Environment) and a textual interface which you can use if, for example, you cannot start the Xserver.

First try using envy and see if that works out.

---

