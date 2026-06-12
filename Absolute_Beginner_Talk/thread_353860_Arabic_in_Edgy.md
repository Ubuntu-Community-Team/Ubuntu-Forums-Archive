---
title: "Arabic in Edgy"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by ayed on 2007-02-05
Sorry to bother all of you once again, 
I have a huge Arabic homework due this Thursday, can anyone tell me how to switch my keyboard layout to Arabic? I already tried changing it in the System--> Keyboard--> layout to no success.
Please I need HELP!!
Thanks:confused:

---

### Post by Oki on 2007-02-05
Perhaps look in Synaptic for the language pack for Arabic.

---

### Post by matthew on 2007-02-05
You will need to install these three packs using synaptic or apt-get or aptitude:

language-pack-ar
language-support-ar
xfonts-intl-arabic

For example, Applications->Accessories->Terminal
```
sudo apt-get install language-pack-ar language-support-ar xfonts-intl-arabic
```will do this for you.

Once those are installed you should will then need to go to 
System->preferences->Keyboard->Layout->add and add the Arabic keyboard layout that you want to use.

---

### Post by Oki on 2007-02-05
And perhaps this can help; [http://ubuntuforums.org/showthread.php?t=102760&highlight=arabic](http://ubuntuforums.org/showthread.php?t=102760&highlight=arabic)

---

