---
title: "I need help getting online!"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by dopey220 on 2007-06-02
I have Feisty installed on a Dell Dimension 4400 PC with a Motorola WPCI810G wireless card installed. How do I get it to connect to my wireless network?

---

### Post by Sammi on 2007-06-03
If it doesn't work out of the box, then it means that the card manufactures (in this case motorola) haven't made open source Linux drivers. But don't despair, because it seem it is possible to make the win drivers work in Linux by using at application called ndiswrapper.

It think the right driver for your card is this one: [http://broadband.motorola.com/consumers/products/WPCI810g/downloads/WN-WPCI-Web-Update-v1.1.exe](http://broadband.motorola.com/consumers/products/WPCI810g/downloads/WN-WPCI-Web-Update-v1.1.exe)

Found it on this page: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/)

Using this howto you should be able to make it work: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

