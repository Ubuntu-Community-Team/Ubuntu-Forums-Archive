---
title: "Wireless Problems again :-("
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Bennnfc on 2008-01-27
Hi all this is my first post here s please dont bite. Im using Ubuntu 7.10

Im having problems installing my in-built wireless card its on a Acer Aspire 5710 and ive already followed all the instructions off this page [http://acer5720linuxubuntu.blogspot.com/2008/01/acer-5720-ubuntu-710-eng.html](http://acer5720linuxubuntu.blogspot.com/2008/01/acer-5720-ubuntu-710-eng.html).

This is a wierd problem because i have had used it on this install but i was having problems with my sound so i did this :
Go to sinaptics manager> Repositories> Updates and mark "Unsupported Updates", and then open the console and write:

$ sudo apt-get install linux-backports-modules-rt

Then:

$ sudo gedit / etc / modprobe.d / alsa-base

Write your password...
And will open a text document, and then add the following at the end of the document:

Options snd-hda-intel model = acer

Save and close ...

Only when i restarted my laptop i had a message about gnome couldnt start and some things wouldent be loaded lie theme's etc and i noticed my little icon which i clicked to check my wireless status was changed and it wasnt connecting now the only way i can get online is by using a wired connection.

Can anyone help me :)

---

### Post by TygerFish on 2008-01-28
You could try undoing what you've done, moving backwards.  For starters, if you're at least getting into Gnome (albeit with errors) you can try:
```
sudo gedit /etc/modprobe.d/alsa-base
```
and just remove the last line that you added.  Then restart and see if that works.  If it does, at least you're back to where you started!

---

