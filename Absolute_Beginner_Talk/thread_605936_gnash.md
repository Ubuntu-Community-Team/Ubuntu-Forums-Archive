---
title: "gnash"
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by natman on 2007-11-07
Hi,
I am running 7.10 with firefox and every so often i notice the fan and cpu graph going crazy, i type "top" and always see "gtk-gnash" is the problem i quit it and back to normal with no noticeable effects, why is this happening and how to fix the problem?

---

### Post by droppedd on 2007-11-07
gnash is the GNU flash player, which is really not very stable and is slower than the official flash plugin. Uninstall gnash and install flashplugin-nonfree (the official Adobe Flash 9 plugin):

sudo apt-get install flashplugin-nonfree
sudo apt-get remove gnash

and that should fix it for ya. You may need to turn on the universe etc. repositories in Synaptic to get the Adobe plugin to install.

---

### Post by c.s.lewis on 2008-01-28
Your suggestion worked for me. When I upgraded to 7.10, I was asked if I wanted to change my default flash player and I did. In retrospect, I wish I hadn't because it took me several days to find this thread. As a result of changing from the default flash player, my homepage which is my local newspaper online, quit showing the flash player and it was driving me nuts until I found the answer in your thread. Thank you!

---

