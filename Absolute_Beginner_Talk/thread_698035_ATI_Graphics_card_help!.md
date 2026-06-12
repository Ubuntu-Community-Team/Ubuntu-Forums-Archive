---
title: "ATI Graphics card help!"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Karoniakowa on 2008-02-15
I am trying to get this ATI Radeon x1300 Graphics card to work and am not having much luck. i have only had ubuntu for 2 days

I started off putting the card into the pci slot and ubuntu wouldn't load so i switched the settings in the bios to boot up with the on board card. 

I got the Restricted pop up just like i was hopeing for and installed what ever was needed and it told me to restart.  

After switching the bios back  it boots up to a text only ubuntu  i do not know any commands so i try switching back to my onboard graphics and now ubuntu will not Start on my onboard card. 

Like i said i do not know any ubuntu commands and have no way ( that i know of) to get out of the text ubuntu...So i would like to know what i did wrong,How to make this card work and if its not possible to get this to work on ubuntu how do I get back to my GUI 

Thank you for reading i will be checking back to this in about 40 mins.

---

### Post by spiderbatdad on 2008-02-15
If you can get text mode or safe graphics boot, try this in a terminal to restore you previous xorg.conf.```
sudo dpkg -reconfigure -phigh xserver-xorg
``` Once you know how to repair your xsession you can try some different methods for enabling visual effects with a new post.

---

### Post by dstew on 2008-02-15
Boot to recovery mode (text-mode) with your card in the slot and enter this command```
lspci
```Find your graphics card in the list. Post the card information to the forum. You can also try this:```
sudo dpkg-reconfigure xserver-xorg
```When you get to the driver part, you can try ati or vesa. After you finish reconfiguring your xserver, enter```
startx
```If neither of these work, there are more things we can do.

---

### Post by Karoniakowa on 2008-02-15
Hi

Problem fixed not exactly sure how

after putting in sudo dpkg-reconfigure xserver-xorg i restarted and it let me go on with low grafhics  i reanbled the driver then restarted again and it works great

lspci says its in there as well

Thanks again

---

