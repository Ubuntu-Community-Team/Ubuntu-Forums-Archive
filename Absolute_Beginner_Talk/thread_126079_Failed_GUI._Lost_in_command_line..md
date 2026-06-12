---
title: "Failed GUI. Lost in command line."
date: 2006-02-05
forum: Absolute Beginner Talk
---

### Post by SumoJim on 2006-02-05
Ok, I was working with Hoary Hedgehog and trying to figure out how to update things like OpenOffice and Gaim... Someone told me to update to Breezy first. They said to open some file and change all of the words "Hoary" to "Breezy" and then type sudo apt-get update into the command line. So, I did.... I then noticed that if I tried to open a new program it would try to start and then quit with no errormessage or warning. I then restarted my computer and it couldn't load Gnome and was presented with the command line which I have very little experience with. I know I have KDE on my computer somewhere but I don't know how to start it from the command line. The only thing I can really figure out on my own is how to change directories... If anyone could help me get Gnome or KDE to load I would really appriciate it... I would perfer Gnome but since it seems  to have some sort of error now KDE may be the easier solution.

Thanks!!
Jim

---

### Post by taurus on 2006-02-05
If you want to start X again, then type this at the prompt,

startx

However, sounds to me like you have a bust xorg (X)!!!  You can look in /etc/X11/xorg.conf or read /var/log/Xorg.0.log to see what's wrong with it and fix it.  Otherwise, backup your personal files and install Breezy the right way then!

---

### Post by SumoJim on 2006-02-05
I tried typing 
"sudo /etc/X11/xorg.conf"
and
"sudo /var/log/Xorg.0.log"
directly into the command line with no sucess. I cannot backup my files because I don't know much about the command line.... Is there a way to copy to CD from the command line?

I'm guessing I'll have to reboot with my "Hoary Hedgehog" install CD... Lose all my data and start again... I don't remember if I had anything important on there... If this is the case I may be just about done with Linux... Learning Linux is getting to be way too frustrating.

If anyone can guide me through this it would be greatly appriciated.... I will need someone to hold my hand though and tell me EXACTLY what to type.

---

### Post by BoyOfDestiny on 2006-02-05
[QUOTE=SumoJim]I tried typing 
"sudo /etc/X11/xorg.conf"
and
"sudo /var/log/Xorg.0.log"
directly into the command line with no sucess. I cannot backup my files because I don't know much about the command line.... Is there a way to copy to CD from the command line?

I'm guessing I'll have to reboot with my "Hoary Hedgehog" install CD... Lose all my data and start again... I don't remember if I had anything important on there... If this is the case I may be just about done with Linux... Learning Linux is getting to be way too frustrating.

If anyone can guide me through this it would be greatly appriciated.... I will need someone to hold my hand though and tell me EXACTLY what to type.[/QUOTE]

Hi. Well if you changed all the instances of hoary to breezy in your sources.list, you are golden.
Here is what you do.
Reboot
press escape to go into the grub menu
choose "recovery mode"

once everything is done, you'll be at a prompt with the word root.

Type this stuff:

apt-get update
apt-get dist-upgrade

Wait patiently, when everything is done, type
reboot.

Then use your system as normal...

That should do the trick! You will have a full fledged breezy, instead of hoary.

If things don't work out... I'd suggest to make /home on a seperate parition, so you can reinstall ubuntu (or other linuxes) and not lose your personal data and settings...

Best of luck!!

EDIT: I'll be out for a few hours, but I just want to mention why I recommend doing a full upgrade. The person gave you bad advice (mixing breezy with hoary). What you should use is called "hoary-backports" search the forums on it here. I'm guessing something broke by mixing, do doing a dist-upgrade to breezy might fix the problem. Also, there is breezy-backports that has even newer software, again search the forums... If it is really xorg that broke (somehow I doubt your xorg.conf changed) you can try running sudo dpkg-reconfigure xserver-xorg... Anyway good luck to you once more. Also, upgrading in this way, you won't lose settings or data...So don't worry, you've got nothing to lose.

---

### Post by SumoJim on 2006-02-06
Ok, I tried
sudo apt-get update
again and the final error that shows up reads:
"Some index files have failed to download, they have been ignored, or old ones used instead"

I have no idea what this means so I tried looking into backporting.... It seems I need to know whether I have Breezy or Hoary. At this point I am not sure anymore. How can I check from the command line?

---

### Post by taurus on 2006-02-06
If you want to view the content of a file, then do

more <filename>

If you want to edit a file, assuming it's a system file, then do

sudo pico <filename>

---

### Post by newuser111 on 2006-02-06
probably your display driver was broken in the updated kernel

do sudo dpkg-reconfigure xserver-xorg and select vesa

not sure if you are using ati or nvidia

---

### Post by SumoJim on 2006-02-06
I don't know.... I guess I'm just going to re-format my hard-drive and start from scratch... Thanks for trying to help.

Jim

---

