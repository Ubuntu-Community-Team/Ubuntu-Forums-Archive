---
title: "Is Global Copy Possible?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by farang on 2007-06-22
Dear forum,

I am wondering how I can configure Feisty to make copy&paste possible from one application to another, even after the source application is terminated.

If I select "Dear forum," in the current browser, terminate the browser and open GEDIT, then I cannot paste "Dear forum," to the text editor.  In order to paste the character string in the current setting in my system, I have to keep Firefox open.  How can I make the OS clipboard work like that of Windows?

TIA

---

### Post by wormser on 2007-06-22
Install glipper

```
sudo apt-get install glipper
```

But you probably want it to start on every boot.  System> Preferences> Session> New> name it glipper and the command is glipper.

If you are using kubuntu then try klipper.

---

### Post by farang on 2007-06-22
Works as you've told me.  Thanks!
:)

---

### Post by farang on 2007-06-24
> **farang said:**
> Works as you've told me.  Thanks!
:)

Oopps, the System> Preferences> Session> New part has turned out to be not working.

Using the menu above I added a line in "Startup Programs" as below;
Name: glipper
Command: glipper

I logged out and re-entered the DNOME desktop.  Glipper does not run at startup nor the Session menu has the line I added above.

Command <glipper> at the terminal does starts Glipper but it returns an error message:
(process:8206): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed


:( :( Did I do anything wrong ??

---

