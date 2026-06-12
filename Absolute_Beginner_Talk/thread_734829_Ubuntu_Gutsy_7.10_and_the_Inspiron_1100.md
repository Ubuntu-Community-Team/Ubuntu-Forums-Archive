---
title: "Ubuntu Gutsy 7.10 and the Inspiron 1100"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by Heratiki on 2008-03-25
Just thought I would put a couple of tips for those trying to install Ubuntu on a Dell Inspiron 1100 or 1150 (As these both have the 845G Videocard onboard and the ACPI problem)...

So here is what I did...

I popped in the CD and started up the laptop and made it boot the CD...

Please bare in mind that my bios version is A32 so even though I did have a few problems the first go around trying to install you have to have atleast this bios version.  That way you won't have a multitude of problems while trying to run it...

Get to the first screen and make sure you choose the 2nd Option (If your using the LiveCD) which would be the Safe Graphics Option...

The system will take some time (dependent on RAM if you can go buy 1GB for this machine it will fly then) to boot and eventually you'll be in the LiveCD environment...  Once there do one thing... Go to the Applications button...  Then Accessories and then choose Terminal (Gnome Terminal)...   That should start up your term program...   Before installing make sure you edit your xorg.conf file by typing > sudo nano -w /etc/X11/xorg.conf  When it opens simply scroll down to the line that says

> Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:0:2:0"
EndSection


And change it to...

> Section "Device"
        Identifier      "Generic Video Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

After you make the change hit Ctrl-O and it will save and then hit Ctrl-X to close it...
Now that that is done you can begin the install (which takes some time) so go get a magazine or watch TV or donate to the Ubuntu cause...

Ok your install is completed and it's asking you to reboot...  Go for it...  But after the machine reboots make sure you hit Esc at the screen that pauses right before Ubuntu starts so that you get the Ubuntu Boot Menu...

Choose the first entry and hit "e"...  This will send you to the grub line editor...  Choose line 2 which should look something like this... 

> kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2857f9a7-146b-408f-820e-08fa73702a50 ro quiet splash (not exact but almost)

And move all the way to the right to the end of the line and add these two things so that it looks like this...

> kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2857f9a7-146b-408f-820e-08fa73702a50 ro quiet splash nolapic acpi-off

Hit Enter to save the line...  Hit the up arrow to go to the first line and hit b to boot...

This is just precautionary as sometimes I would boot ok with and without this...  But it always would boot with it...

Now your in Ubuntu and it's all working... Almost...  Open up another Terminal Window (Applications - Accessories - Terminal) and type this > sudo nano -w /boot/grub/menu.lst

It should open the file... Scroll down quite some ways until you see the line we just edited before when we were in the Grub Boot editor...  Go to the very end of the same line and add those two items again...  Just because we did it before doesn't mean they were saved just that grub knew to boot with those parameters that time...  After adding nolapic & acpi-off to the very end you can hit Ctrl-O to save it and Ctrl-X to close it... And type exit to close the Terminal window...  And now your done... Even after the first update (200+ packages) you will still have a working system...  Just make sure you keep an eye on those two files (/etc/X11/xorg.conf    --    /boot/grub/menu.lst) so that if one of the updates changes what is in them you know what to change them back too...  Hope this helps and it's always good to get Linux running on a lost cause... These machines are so cheap now they make for great fun and with my 1GB of RAM I can run World of Warcraft... w00t...

Heratiki

EDIT:  Just a side note... It's probably a good idea to install i8k-tools and grellm-i8k after your install to keep watch on your processor temperature as these machines have had problems in the past with Linux in general and overheating...  The grellm-i8k plugin allows you to control the fan speed as well which makes keeping it cool or quiet much easier...

---

