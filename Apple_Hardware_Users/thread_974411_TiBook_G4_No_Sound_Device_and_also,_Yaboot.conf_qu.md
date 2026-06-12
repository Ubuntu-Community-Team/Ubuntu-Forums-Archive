---
title: "TiBook G4 No Sound Device and also, Yaboot.conf question"
date: 2008-11-07
forum: Apple Hardware Users
---

### Post by Elephex on 2008-11-07
Hello gurus!

I have a two-fold problem

1.) I have a g4 Powerbook (PPC) and ubuntu does not recognize any sound device. I want to use the onboard sound but i cannot even select it. 

2.) How do you edit /etc/yaboot.conf? I have tried to  append="video=ofonly" but i cannot save the file due to not having the proper authority. I assume i need to do this through Terminal with a sudo but am a total noob at this whole thing.

any help would be very much appreciated!

Thanks.

---

### Post by tiresia on 2008-11-07
> **Elephex said:**
> I have a two-fold problem

1.) I have a g4 Powerbook (PPC) and ubuntu does not recognize any sound device. I want to use the onboard sound but i cannot even select it. 
You can have here a look
[http://ubuntuforums.org/showthread.php?t=954307](http://ubuntuforums.org/showthread.php?t=954307)

> **Elephex said:**
> 
 2.) How do you edit /etc/yaboot.conf? I have tried to  append="video=ofonly" but i cannot save the file due to not having the proper authority. I assume i need to do this through Terminal with a sudo but am a total noob at this whole thing.

First of all, make a back up of your file
```
sudo cp /etc/X11/yaboot.conf /etc/X11/yaboot.conf.bak
```
If you have problems, you can restore it just copying it back
```
sudo cp /etc/X11/yaboot.conf.bak /etc/X11/yaboot.conf
```
To edit it
```
sudo nano /etc/X11/yaboot.conf
```

If you want to read some documentation on basic commands
[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

---

### Post by Elephex on 2008-11-07
> **tiresia said:**
> You can have here a look
[http://ubuntuforums.org/showthread.php?t=954307](http://ubuntuforums.org/showthread.php?t=954307)



First of all, make a back up of your file
```
sudo cp /etc/X11/yaboot.conf /etc/X11/yaboot.conf.bak
```
If you have problems, you can restore it just copying it back
```
sudo cp /etc/X11/yaboot.conf.bak /etc/X11/yaboot.conf
```
To edit it
```
sudo nano /etc/X11/yaboot.conf
```

If you want to read some documentation on basic commands
[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

Thanks for your help!

However, My sound issue is not related to not having volume, but when i click volume control a message pops up with the following:
No volume control GStreamer plugins and/or devices found


With the command to edit my yaboot.conf, I can get it to change the text, but cannot save the file. I assume I just exit the terminal after changing the text, but i cannot use ^X to do so. 

Sorry for the entry-level questions, I am learning but having a good time figuring these things out so far.

Thanks!

---

### Post by tiresia on 2008-11-07
> **Elephex said:**
> 
With the command to edit my yaboot.conf, I can get it to change the text, but cannot save the file. I assume I just exit the terminal after changing the text, but i cannot use ^X to do so. 


In 'nano' (the terminal text editor) the sign ^ means 'control'.
So you press just ctrl+X, to exit, and say yes to save the file

---

### Post by Elephex on 2008-11-07
> **tiresia said:**
> In 'nano' (the terminal text editor) the sign ^ means 'control'.
So you press just ctrl+X, to exit, and say yes to save the file

Ah! That is perfect. Thank you very much. So, that problem is solved. With the GStream business im thinking of trying the following 

sudo apt-get install gstreamer0.10-tools gstreamer0.10-x gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg gstreamer0.10-alsa gstreamer0.10-schroedinger gstreamer0.10-pulseaudio

That should solve it. Will post here when and if it does. 

Thanks!

---

### Post by Elephex on 2008-11-07
So, after changing my yaboot.conf file, i restarted and get the "white screen of death" again. Is there any way to bypass this? Last time I had to do a complete reinstall. 

Oh the joy of an old computer and a new OS!

---

### Post by Elephex on 2008-11-07
So, it booted to the white screen 2 times, then on the final try of 
Linux video=onlyif

It booted swimmingly.... This is perplexing, has anyone else had the same problems?

Elephex

---

### Post by stream303 on 2008-11-08
Just remember that after editing your /etc/yaboot.conf file, you need to make the system aware of the change with:

```
sudo ybin -v -C /etc/yaboot.conf
```

otherwise it will still use the values from the last time, even though the file itself has changed.

---

