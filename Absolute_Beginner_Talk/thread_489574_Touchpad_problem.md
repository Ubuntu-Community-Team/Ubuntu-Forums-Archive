---
title: "Touchpad problem"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Raffaz on 2007-07-01
Hi

Im new to ubuntu so bear with me lol.

Ive been trying to disable the double tap setting on my touchpad. Someone gave me this link with instructions but it hasnt went to plan. [http://www.arsgeek.com/?p=1862](http://www.arsgeek.com/?p=1862). I restarted ubuntu studio and i get an error that says that the 2 is'nt a valid character. How do i go about changing this in the file that i edited, bearing in mind that i cant boot into ubuntu. Thanks.

Mick

---

### Post by coffeecat on 2007-07-01
I'm assuming you edited your /etc/X11/xorg.conf file and now you can't boot into the GUI desktop. That won't stop you booting into a non-GUI terminal and repairing the xorg.conf file and then rebooting.

Boot up and let the xserver crash with an error (if this is what it's doing). Forget about that and press ctrl-alt-F1 simulataneously. You'll find yourself at a login prompt without a GUI. Log in as normal. The password doesn't appear to be going in - but it is. Now you have to work solely from a command prompt. Don't panic! :wink:

Type the following command:

```
sudo nano -w /etc/X11/xorg.conf
```You'll be prompted for your password again. Nano is a simple but adequate text-editor. You can't use your mouse so simply scroll down to the line you need to edit and do so. Then do ctrl-o to save the edited file and ctrl-x to exit. Now reboot:

```
sudo reboot
```Hopefully, so long as your edit is correct it should boot into the GUI.

---

### Post by Raffaz on 2007-07-02
Excellent, cheers for the reply. It's sorted now. I also managed to sort the double tap by adding Options "MaxTapTime"  "0" :)

---

