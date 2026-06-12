---
title: "Put Mandriva on another partition, Ubuntu not showin' up at startup?"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by SomeGuyDude on 2007-11-16
Is there a way to repair this?

I can access the HD, it's all there and unharmed. I just don't get the option to boot Ubuntu when I start up.

---

### Post by skymera on 2007-11-16
try:

sudo update-grub

---

### Post by mick222 on 2007-12-08
I,ve  got the same problem Mandriva doesn't recognize other linux oses and even trying to add them with the Mandriva control centre doesn't seem to work . The mandriva forums aren't much help as when you search most answers are in FRench . THe only way seems to be to edit the menu lst file can someone here tell me how to do that in Mandriva .

---

### Post by mick222 on 2007-12-08
I entered sudo update-grub  in Konsole as root and it said sudo command not found

---

### Post by floke on 2007-12-08
In Mandriva..become root (su or sudo) - then

nano /boot/grub/menu.lst

and add your Ubuntu boot lines here

If you're not sure what they are then mount your ubuntu partition (assume here its sda1)

-- in terminal --
mkdir /home/[yourname]/here
mount /dev/sda1 /home/[yourname]/here
cat /home/[yourname]/here/boot/grub/menu.lst

-- copy the bits you need and paste into Mandriva grub - but you'll have to change manually every time the kernel changes!

Hope this helps

---

### Post by mick222 on 2007-12-08
Mandriva seems strange doesn't recognise sudo as a command 
when i type nano /boot/grub/menu. lst
it says -bash: nano: command not found

---

### Post by floke on 2007-12-08
Have you tried 'su'
and 'vim' instead of nano?

---

### Post by mick222 on 2007-12-08
managed to fix it gave up on mandriva konsole. Booted Ubuntu from live disk and used terminal to navigate to mandriva grub and edited with gedit. seems to have worked

---

### Post by AdamWill on 2007-12-10
Mandriva doesn't use sudo by default (just plain su), and nano is not installed by default, though it's easily available from the official repositories. This is the official Mandriva help page for editing system config files:

[http://wiki.mandriva.com/en/Docs/Basic_tasks/Editing_configuration_files](http://wiki.mandriva.com/en/Docs/Basic_tasks/Editing_configuration_files)

---

