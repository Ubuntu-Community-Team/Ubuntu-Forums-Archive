---
title: "Computer Starts Up.. But No Screen?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-03
Alright, I have been using possibly one of the worst computers ever made, so i decided i want to get my old computer fixed.  Problem is, I did some huge update, and I got gnome, beryl, etc.  

Okay, so the update I did took about two hours.  After I restarted, after the update I no longer have a screen.. I get the old Kubuntu loading screen and all, but after that, It loads me up in the terminal.  After I put my username and password in, it still dosent take me to a desktop, but it leaves me in the terminal, something like this

nic@desktop: 

Or something.  So im stuck here.  I havent been able to get my computer back and working.  What can I do.



A list of things I wont be able to do:
1.  Make a new CD
2.  Order a new CD.
3.  I dont have a Windows xp CD.


What can I do from here.  I've tried changing the kernel I load up with, and that dosen't work.  
What can I do.  I dont get any messages saying the X-server hasen't started, so rule that out.

Any suggestions?

---

### Post by arochester on 2007-06-03
At the prompt, after you have logged in, input >  sudo dpkg-reconfigure xserver-xorg
 This will start a text-based wizard to reconfigure your xserver. Answer the questions you can. If there are questions you can't answer then go with the given default.  FInish with a > sudo reboot If at first you don't succeed then try again. If necessary specify VESA.

You may have to reinstall any special video driver again. If you have already downloaded and saved it, just run again.

---

### Post by LollYouSuckZor on 2007-06-03
Okay, see I removed the video card, so I swiched back to nv while editing the settings.  After rebooting, I still start up in the termninal..

---

### Post by Pollywoggy on 2007-06-06
Let me guess.  Nvidia type video card?

Try this in that console that you get when the machine boots, but first make sure you have a ~/.xinitrc file.

Mine looks like this:

exec xfce4-session

but 'xfce4-session' can be replaced with 'startkde' or 'gnome-session' or whatever the appropriate command is for your system.

Then do 'startx' in the console and if that does not work, try one of these:

startx -- :1

startx -- :2

Post the errors in this thread.

---

