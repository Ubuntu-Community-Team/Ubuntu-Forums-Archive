---
title: "laptop brightness problem"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by short3000y on 2007-12-06
anytime i try to change the brightness on my laptop, my screen goes black, is there any way to fix this?:(

---

### Post by short3000y on 2007-12-06
can anyone help?

---

### Post by betes on 2007-12-06
I probably don't have an answer for you, but others might be more helpful if you give more details.  What laptop do you have? What version of ubuntu are you running? How are you changing your brightness settings?

---

### Post by short3000y on 2007-12-06
i have a gateway m285e and running 7.10, and i have a ati mobility radeon 1400 graphics card and it happens any way i try to adjust the brightness... but i never had a problem with XP

---

### Post by short3000y on 2007-12-06
...please help me

---

### Post by betes on 2007-12-06
It looks like this is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/149547](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/149547)

The bug seems to only display the screen at certain brightness settings.  To confirm that this is the same bug try to keep brightening (or darkening) the screen after it goes black to see if you can get to another value that will display. For example, if it displays at 100% but goes plack when you darken it, keep darkening to see if it redisplays at 75% or some other number.

I didn't read the above launchpad link that carefully, but it seems to be something that won't get fixed until the next Ubuntu version comes out in April.

---

### Post by Swmmrman on 2007-12-06
I had a gateway laptop myself.  I found something in the bios to change to stop that behavior.  Not sure what it was.  I wish you the best of luck in this.(i know it drove me nuts)

---

### Post by Netrunner on 2007-12-07
i have a similar problem too.
brightness applet got my screen dark (like turned off)
rebooting it's dark again (possibly bios or monitor has memory of last brightness?)
so to see something i had to remove the battery (my awful quick way not suggested to anyone) during power on.
(guess you can use an external monitor if u're not in my hurry)
at the restart i can see the console and everything, but when i log into gnome, screen get dark again.
my solution has been to switch to kde.
don't know if there is a config file that i can edit from console to set the applet brightness.
nor wich commands are used by the applet.
brigthness function key on keyboard do not work on my acer aspire 5920
i use latest updated version of gutsy.
if someone has a solution please help. i want to understand the problem.
but i'm happy with kde.

---

### Post by betes on 2007-12-07
@netrunner: You could try reinstalling gnome.  Or if you can get into the terminal in gnome (which might be hard if its dark) you could adjust the screen brightness from the command line using:

echo -n 100 > /proc/acpi/video/VGA/LCD/brightness

(where 100 is the percentage brightness).

---

### Post by Netrunner on 2007-12-07
Thank you for your tips betes. I already reinstalled gnome. But even if kde works fine, gnome keep his previous settings. My aim is to find them. Because when i switch to the reinstalled gnome everything gets dark, and all i can do is:
control + alt + f1 (i can't see anything but there should be a console)
make the login
and try typing
echo -n 100 > /proc/acpi/video/VGA/LCD/brightness
but nothing happens. Even with sudo. i tryed also:
sudo /etc/init.d/gdm stop (or) restart
if i give the command echo -n 100 > /proc/acpi/video/VGA/LCD/brightness within kde (also sudoing it) it says permission denied but function keys work. 
But that do not solve the gnome problem. Now it's dark again. Unless i can find a config file to edit i better stick with kde.
Someone know if there is a config file for brightness?


ps. could it be that a notebook monitor or bios have a sort of memory for brightness? 
It's so strange that after shutdown it continues to be dark at reboot untill i take out the battery, i'd espected it to get dark loading X server or gnome, not before as a monitor default.

Anyway i guess editing the file where the GNOME_BrightnessApplet store his brightness setting should be fine, but i don't know anything about that applet or where is that file. and gconf-editor didn't help (i use it from kde of course)
Another solution would be to inhibit the load of the applet (if i knew how to do it without gnome...)

---

### Post by Netrunner on 2007-12-09
anyway i just solved in another way.
i know it is not suggested but without knowing wich file i had to edit i resetted to default gnome.
terminal and

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

no more applet setting my screen dark.
:)
anyway knowing the file of the help would have been more painless.
:lolflag:

---

### Post by Izek on 2008-02-12
> **Swmmrman said:**
> I had a gateway laptop myself.  I found something in the bios to change to stop that behavior.  Not sure what it was.  I wish you the best of luck in this.(i know it drove me nuts)

I have this problem too, and I tried setting the "Operating System Type" (Like you were getting at) to "Other," but it doesn't help.

I want a fix for this too. ALL brightness settings for my **Gateway MX6931** besides 100% will cause the screen to flicker or go black. This is a problem when I remove my power cord, as Ubuntu will **auto-adjust** the brightness to something lower.

---

### Post by Izek on 2008-05-09
> **Izek said:**
> I have this problem too, and I tried setting the "Operating System Type" (Like you were getting at) to "Other," but it doesn't help.

I want a fix for this too. ALL brightness settings for my **Gateway MX6931** besides 100% will cause the screen to flicker or go black. This is a problem when I remove my power cord, as Ubuntu will **auto-adjust** the brightness to something lower.

This problem for auto-adjusting seems to have been fixed for me in Ubuntu 8.04.

---

