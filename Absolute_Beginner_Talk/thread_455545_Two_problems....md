---
title: "Two problems..."
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by rukift on 2007-05-26
1. What would I have to do to get VLC media player my default for playing movies?

2. Ok, I think I majorly screwed up somewhere. Whenever I log in, the computer takes me to my desktop for a seconds, then a blank screen with a flashing underscore. After another few seconds, it takes me back to the login page! It's really irritating, I can't go on my computer anymore. ): Little help? Ubuntu's worked just fine for me for months, but out of nowhere it started doing this!

---

### Post by icechen1 on 2007-05-26
> **rukift said:**
> 
2. Ok, I think I majorly screwed up somewhere. Whenever I log in, the computer takes me to my desktop for a seconds, then a blank screen with a flashing underscore. After another few seconds, it takes me back to the login page! It's really irritating, I can't go on my computer anymore. ): Little help? Ubuntu's worked just fine for me for months, but out of nowhere it started doing this!

try this: [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by taurus on 2007-05-26
At the GUI login screen, press <Ctrl><Alt>F2 to get to a console.  Log in with your username and password.  Then, post the output of this command here.

```
df -h
```

---

### Post by Happy_Man on 2007-05-26
Well, you could set it in the preferred apps dialog, sorry I can't say more, it's been while since I last used GNOME.

---

### Post by SomethingCronic on 2007-05-26
> =2. Ok, I think I majorly screwed up somewhere. Whenever I log in, the computer takes me to my desktop for a seconds, then a blank screen with a flashing underscore. After another few seconds, it takes me back to the login page! It's really irritating, I can't go on my computer anymore. ): Little help? Ubuntu's worked just fine for me for months, but out of nowhere it started doing this!


This sounds like when your out of disk space. You may need to log into with terminal and delete some stuff. Remember to enter you /home/<name>/,Trash folder and clear out anything in there.

---

### Post by Happy_Man on 2007-05-26
Some cleaning codes to get you started:
```
sudo apt-get clean
sudo apt-get autoremove
```

---

### Post by rukift on 2007-05-26
> **icechen1 said:**
> try this: [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

That worked perfectly, thank you so much!

And oh, in the preferred applications thing... I tried that, and they only offer three choices for programs: your email, web browser, and command line. Nothing about anything else, but hey, I'm just thrilled my computer works again. :D

---

### Post by ugm6hr on 2007-05-27
> **rukift said:**
> 1. What would I have to do to get VLC media player my default for playing movies?

I use Xubuntu - so it might be different.... but:

In file manager (thunar for me - nautilus for you), find any media file you have and right-click.  This should give you an "Open with other application.." option - or something like that.  Click that, and then chose VLC.  There is an option to make this default for all similar files.

Just repeat this for every type of media file - .mp3, .xvid etc.  In fact, it allows you to specify a different media player for different file types - which might be handy.

---

