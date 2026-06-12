---
title: "installing flash player"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by kensou on 2007-05-11
how to install flash player 9 in ubuntu 7.04 fiesty fawn?

---

### Post by Kobalt on 2007-05-11
Applications > Add/Remove. Search for flash, select, install.

---

### Post by starcraft.man on 2007-05-11
Just pop open the terminal (Applications > Accessories > Terminal) and type this in:

```
sudo aptitude install flashplugin-nonfree
```

That should do it. If you get any trouble with Audio in sites like youtube, check [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox") for fix. 

Feel free to read more through ubuntu guide it answers lots of questions for new and advanced users :)

---

### Post by kensou on 2007-05-11
when try to install flash plugin  by writin in terminal it give me the error
Segmentation fault (core dumped)

---

### Post by Kobalt on 2007-05-12
Didn't you manage to install it from Add/Remove ?
You can try this then if you want : [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

