---
title: "kubuntu broken after update plz help"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by superoo on 2007-01-13
Hi, I have used Kubuntu Edgy for a month now with no problems however there was always an icon in the buttom right that said 83 updates available.  After installing the updates i rebooted and it boots into a console. i don't know how to make it work again

i tried ```
dpkg-reconfigure xserver-xorg
```
but it didn't help

---

### Post by obsidion on 2007-01-13
> **superoo said:**
> Hi, I have used Kubuntu Edgy for a month now with no problems however there was always an icon in the buttom right that said 83 updates available.  After installing the updates i rebooted and it boots into a console. i don't know how to make it work again

i tried ```
dpkg-reconfigure xserver-xorg
```
but it didn't help


  In what way didn't it help and what made you think that command without sudo in front of it would do anything.
What happened after you did that and reconfigured your xserver. Did you expect it to suddenlt log you on, did you reboot after running the command as sudo, what did you do from there that didn't work ?
 Information is the only way we can help you. Providing litle or none does not help us to help you

---

### Post by superoo on 2007-01-13
yes i had sudo infront of it and i filled out all the information to the best of my ability.  I believed that after reconfiguring i would be able to reboot and it would start as normal since i read this in another post.  After running the script nothing changed even after reboot.  Is there a was to manually log into a KDE session from the console?

---

### Post by obsidion on 2007-01-13
> **superoo said:**
> yes i had sudo infront of it and i filled out all the information to the best of my ability.  I believed that after reconfiguring i would be able to reboot and it would start as normal since i read this in another post.  After running the script nothing changed even after reboot.  Is there a was to manually log into a KDE session from the console?

   There are a couple of things to try sudo dpkg-reconfigure kdm
or sudo kdm
or startx without the sudo

Failing all these, maybe something has failed to install
 sudo apt-get update
sudo apt-get dist-upgrade

might give you some pointers

---

### Post by superoo on 2007-01-13
Ok, all is well i reinstalled the nvidia driver then ran the reconfigure script again and all is good!!!

---

### Post by obsidion on 2007-01-13
> **superoo said:**
> Ok, all is well i reinstalled the nvidia driver then ran the reconfigure script again and all is good!!!


  Glad you got it going, but pointing out you had an nvidia card would have given us a clue where to start helping you.

---

