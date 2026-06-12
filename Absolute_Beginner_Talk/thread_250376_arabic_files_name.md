---
title: "arabic files name"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by zAzO0o on 2006-09-04
hey all again 
please i need help as my ubuntu 6.06 can't display my arabic file name it display the name like this &#1567;&#1567;&#1567;&#1567;&#1567; &#1567;&#1567;&#1567;&#1567;&#1567;.mp3 
so please any one can help me told me how to make ubuntu display the arabic file names as i live in egypt and arabic is my country language :D

---

### Post by msak007 on 2006-09-04
There are several packages that provide Arabic support, so you may need to install them. First open a terminal and type:

```
sudo aptitude update
sudo aptitude install language-support-ar language-pack-ar-base language-pack-gnome-ar-base ttf-arabeyes
``` 
That'll install all the needed base language files and additional Arabic fonts. It'll also install Arabic support for apps such as Firefox, Open Office, etc., and allow you to see file names encoded in Arabic. I'm not sure how it is in Gnome, but in KDE there's a Regional / Language setting in System Settings where I can pick the region / language, and can add Arabic to the list of languages (to change the user interface, for example). Hope this helps.

---

### Post by zAzO0o on 2006-09-04
i do the code that you send but nothing changed :S 
and when i search for region / language in system i didn't found it also 
what can i do ?

---

### Post by msak007 on 2006-09-04
> **zAzO0o said:**
> i do the code that you send but nothing changed :S 
and when i search for region / language in system i didn't found it also 
what can i do ?

Did the files actually install then? What did the output say, that they are already installed or that they couldn't be found? If you search in Synaptic, does it indicate they're already installed? If they are then I'm not sure what else could be wrong as those packages provide Arabic encoding / character support. I'm not sure where you can change Gnome's language settings (maybe somebody else can help here), but that may be needed.

---

### Post by zAzO0o on 2006-09-04
yes i'm sure that the packages are correctly installed and i looked in the synpatic an found that they are installed

---

### Post by zAzO0o on 2006-09-04
[ATTACH]15260[/ATTACH]

[ATTACH]15261[/ATTACH]

this 2 attachs show you what i have

---

### Post by msak007 on 2006-09-04
I see what you mean. I have all the same language packages / files installed and have no problem seeing Arabic text or typing it in file / folder names. A couple of questions though - did you reboot after installing all these files? I'm not sure if you have to or not, but sometimes (even in Linux) a simple reboot will fix certain problems or initialize files that are needed. My second question is if the folder you're trying to view (/media/win3/top/????)  is a local (as in, in your computer) drive that you're navigating to or if it's a Samba / network share mounted locally.

---

