---
title: "xorg.conf corrupted-help please!"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Trurl on 2006-06-12
Hi all,

   In trying to fix my touchpad, I somehow managed to remove my computers ability to boot ubuntu in a graphical mode. I get a blue screen error about X's graphical interface being unloadable and then I get a black screen with nothing but a terminal line. I edited xorg.conf after installing touchpad drivers because my touchpad was acting up and the site I was at had a sample of how the touchpad section of xorg.conf should look. I backed up the original, and I know there is a barebones version lying around something else on the hard drive. I tried to gedit the corrupt xorg.conf from the terminal but I got an error that gedit could not display in this mode. 

  I then booted into XP to try to fix xorg.conf by accessing the partition only to find that I can't access root from the XP side (can I fix this at some later point by the way?). 

I can't even boot in recovery mode because the X error appears again! 

So, can anyone help me fix my xorg.conf?  

Thanks,

Trurl

---

### Post by blair on 2006-06-12
sudo dpkg-reconfigure xserver-xorg shoud restore the package and its associated default config file. tip: next time backup your files. 

actually, if you look in /etc/X11, you may see one or more files titled xorg.conf.<yada yada> where the trailing string there is a date/time stamp. This is likely your original file that has been backed up and renamed to reflect the date/time stamp when the file was modified. find the latest version and restore it by copying it to xorg.conf.

---

### Post by Trurl on 2006-06-12
Thanks for that suggestion. I wound up using a cruder method, booting in recovery mode, using nano from the command-line and overwriting the corrupted file with a re-named backup file. What exactly does X do? Is it the GUI program for Ubuntu? 

-Trurl

---

### Post by IYY on 2006-06-12
Pretty much all the graphics you see in Linux use the X server.

---

