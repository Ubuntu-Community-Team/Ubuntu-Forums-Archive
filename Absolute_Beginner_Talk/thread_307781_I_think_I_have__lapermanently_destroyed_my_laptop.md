---
title: "I think I have  lapermanently destroyed my laptop"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by SultanTravi on 2006-11-27
**THANKS TO ALL WHO HELPED! I'M SLOWLY GETTING THE SITUATION UNDER CONTROL, NO MORE HELP NEEDED ON THIS TOPIC!**


EDIT: Biggest concern now
I need to get GParted to work with NTFS.

OK, here are the problems I have.  I've spent 2 days Googling and searching the help files for anything that can help me, and have ended up right where I started.

I installed Ubuntu because I wanted to try out Linux.  I know my way around Windows and computers better than the average user (but nothing compared to most you guys), so I figured I would try one that seemed user-friendly.

I installed 6.10 on a partition on my HDD.  It's an 8 GB partition.

I quickly discovered that I had somehow messed up Windows.  If I try and boot windows, it says that autochk could not be found, flashes the blue screen of death, and reboots.  I found the problem--my Windows partition is hidden.  I know how to fix it (change the 0x17 to 0x07 on the drive hex info using ptedit), but since I am having trouble installing dosemu and creating a bootable flash drive, I can't.

Also, my microphone will not work.  I have tested sound output, which is fine, and also made sure that my inputs are not muted.  Everything is maxed.  No input will work.

Finally, my Firefox is very buggy.  For some reason, random pages (including Gmail) will crash the program--it closes instantly and without warning.  Additionally, while typing, random text from things I've looked at appears (very odd).

Anyway, I'm wondering what my best course of action at this point is.  Should I try installing a fresh Ubuntu (one of the earlier versions) on this partition? I don't have my Windows disc accessible, and I'm hoping to regain productivity ASAP.

Thanks, sorry about the long post.  I hope it's in the right place.  I'm wary about doing anything else for fear of further messing up my laptop.

---

### Post by xpod on 2006-11-27
Mabey you would have been better with Dapper as apose to Edgy..

FF 2 in Edgy has been problematic for quite a few people seemingly but i cant say i`ve really had any issues with it.

Cant really give you much real help as i just stumble along myself but mabey trying Dapper lts is the way to go.

Good luck regardless

---

### Post by adam.tropics on 2006-11-27
Do you just mean you need to change the flags for the xp partition from hidden, because, whilst I am not vouching for it, gparted can do that.

---

### Post by SultanTravi on 2006-11-27
Thanks guys.  Gparted? I'll look for it.  

Yeah, I'm thinking I better change down to Dapper.  From what I've seen, that would be better for a beginner and more stable.

---

### Post by xpod on 2006-11-27
Edgy`s just as stable me thinks but Dapper has the LTS and would mabey have been the better option.

Although Gparted is on the cd, with ubuntu installed you`ll need to also install Gparted if you wish to check stuff with it as it dosent actually come with the install

To install Gparted you can either look for it in Synaptic..Or you can just type
```
sudo aptitude update
```

then

```
sudo aptitude install gparted
```

You can type that in the terminal which is found in your applications>accesories>terminal

Of course none of that will matter just now if your going to go with Dapper
No point going through all the updates and stuff just yet if thats what your going to do....

---

### Post by gn2 on 2006-11-27
The gparted live cd should help you get fixed.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Doubt you have harmed any hardware, it's more likely that your microphone needs some work to get it going in Ubuntu.

---

### Post by SultanTravi on 2006-11-27
Thanks guys.  I installed Gparted--but I don't seem to know where it is.  I'm looking for it now.. this is kind of embarassing.

I also downloaded the Live CD.

---

### Post by steve.horsley on 2006-11-27
For a command line proggy, **sudo fdisk /dev/hda** should allow you to change the type of the partition. It's in the default Ubuntu install.

---

### Post by adam.tropics on 2006-11-27
> **SultanTravi said:**
> Thanks guys.  I installed Gparted--but I don't seem to know where it is.  I'm looking for it now.. this is kind of embarassing.

I also downloaded the Live CD.

system>>administration>>gnome partition editor

---

### Post by SultanTravi on 2006-11-27
Okay, I have Gparted running successfully.  However, I can't figure out how to install NTFS support.  If some one could give me the command for that, I think I'd be good to go (at least with Windows).

---

### Post by seshomaru samma on 2006-11-27
Cant help you with Gparted
I use QTparted 
(you can get it by running this command:
su```
do apt-get install qtparted
```)
The interface is similar to Gparted but when you right click on a partition you have the option to make it active

however , from your description it seems like your windows partition is broken and should be fixed with a windows CD
no harm in trying with qtparted or gparted though...

---

