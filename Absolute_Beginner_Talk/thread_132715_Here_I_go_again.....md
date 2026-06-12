---
title: "Here I go again...."
date: 2006-02-18
forum: Absolute Beginner Talk
---

### Post by qwazert on 2006-02-18
Everything was running fine on the old 450Mhz box. Then I did a "dual-boot" system on the family computer....
The Windows98SE portion is still fully-functional, I didn't lose any files, folders or data. Gparted is wonderful!

My problems are ALL in Ubuntu again. Here is a list of my outstanding (and unsolved) headaches:

1) MediaVision ProAudio Spectrum (PAS-16) soundcard is totally dead in the water. Not even recognized.
2) Desktop wallpaper vanishes each time I log in.
3) FireStarter firewall asks for password each time I log in...doesn't do that on my other computer!
4) When I log out with Ctl-Alt-Backspace, it takes me to some **Twilight Zone** from which I cannot return unless I reboot completely.
5) Firefox (v1.0.7) looks different than it does on the other box. Even the icon is missing the fox's head!

What have I done differently? I wish I knew...!

---

### Post by prizrak on 2006-02-18
1) No idea search the How-To's possibly maybe also this site [http://doc.gwos.org/index.php/Main_Page](http://doc.gwos.org/index.php/Main_Page)
2) Also weird
3) That's normal if you start the frontend for it, it needs to run as root.
4) It's not Twilight Zone it's the terminal just type your username and hit enter you will be prompted for a password put that in then type in "startx" w/o the quotes
5) That's also normal default Ubuntu install has a world as an icon as opposed to your normal fox around the world icon.

---

### Post by qwazert on 2006-02-18
Thanks for the reply(s)

1) I have found nothing ANYWHERE in the entire Google-Universe regarding this sound card. The fact that it has a modprobe entry (pas2) suggests that support IS there...but I am skunked to find HOW to make it work. It was a pain in Win95/98 and is proving to be just as frustrating in Linux. Maybe I'll just trash the thing and buy an SB!

2) I've tried setting the wallpaper as SUDO, regular user...to no avail. THEN, I set it and rebooted using the ***Save settings*** option and it is working now...go figure!

3) I use FireStarter on my other computer and it never asks for a password. I know it is functional, because it passes all the PORT tests at GRC.

4) ***StartX***...That's the command!!!:rolleyes: I tried several variations but got nowhere with it. 
Why is it that sometimes it simply restarts itself?

5) I think I may need to UPDATE some of the apps. 

Thanks again.

---

### Post by taurus on 2006-02-18
I have heard that those ATI radeon video cards would do that with X.  Personally, I always use nVidia and never have any problem with it.

---

### Post by nalmeth on 2006-02-19
> Twilight Zone Nice touch :) 
sorry, I don't know much about your sound card problem. 
Maybe the xserver is not configured properly, and likely you will need updates. You installed with a breezy CD?

---

