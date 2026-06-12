---
title: "Noobiest of noob questions"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by alter_ego on 2006-03-30
After a lot of contemplation, i installed Ubuntu on my notebook. Made it dual boot with Win XP.

Everything seems to working as of now. Then i downloaded Opera browser for Ubuntu and saved it to my desktop.

Now how do i install this package, i have the .deb file, how do i go about installing any application for that matter using the GUI? (See how bad i am doing ?).

Help!!.

---

### Post by moffa on 2006-03-30
To install deb packages: (in a console)

sudo dpkg -i [packagename.deb]

To install other programs, use:
(in a console)
sudo apt-get update
sudo apt-get install [package name without the .deb]

Since you asked about using the GUI, use Synaptic (spelling?).  Try enabling the other repositories if you can't find what you are looking for.

I really recommend reading the sticky topics at the top of this forums.

P.S. Welcome :)

---

### Post by Mustard on 2006-03-30
Here is another link that might add to the above explanations...

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

