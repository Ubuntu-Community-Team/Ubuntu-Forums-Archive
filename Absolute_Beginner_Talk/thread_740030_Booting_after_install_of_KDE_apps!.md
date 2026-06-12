---
title: "Booting after install of KDE apps!"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by jeffinhedon on 2008-03-30
Please can anyone assist 
I have Ubuntu 7.1 installed and running perfect!!!
I saw a thread that I thought might be an interesting project
It was to install the KDE desktop and lots of K apps.
I followed instructions and did an apt install from terminal
During the process it asked if I wanted KDE or Ubuntu (Gnome)
I said KDE
However I now cannot boot up 
The bootup process starts with a blue Kubuntu logo and progress bar
Then just hangs
I can boot up using recovery mode (this is it )
But How can I get back to the Gnome desktop and bootup as I had before this trial
Do I have to uninstall KDE and all its apps or ????
How can I recover my original Ubuntu bootup screen ?????
Your help and advice will be very much appreciated
Thanks in advance:confused::confused:

---

### Post by rickocop on 2008-03-30
Ok, the easiest way to find out what the problem is, is to discover where the startup is failing, so we'll do that by (temporarily) removing the splash screen (big kubuntu logo with progress bar)

I assume you're using grub: restart the computer and highlight the startup option "ubuntu kernel generic" or similar. Press the 'e' key once and a few lines should appear on screen replacing the menu which look similar to:

root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=111aa111-11a1-111a-1aa1-11a1111a111a ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

then highlight the line named kernel, and press the 'e' key again

now you have the option to edit the line, 
move your cursor to the end of the line and delete only  the word "splash". 
press the return key to submit
now you should be back to the lines above.
press 'b' once to boot your computer.

now loads of lines will be printed to your screen telling you what's happening as it boots up with "[ok]" at the end to indicate they've successfully started, eventually one won't do this. can you please tell me what it says, 


To reboot
when it stops loading - try pressing ctrl+alt+F2 which, if your lucky might bring up a prompt for your username: in which case login and type sudo reboot
otherwise you'll have to do it from the power switch on computer

---

### Post by jeffinhedon on 2008-03-30
Many thanks for prompt response.
I have done as you suggested
and the boot up sequence ran to the following line
Running local boot scripts (/etc/rc.local)
then hung
I pressed enter and was able to log in as user
What happens now ????

---

### Post by rickocop on 2008-03-30
ok,

firstly try opening a terminal and using the following command:

"sudo dpkg-reconfigure gdm"

which should hopefully give you an option to switch between gdm and kdm, select gdm and reboot.


if this doesn't work, try same procedure as last time, logging in, and typing "startx", what happens?

---

### Post by jeffinhedon on 2008-03-31
Well now!
Success I think??
After doing the reconfig.
The system now boots with the Kubuntu splash
but finishes with normal Ubuntu log in screen
so I can input my name and password as before.
Will it matter that the blue Kubuntu appears at boot up/
It now seems I have loads of different apps to use
Are any of these used to change the splash or doesnt it really matter?
I will look through all the apps to see what they all do.
Many thanks for your help so far in this :):)

---

### Post by rickocop on 2008-03-31
To be honest I don't know. 

The issue is if something in the boot sequence is specific to kde then it's not quite back to how it is, however I suspect the only real difference is whether you use kdm or gdm and there was something missing when it tried /etc/local that kdm needed and so it just hung without ever running kdm, but it gave you the login prompt subsequently so linux had started fine.

I'll see if I can find out a bit more about the splash screen.

---

