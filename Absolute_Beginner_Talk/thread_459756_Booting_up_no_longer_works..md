---
title: "Booting up no longer works."
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by Tynictansol on 2007-05-31
Hey everyone.   This is my first post here, though I registered as soon as I installed Edubuntu.  I've had it now for about a month, and I love it.   Last night I configured it to automatically log me in, and continued to use the computer.   The only other thing I can think of that I changed during that time of the computer being on was an extension I installed in firefox.  I logged out, and turned the computer off.   

     Today I didn't touch the computer until this evening around 10.   The computer comes to its bootloader and as usual I choose the ubuntu. Looking back, it seemed to take a bit longer going through the loading bar portion, but not anything that I thought was odd the first time through.   The cursor came on screen, as did the Gnome loading box.   And that's pretty much it.   it'll sit there, and going through it a few different times I've occasionally gotten this error with the red circle with a white tak in it
      There was an error starting the GNOME settings daemon.
     
      Some things, such as themes, sounds or background settings may not work correctly.

     Process /usr/lib/control-center/gnome-settings-daemon exited with status 1

    GNOME will still try to restart the settings Daemon Next time you log in.

Only button is the close one.    At this point the computer seems idle, and the screen will go to sleep if it waits long enough.   USB ports are operational, as my mouse still works.

If it's relevant, I have a Toshiba Qosmio G-15R.   Ubuntu's on the second installed harddrive, XP Media Center's on the first one.   I've really enjoyed using Edubuntu so far, and have been learning a little on the commands for the terminal, but booting into the  recovery mode is still relatively greek to me.  

Thankyou so much for any help that can be provided in advance.

Tyler

P.S.   Though this appeared before this problem, at the bootloader screen several days ago appeared two new options for Ubuntu, being kernel 2.6.20-16   vice the -15 that was originally there.  Is this related or is this something that happened from like, an update or something?   Anyway, thanks again

---

### Post by candtalan on 2007-05-31
I may not be able to help much.
If it was me, I would find it comforting to see that it still ran ok from a live CD. Do you have one available, a recent cd such as 7.04 say? It will nort cure things but it is a simple way of basic confirmation of hardware etc.

it looks as if booting (linux kernel) is basically ok, but maybe the window manager (gnome) is getting trouble for some of its function.

Do you get any menu if you right click the mouse?

I do not know of a specific suggestion, but a thought comes that if it is gnome settings which are giving trouble, then maybe a reinstall of the package ubuntu-desktop might be useful, maybe someone else here can comment. It would however require you to access a command line and maybe use the keyboard. 
Comments anybody?

---

### Post by dave-5B on 2007-05-31
first of all your system is booting correctly, if gnome is trying to boot then all your partitions, grub and friends are sorted

if you press ctrl + alt + backspace the x window system will quit and you will be left at a command prompt

also pressing ctrl + alt + F[1-6] will change between terminal screens

from here you can maybe try:
sudo dpkg-reconfigure edubuntu-desktop

this command will act much like it sounds, however it may break any custom applications/settings you have made to your system, its also a fairly drastic and brute force solution but GNOME should work on restart

every time the kind people decide its time for you to upgrade your kernel you will get a new entry in the grub menu, this is in case the new kernel doesnt work (you would be up the creek otherwise)

---

