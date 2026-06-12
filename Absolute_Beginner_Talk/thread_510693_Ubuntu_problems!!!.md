---
title: "Ubuntu problems!!!"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by 4Real on 2007-07-26
Yay i installed ubuntu on my destroyed 98! 

Damn! Theres a few problems that i cant live with!

Theres no sound... It says i need gstream plug in or different sound device...it worked fine before 

My screen resoltuion is big and has no option for 1024x768 screen resolution! So my screen resolution is 864 x 660 (roughly)  

How do i get rid of the GRUB problem... 

im only **13** who came out of the gates (bill)... i want linux but maybe im not up for it... if anyone can help me that would be cool :KS

---

### Post by 4Real on 2007-07-26
Oh yeah in the start-up it asks you what to boot screen ... Like 6 different options

---

### Post by deadgobby on 2007-07-26
Please post your system specs. Like CPU, RAM, Vid Card, sound device and ect..

---

### Post by 4Real on 2007-07-26
266 MHZ 
256 Ram
9 GB - (ubuntu 4.3 gb)

Sorry i'm not sure about the sound card or video card :(

also im running Ubuntu 7.04

---

### Post by Happy_Man on 2007-07-26
Right... open up Applications --> Add/Remove and search "gstreamer" then install all the codecs.

Your screen resolution can be fixed by editing /etc/X11/xorg.conf. Just go ahead and post that file here, and one of us will tell you what to do.

Yeah... that's what it's supposed to do. Show you all the different kernels you can boot and such. Just boot the latest kernel (eg the default) and you'll be fine. 

Welcome to Ubuntu!

---

### Post by 4Real on 2007-07-26
yes finally help... I'm not on Ubuntu right now but where do i find that file? How do i post it up here? You sure the sound will be fixed like that? has it happened to you?

---

### Post by 4Real on 2007-07-26
yeah so right now im taking as many notes as i can ... if you can lend me some tips that would be cool :guitar:

---

### Post by paradoxchild on 2007-07-26
easiest way to get better screen resolutions (with a little command line) is go to a terminal (accessories > terminal) and type sudo dpkg-reconfigure -phigh xserver-xorg, hit enter, then scroll through and hit space an all resolutions you want then hit enter. You may have to do ctrl alt backspace to restart the gui to get those resolutions, or maybe restart.

---

### Post by Happy_Man on 2007-07-26
Yeah... I'm pretty sure it will be fixed like that... since it's asking for you to install them.... :D ;)

To paste the file... just open it up in a text editor, *BE SURE NOT TO CHANGE ANYTHING IN IT* and just copy and paste the file on here. Or send as an attachment to your post. Either way. And, as I said, the file is in /etc/X11/xorg.conf.

EDIT: Try paradoxchild's solution before posting xorg.conf, though. I had completely forgotten about that. *slaps forehead*

---

### Post by 4Real on 2007-07-26
my keyboard configs is a bit messed up to... when i hold shift and press "1" this should come up = !
instead some other thing comes up.

---

### Post by 4Real on 2007-07-26
My Ubuntu computer is not hooked up so it will be hooked tomorrow... I'll post a new topic about how it went... I still need help with keyboard help... NOTHING IS WRONG WITH THE KEYBOARD... i think i used wrong config... hmmm....:confused:

---

### Post by graigsmith on 2007-07-26
> Theres no sound... It says i need gstream plug in or different sound device...it worked fine before
 

do you mean it worked fine, in ubuntu? or in windows? if it was just working only in windows, that doesn't guarentee that it will work in ubuntu.  linux is a different operating system than windows, and it might not work with every device.

---

### Post by Depressed Man on 2007-07-26
Did you choose the keyboard layout? Ubuntu menu bar > system > preferences > keyboard

You can choose the keyboard you want in there.

---

### Post by 4Real on 2007-07-26
> **graigsmith said:**
> do you mean it worked fine, in ubuntu? or in windows? if it was just working only in windows, that doesn't guarentee that it will work in ubuntu.  linux is a different operating system than windows, and it might not work with every device.

It worked fine in Ubuntu... Damn that would suck if it didn't work... I hope its something to do with Gstream...

Thanks Depressed Man for the keyboard help... I gotta go eat so i'll ***_revive_*** the thread later... Bye All

---

### Post by 4Real on 2007-07-27
Ok non of my problems have been solved yet. 

I´ve been given instuctions to do this : Open Up Applications and Search GStreamer then install codecs. [I]I can't seem to find a search engine in Applications...
[/I]


Go to Applications go to terminal type sudo akpg=configure-phigh xserver-xorg

It doesnt work...

Go To Applications > Accersories Menu. Type codec. sudo gedit_/boot/grub/menu.lst...

Where do i type codec?

I am very confused :confused::confused::confused:

---

### Post by 4Real on 2007-07-27
sorry for bumping my post but i really need help... i might have to uninstall ubuntu if i cant get sound and a good Screen Resoultion :(:(:(:(:(

---

### Post by Happy_Man on 2007-07-27
I said Applications --> Add/Remove..... then search gstreamer in that.

the code is: ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` Copy and paste that into a terminal (Applications--> Accdssories --> Terminal)

---

### Post by Malta paul on 2007-07-27
Hi, Regards your keyboard problem you could try: System >Administration >Keyboard Preferences, then click on 'Click Layout'  then select you keyboard model.
Have fun :wink:

---

