---
title: "please help"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by jordansdad253 on 2007-05-15
so i am brand new to linux. i'm using xubuntu feisty fawn 7.04 and the problem i'm having is trying to install new themes. i'm the only user on this computer and i thought i had all permissions, but everytime i try to extract the folder to /usr/share/themes it says; You don't have the right permissions to extract the files to the folder "/usr/share/themes". i'm so lost, i've been searching all throughout google and can't seem to find an answer to my dilema. please help!!

---

### Post by eentonig on 2007-05-15
As a regular user, you only have full rights to the documents under your /home/<username> directory.

read up on Linux and how it works [here]("http://www.psychocats.net/ubuntu/index.php")

To do what you want to do however, it'll suffice to System\Preferences\themes... and drag the archive file into the new window. This will install this theme in a hidden folder under your home (/home/username) folder.

---

### Post by jbro on 2007-05-15
Hello,

The easiest way to do this, assuming you are running GNOME would be to go to System->Preferences->Theme and then clicking the "Install Theme" button in the theme selection window.

If you want to install themes by hand and if you're the only user of the computer, then you might as well just put the themes in your home directory. Assuming you are referring to GTK or Metacity themes, you can create a .themes directory and extract the themes there. The Gnome Theme Manager should pick them up automatically. To do this do the following in a terminal:
```
cd
mkdir .themes
cd .themes
tar -zxf theme_name.tar.gz
```
Replace theme_name in the last line with the real name of your theme. If the extension of the theme is .tar.bz2 instead of the last line above, do ```
tar -jxf theme_name.tar.bz2
``` You can also use a GUI program to extract the files into the /home/user/.themes directory.

Regards and good luck,
jbro

---

### Post by jordansdad253 on 2007-05-15
sorry if i get annoying but i'm still having trouble. i can't seem to find system\preferences\themes when i tried extracting it there it made a new folder but that one is not hidden and neither is the folder i moved to it. is there somewhere i can find maybe a baby-step beginners guide to installing themes? i just don't want to try anyone's patience.

---

### Post by jordansdad253 on 2007-05-15
Thanks for all your help i was able to figure it out!! thanks again and sorry for the noob question

---

