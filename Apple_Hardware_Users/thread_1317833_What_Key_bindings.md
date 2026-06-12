---
title: "What Key bindings?"
date: 2009-11-07
forum: Apple Hardware Users
---

### Post by Bibabenjo on 2009-11-07
Hello,

Recently I updated my macbook 2.1 to Karmic. Unfortunately the settings for my Keyboard dont work any longer (the "at" sign, the Euro sign for example)
I know I can set them under preferences.
Could anybody post his configuartion? (what keyboard model, and what special bindings)

Thank you very much!!

---

### Post by book on 2009-12-09
> **Bibabenjo said:**
> Hello,

Recently I updated my macbook 2.1 to Karmic. Unfortunately the settings for my Keyboard dont work any longer (the "at" sign, the Euro sign for example)
I know I can set them under preferences.
Could anybody post his configuartion? (what keyboard model, and what special bindings)

Thank you very much!!

Bibabenjo, 

I'm sorry I cannot tell you the answer to your question. In fact I seem to have the same problem as yourself with the AT-sign and the Euro-sign 


The AT-sign, in particular, can be quite important in this age of the Internet. Therefore, I decided to suspend the Karmic Koala and return to Mac OS for the time being. In case the Mactel Team or somebody else comes up with a solution, than I shall give the Karmic Koala a new try.

Further comments:

- I tried to install Ubuntu 9.10 on a Macbook 2,1

- Neither BootCamp nor Diskutil let me create a new partition on the 80 GB harddisk so as to enable a dual boot install. Therefore, I decided to wipe out MacOS and do a single boot install of Ubuntu, which succeeded OK, except that I did not get the AT-sign...

- In Ubuntu's preferences tried with keyboard models "Apple laptop" and "Macbook/Macbook Pro",  and the layouts  "Finnish Macintosh" and "Swedish Macintosh". However, the ctrl, alt and option keys remained dead. 

- I installed pommed and so got some life at least to the FN-keys. Still, no  AT-sign or EUR0-sign. (The EURO-sign, too might sometimes be important.)

- I tried to follow the instructions about fixing the keyboard issues on the page "MacBook 2,1 and Ubuntu 9.10 (Karmic Koala)" ([https://help.ubuntu.com/community/MacBook2-1/Karmic](https://help.ubuntu.com/community/MacBook2-1/Karmic))
where it says: "To have the dead keys on the Alt/Option key the way they are mapped in Mac OS X, add this line to the end of your ~/.xinitrc file " etc. However, a file with that name was not to be found in this linux distro. At least I could not find it.  Therefore, I believe that instruction is misleading. Excuse me if I am wrong. 

- Hereafter, as said above, I proceeded to wipe out the Karmic Koala and to re-install MacOS Leopard. But I have reason to believe  that it will now be possible to create a new harddisk partition with BootCamp and to install Ubuntu 9.10 there anew, which I will do when I/ we get the answer to our key question.

Best.

---

### Post by Bibabenjo on 2009-12-09
Hey book,

Im sorry that it didnt work for you as well. 
But making a new partition should work with Discutil, I did it with leopard too. For Bootloader I use refit! 
You should consider to reinstall ubuntu (best is dual boot I think, so you could switch in case that something doesnt work as expected!

I finally fixed the "Keybinding" Problem too! Im not sure how exactly, but it works for me. Im sorry that I didnt post the answer (simply forgot the thread)

So I just post my settings:

Under Keyboard I selected: Macbook/Macbook Pro (Intl) and for me German Macintosh
Then I clicked on keybinding settings (or s.th. like that) and activated the following settings:
Euro-Symbol to E
Key to switch to third "keymeaning": any alt key

With this settings it works well for me! 

Hope you will give it a try, you are missing so much without ubuntu ;)

Regards

---

### Post by llamabr on 2009-12-09
Hello.  I don't have a macbook, and I actually run debian on my ibook.  But when I log into ubuntu 9.10 on another laptop, when I get to the gdm login screen, at the bottom, it gives me the option to select my keyboard layout, among other things.

Do you not have this option?

---

### Post by book on 2009-12-12
Bibabenjo, thanks for the advice. The layout options you mentioned fixed the problem with the Alt-keys and the Euro-sign.

After i had erased all data from the harddisk and re-installed Mac OSX Leopard, the BootCamp utility created a partition , and the Karmic Koala could be installed.

---

### Post by tom4everitt on 2009-12-13
> **book said:**
> Bibabenjo, 

- I tried to follow the instructions about fixing the keyboard issues on the page "MacBook 2,1 and Ubuntu 9.10 (Karmic Koala)" ([https://help.ubuntu.com/community/MacBook2-1/Karmic](https://help.ubuntu.com/community/MacBook2-1/Karmic))
where it says: "To have the dead keys on the Alt/Option key the way they are mapped in Mac OS X, add this line to the end of your ~/.xinitrc file " etc. However, a file with that name was not to be found in this linux distro. At least I could not find it.  Therefore, I believe that instruction is misleading. Excuse me if I am wrong. 


Actually I don't find it too rare that you should add a line to a non-existent file. If it doesn't exist it usually works with just creating the file and adding the given line to that (empty) file. 

It's quite common actually that there is a script checking if a file exist, and, if it does, reads settings from it. The file ~/.bash_profile is a good example of that, it does exist exist in most linux distros, but not in OS X. Adding such a file in OSX, with settings for your bash prompt e.g., will still work fine (the file will be read).

---

