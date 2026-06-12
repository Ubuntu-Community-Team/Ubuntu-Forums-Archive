---
title: "Quick help on package manager"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2005-07-11
Help me quick!!! \\:D/  I just sucessfully installed games from CD with synaptic. Now what? I mean how can I open the darn files from menu or icon? Must I apt-get the different files or how do you create the "shortcuts" to run the files. This is for my kids.

---

### Post by poofyhairguy on 2005-07-11
[QUOTE=GrootBrak]Help me quick!!! \\:D/  I just sucessfully installed games from CD with synaptic. Now what? I mean how can I open the darn files from menu or icon? Must I apt-get the different files or how do you create the "shortcuts" to run the files. This is for my kids.[/QUOTE]

Use the name of the program in the run dialog box. Some can be found by isntalling the menu:

sudo apt-get install menu

TO add shortcuts:

[http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor)

---

### Post by GrootBrak on 2005-07-14
Did it still no shortcuts or links. I have to search far and wide in my folders to get the program I need, then I have to make a shortcut to it and drag it to desktop. Is'nt there an easier way. 

I don't have any "smeg" as well. Sigh. back to the fact that I do not have any internet available and so far nothing in bluetooth had me setting up Bluetooth correctly. In fact the ever increasing list of depencies is getting longer and longer...

---

### Post by GrootBrak on 2005-07-15
Thanx that worked great. Do you perhaps know why I often get the following kind of response in Synaptic?

Depends on **yada yada** but **yodo jodo** is to be installed. Then nothing happens anyway. The package gets unmarked.

---

### Post by Wolki on 2005-07-15
[QUOTE=GrootBrak]Thanx that worked great. Do you perhaps know why I often get the following kind of response in Synaptic?

Depends on **yada yada** but **yodo jodo** is to be installed. Then nothing happens anyway. The package gets unmarked.[/QUOTE]

This often means you have repositories enabled that don't work well with Ubuntu, like Debian repos.

---

### Post by RastaMahata on 2005-07-15
[QUOTE=Wolki]This often means you have repositories enabled that don't work well with Ubuntu, like Debian repos.[/QUOTE]
 Wolki's right. Just in case, paste here your /etc/apt/sources.list

---

