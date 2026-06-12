---
title: "Reinstall graphics drivers from grub"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by Yuck on 2007-09-02
Hi, 
further to this thread

[http://ubuntuforums.org/showthread.php?t=540940]("http://ubuntuforums.org/showthread.php?t=540940")

I think I may need to reinstall my graphics drivers. I think this because while my display is messed up clickable stuff seems to still be working. For example desktop documents that I know are there although I can't see them seem to open. I can only do this while in recovery mode through grub though. I've tried 
```

sudo apt-get install
```
and
```
sudo dpkg-reconfigure xserver-xorg
```
and still no joy. 
So I'm guessing that maybe I need to remove my current drivers first and then reinstall? How would I do this. Failing this I'm currently backing up to a second drive everything on my main partition, will I be able to get my emails, contacts and calendar back into evolution if I reinstall Ubuntu and then copy the old files back over?

---

### Post by overdrank on 2007-09-02
> **Yuck said:**
> Hi, 
further to this thread

[http://ubuntuforums.org/showthread.php?t=540940]("http://ubuntuforums.org/showthread.php?t=540940")

I think I may need to reinstall my graphics drivers. I think this because while my display is messed up clickable stuff seems to still be working. For example desktop documents that I know are there although I can't see them seem to open. I can only do this while in recovery mode through grub though. I've tried 
```

sudo apt-get install
```
and
```
sudo dpkg-reconfigure xserver-xorg
```
and still no joy. 
So I'm guessing that maybe I need to remove my current drivers first and then reinstall? How would I do this. Failing this I'm currently backing up to a second drive everything on my main partition, will I be able to get my emails, contacts and calendar back into evolution if I reinstall Ubuntu and then copy the old files back over?


HI and which driver did you choose for you graphics card during the reconfigure command? And what graphics card do you have?

---

### Post by Yuck on 2007-09-02
Hi I choose the nvidia, I have an nvidia 6800. 
I've looked at the backup xorg.conf, that also had the nvidia driver listed. Which has been working fine for about 2 months until yesterday. It's more than a little weird.

---

### Post by overdrank on 2007-09-02
> **Yuck said:**
> Hi I choose the nvidia, I have an nvidia 6800. 
I've looked at the backup xorg.conf, that also had the nvidia driver listed. Which has been working fine for about 2 months until yesterday. It's more than a little weird.

Ok well run the command again and choose vesa as the driver and hopefully that will get you to the gui and then you can go from there. I don't think a reinstall is called for.

---

