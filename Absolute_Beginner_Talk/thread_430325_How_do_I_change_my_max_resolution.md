---
title: "How do I change my max resolution?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by ChaosNipples on 2007-05-02
I have a 19 inch monitor that has a maximum resolution of 1600x1200. From what the **System>Preferences>Screen Resolution>** menu says the max I can have it is 1024x768. I would really like some help with this since it annoys my eyes when I look at my ¨large¨ screen (If you catch my drift).

Thank you for reading!

---

### Post by tommcd on 2007-05-02
First, back up your xorg.conf like this:
sudo cp -i /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
Boot to recovery mode and type "sudo dpkg-reconfigure xserver-xorg" without the quotes. Choose defaults for all if you don't know the answer. At the end where you configure your monitor, choose advanced if you know your monitor's horizontal sync and vertical refresh rates. Otherwise choose medium if you don't know them.
Either way, when you get to the screen resolutions, scroll up and down with the arrow keys and select the resolutions you want with the space bar. When you finish, type "sudo reboot". You should get the resolutions you want. If you have installed nvidia drivers, you will need to reinstall them after this.
And welcome to the forums!

---

### Post by ChaosNipples on 2007-05-02
Thanks for the help!

---

### Post by Brudy on 2007-05-02
How do you boot to recovery mode?
As I have used sudo dpkg-reconfigure xserver-xorg last night, I started this machine tonight, with difficulty as to a failure, after 3 atempts to restart in terminal mode with dpkg-reconfigure xserver-xorg the last attempt restared.
I still have the word program fill morew of the screen than I can see.

---

### Post by tommcd on 2007-05-03
To boot to recovery mode just choose it with the arrow keys at the grub menu and select it with enter. You will only see the grub menu if you dual boot. If you don't see the grub menu hit Esc key as the PC boots up and select 'recovery mode' option.
Another way to do this is to boot to the GUI, then hit ctrl+alt+F2 (or any F key from 1-6) to get a terminal. Login and type "sudo /etc/init.d/gdm stop". Then run "sudo dpkg-reconfigure xserver-xorg". When done type "sudo reboot" or "sudo /etc/init.d/gdm start" to restart the GUI. ctrl+alt+F7 gets you back to the GUI.
Hope this helps.

---

