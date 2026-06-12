---
title: "[SOLVED] need help with boot console resoution!"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by dosterror on 2007-10-21
Hello everyone, i have just installed gusty server edition and since i dont intend on using xwindows, i was wondering how to change the text console resolution?

its set at 640x480 by defaults and ive tried vga=xxx (ive tried all from 771 to 795) in menu.list but no avail, the screen always goes blank. vga=ask, along with 'scan', gives me some options and all of them seems to be worse than default.

ive tried this with 2 different video cards and 2 different monitors with the same result so im assuming its not the hardware thats causing this problem. im currently using nvidia 6600 GT.

in the past ive used slackware on the same hardware and ive had no problem running a 1280x1024 text console so im also assuming theres some configuration that im not setting/that i dont know about. is there a way to change the console that runs on boot up or a way to change the resolution other than setting vga=xxx?

thanks!

---

### Post by Hobo Joe on 2007-10-21
If you have the drivers installed run this command:
```

sudo nvidia-settings

```

From there you can change the resolution, and save it to your xorg file.

---

### Post by shad0w_walker on 2007-10-21
That option will only work in a X environment, the Nvidia drivers aren't used to display the console.

In response to the actual problem, to my knowledge what you are doing should set up the console how you want. I did that once (Don't use the terminal enough to bother again) and it worked just fine doing it in the same way as you. Hopefully you will get a more knowledgable user come along and give you a hand.

---

### Post by dosterror on 2007-10-21
thanks. like i said, i dont intend on working in an x environment (although i might if webmin requires x).
i forgot to mention that when i boot up with the installation CD (text mode), the F4 - VGA option works fine for all resolutions in text mode. its only when i boot up the system from grub that the framebuffer doesnt seem to respond to anything but vga=normal.
how does the install CD get resolutions to work? am i missing something configuration here?

---

### Post by nosneros on 2007-10-21
Hi,

I had some success following the suggestions of RedSquirrel [here]("http://ubuntuforums.org/showthread.php?t=577457&highlight=console-setup#8") This enables the vesafb driver.

Then I added a video line to the kernel options in my /boot/grub/menu.lst:

# kopt=root=UUID=2db4a9f3-49dd-45b6-972d-fdb8c3f1233e ro video=vesafb:1440x900-32@52 
<--Notice it is still commented

and ran "sudo update-grub". *Edit* Of course, you should change your video option to match your desired resolution. */Edit*

You can run "sudo dpkg-reconfigure console-setup" to select the size of your console font.

Now it seems the framebuffer is working during boot. But after kdm starts up, it seems to put an extra space in between lines, so what I'm typing is displayed off the bottom of the screen...weird. Right now, I have console font size 8. I might try changing it back to the default (16) and see what happens.

HTH

---

### Post by marcantonio on 2007-10-21
It's something with Gutsy.  I've always had vga=791 set in menu.lst.  Since I've installed Gutsy any vga= option I try results in a black screen with a blinking cursor...

---

### Post by nosneros on 2007-10-21
Just an update: leaving my font at 16 seems to be ok. I can run size 8 immediately after doing a dpkg-reconfigure console-setup, but then upon reboot it has that weird double line problem. I guess just skip that step unless you're brave :)

Also, the format for the video option is video=vesafb:<width>x<height>-<colordepth>@<refresh rate>. More info [here]("http://dev.gentoo.org/~spock/projects/vesafb-tng/").

---

### Post by dosterror on 2007-10-21
im at school, but ill try it out when i get back home
thanks!

---

### Post by dosterror on 2007-10-22
Thanks everybody, specially nosneros!! i finally got it to work
heres a recap on what ive done using what nosneros' told me
i first switched my vid card to an old radeon cuz i happened to find one under my bed

```

1. sudo vim /etc/initramfs-tools/modules and add fbcon and radeonfb
so my /etc/initramfs-tools/modules looks like:
fbcon
vesafb
radeonfb

2. sudo update-initramfs -u -k all -v

3. sudo vim /etc/modprobe.d/blacklist-framebuffer
change the line "blacklist radeonfb" to "# blacklist radeonfb"
there was a bunch here so i guess i couldve used nvidiafb with my nvidia card..

4. sudo vim /boot/grub/menu.lst:
# kopt=root=UUID=f1ca5651-fd04-46c5-8b55-6f1f7ee79e9d ro video=vesafb:1280x1024-65@52
kept # since update actually reads off of this and is not really "commented"!

5. sudo update-grub

6. sudo reboot and done!

```

i also had to get rid of splash in /boot/grub/menu.lst because it was causing trouble and i couldnt get to login, but then who needs splash? gone with that
i also ran "sudo dpkg-reconfigure console-setup" and terminus at size 14 fits my machine the best!
anything under 13 was too small. and never got those double line problems since my machine doesnt have x..
ill probablynever install a xwin just because of that :)

anyways thanks!

---

### Post by nosneros on 2007-10-22
Glad it works, and glad to help! :) Although, I gotta thank RedSquirrel for the info on blacklisted modules!

---

### Post by wangjiaji on 2007-10-24
Thank you dosterror, your code works great.

---

