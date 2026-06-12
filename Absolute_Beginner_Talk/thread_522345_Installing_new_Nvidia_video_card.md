---
title: "Installing new Nvidia video card"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by serfcx on 2007-08-10
Hi, currently have a PC with integrated video and have purchased a Nvidia PCI-e card which I want to install.
I know that if I install the card and reboot then I will have to

sudo dpkg -reconfigure -phigh xserver-xorg

and then select "nv" as the driver and restart X. Then I would use envy to grab the drivers from the nvidia website.

I have envy installed, would it be possible to install the new card and then at the prompt run

sudo envy -t

and let envy install the correct driver ? This would save me going through all the questions in the reconfigure xsever-xorg - or not ?

Would it work ? Thanks

---

### Post by stchman on 2007-08-10
> **serfcx said:**
> Hi, currently have a PC with integrated video and have purchased a Nvidia PCI-e card which I want to install.
I know that if I install the card and reboot then I will have to

sudo dpkg -reconfigure -phigh xserver-xorg

and then select "nv" as the driver and restart X. Then I would use envy to grab the drivers from the nvidia website.

I have envy installed, would it be possible to install the new card and then at the prompt run

sudo envy -t

and let envy install the correct driver ? This would save me going through all the questions in the reconfigure xsever-xorg - or not ?

Would it work ? Thanks

First thing you need to go into the BIOS to see if there is a setting to disable onboard video.  If not there might be a jumper.

Second, after powering down the PC install the new PCI-E video card.

Third, if you are using Feisty you can just enable the restricted drivers.  If you are using an older distro then follow my procedure here.

[http://www.stchman.com/video_drivers.html](http://www.stchman.com/video_drivers.html)

---

### Post by serfcx on 2007-08-12
stchman - Thanks for the input about changing the bios settings

This process refers to an Asus motherboard and assumes you have "Envy" installed

Press <DEL> when booting to get to Bios setup.
Menu "Advanced" ---> "Advanced chipset settings"----> "Booting graphic Adapter priority"

You then have an option to change sequence to PCI E /VGA

Change and hit F10 to save.

Shutdown and install new card and reboot.

X will complain about unable to start, enter "no" when asked about configuration.

Login with user name and password and at prompt type

sudo envy -t 
and hit "enter"

select "1" for Nvidia

Let envy do its stuff and then your card should be installed and working :)

---

