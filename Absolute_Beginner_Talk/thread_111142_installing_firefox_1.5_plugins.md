---
title: "installing firefox 1.5 plugins"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by RBH on 2006-01-01
i can't seem to get them to install correctly. i upgraded to 1.5 and when i try to view things like quicktime or realplayer clips it pops up a plugin install option. i choose to manually install, which realplayer has a linux version. i d/l it, run through the install and it is there. i can open realplayer and play clips with it, but it doesnt intergrate itself with firefox 1.5. then with the quicktime clips, i have vlc gtk+, which it says plays quicktime files, installed according to my add applications window but again, it isnt intergrating itself within firefox 1.5 as i can't get either of these to play when i click on a realplayer or quicktime clip link, all i get is the install plugin option. do i need to find these in the synaptic package manager and install from there too? 

when i installed firefox 1.5 i installed it into a directory i made for apps in my home directory and when i launched the browser it was still using the older firefox version until i went in and pointed it to the firefox 1.5 bin within home/apps/firefox  could this be my problem if i never uninstalled the original firefox before installing 1.5?

---

### Post by kaamos on 2006-01-01
The plugins will install at /usr/lib/mozilla/plugins/

I think it would be a good idea to link this folder to your firefor plugin folder. To do this open a terminal and
> sudo mv /where_you_installed_1.5/firefox/plugins /where_you_installed_1.5/firefox/plugins-old
sudo ln -s /usr/lib/mozilla/plugins /where_you_installed1.5/firefox/plugins


---

### Post by RBH on 2006-01-01
do i need to use home or will it know that? example, 

sudo mv /home/apps/firefox/plugins /home/apps/firefox/plugins-old
sudo ln -s /usr/lib/mozilla/plugins /home/apps/firefox/plugins

or

sudo mv /apps/firefox/plugins /apps/firefox/plugins-old
sudo ln -s /usr/lib/mozilla/plugins /apps/firefox/plugins

---

### Post by kaamos on 2006-01-01
If you have a firefox folder at /home/RBH/apps do
> sudo mv /home/RBH/apps/firefox/plugins /home/RBH/apps/firefox/plugins-old
sudo ln -s /usr/lib/mozilla/plugins /home/RBH/apps/firefox/plugins

---

### Post by RBH on 2006-01-01
thanks alot......worked like a charm!:D

---

### Post by kaamos on 2006-01-01
Glad to hear it worked. :)

---

### Post by nandasunu on 2006-01-02
thats a great tip, I was also wanting to get the plugins working for 1.5 and it perfect now :p

---

