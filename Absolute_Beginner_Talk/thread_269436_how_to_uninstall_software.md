---
title: "how to uninstall software"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by sdubois92 on 2006-10-01
i need some help

---

### Post by Fass on 2006-10-01
You uninstall software in Synaptics by finding the package you want to remove, right clicking it and choosing "remove" or by simply opening a terminal and writing ```
sudo aptitude remove [insert_name_of_package_here]
```

---

### Post by hesjnet on 2008-06-22
how to I uninstall a program that is not listed in synaptic? Like Google Earth or skype?

---

### Post by oldsoundguy on 2008-06-22
Spend some time exploring all of those pull down menus that are on your desktop.  You will be amazed what you find .. such as under Applications is Add/Remove.

---

### Post by mghambunan on 2008-07-08
how can i uninstall applications installed by running this command ```
./install.sh
```

i can't find the application in Synaptic Package Manager.

---

### Post by ad_267 on 2008-07-08
> **mghambunan said:**
> how can i uninstall applications installed by running this command ```
./install.sh
```

i can't find the application in Synaptic Package Manager.

You need to find out in the documentation for that particular application. You could try ./install.sh --uninstall

---

### Post by mghambunan on 2008-07-08
> **ad_267 said:**
> You need to find out in the documentation for that particular application. You could try ./install.sh --uninstall

Thanks for the quick reply but it seems that it has no documentation on how to uninstall and when I try to run ```
./install.sh --uninstall
``` it reinstalls the application.

---

### Post by ad_267 on 2008-07-08
> **mghambunan said:**
> Thanks for the quick reply but it seems that it has no documentation on how to uninstall and when I try to run ```
./install.sh --uninstall
``` it reinstalls the application.

Try ./install.sh --help or ./install.sh -h

If that doesn't tell you anything then you need to check the website or search for how to uninstall this particular application. I don't think there's any way to easily remove an application installed this way other than by using an uninstall script. You could try opening that script file in a text editor to see what options you can use but the script probably contains binary data.

---

### Post by mghambunan on 2008-07-08
This is what the install.sh contains
```
#!/bin/sh

./ThemesCreatorSetup

if [ -r ThemesCreator ]
then

sudo mv ThemesCreator /usr/bin/ThemesCreator
sudo chmod 755 /usr/bin/ThemesCreator
sudo ldconfig
sudo cp ThemesCreator.desktop /usr/share/applications/ThemesCreator.desktop
sudo cp ThemesCreator.png /usr/share/icons/ThemesCreator.png

fi
```

---

### Post by ad_267 on 2008-07-08
> **mghambunan said:**
> This is what the install.sh contains
```
#!/bin/sh

./ThemesCreatorSetup

if [ -r ThemesCreator ]
then

sudo mv ThemesCreator /usr/bin/ThemesCreator
sudo chmod 755 /usr/bin/ThemesCreator
sudo ldconfig
sudo cp ThemesCreator.desktop /usr/share/applications/ThemesCreator.desktop
sudo cp ThemesCreator.png /usr/share/icons/ThemesCreator.png

fi
```

Ok well that's easy enough to remove then. In a terminal run:
```

sudo rm /usr/bin/ThemesCreator
sudo ldconfig
sudo rm /usr/share/applications/ThemesCreator.desktop
sudo rm /usr/share/icons/ThemesCreator.png

```

If you look at hidden directories in your home directory there might be a .themescreator or something that you can remove too.

---

### Post by mghambunan on 2008-07-08
> **ad_267 said:**
> Ok well that's easy enough to remove then. In a terminal run:
```

sudo rm /usr/bin/ThemesCreator
sudo ldconfig
sudo rm /usr/share/applications/ThemesCreator.desktop
sudo rm /usr/share/icons/ThemesCreator.png

```

If you look at hidden directories in your home directory there might be a .themescreator or something that you can remove too.

Thanks a lot for the help. It completely removes the application and it doesn't contain a hidden directory in my home directory so nothing to remove.

---

