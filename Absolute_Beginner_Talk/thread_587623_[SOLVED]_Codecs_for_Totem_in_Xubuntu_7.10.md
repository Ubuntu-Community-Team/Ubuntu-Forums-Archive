---
title: "[SOLVED] Codecs for Totem in Xubuntu 7.10"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by santiagoward2000 on 2007-10-22
Hi everyone!
I just installed Xubuntu Gusty in my machine. I'm having problems getting Totem to work. I've already installed ALL the gstreamer packages in Synaptic, and added the w32codecs from Medibuntu. I tested it with some videos I had on my drive. There were no problems with .ogg (of course), .wmv and .asf. But I couldn't get .mov, .mpg and .mpeg to work.
With the .mov files I get:
> Video codec 'JPEG' is not handled. You might need to install additional plugins to be able to play some types of movies

And with .mpg and .mpeg files I get:
> There is no plugin to handle this movie.

Does anyone know what packages I'm missing?
Thanks

---

### Post by RomeReactor on 2007-10-22
Hi. Maybe you're missing the **gstreamer0.10-ffmpeg** package:
```
sudo apt-get install gstreamer0.10-ffmpeg
```

If that doesn't work, try switching Totem from gstreamer to xine:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine1-plugins
```

I don't know if you need the **libxine1-gnome** package, though.

---

### Post by santiagoward2000 on 2007-10-23
> **RomeReactor said:**
> Hi. Maybe you're missing the **gstreamer0.10-ffmpeg** package:
```
sudo apt-get install gstreamer0.10-ffmpeg
```

If that doesn't work, try switching Totem from gstreamer to xine:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine1-plugins
```

I don't know if you need the **libxine1-gnome** package, though.

Thanks RomeReactor! You made me found the problem! It seems Xubuntu 7.10 comes Totem Xine and I was installing the gstreamer codecs #-o
So I tried to install the Xine codecs, but I got this:
> Either the application requires special hardware features or the vendor decided to not support your computer type.
So I installed the Gstreamer version of Totem and it did it!
Thanks!!

---

### Post by Zipzit on 2007-11-20
> **santiagoward2000 said:**
> Thanks RomeReactor! You made me found the problem! It seems Xubuntu 7.10 comes Totem Xine and I was installing the gstreamer codecs #-o
So I tried to install the Xine codecs, but I got this:

So I installed the Gstreamer version of Totem and it did it!
Thanks!!

I'm getting exactly the same errors.  What I don't understand is, how do you 'get' the Gstreamer version of Totem?  My Add/Remove Applications shows the Gstreamer codecs, but I don't see Totem-Gstreamer listed anywhere (either on the Add/Remove Applications menu, when set to 'all available applications'  or in the Synaptic Package Monitor.  I can see a generic Totem (which appears to be a place holder?) and the Totem xine in the Package Monitor.  

Am I doing something wrong?  this is really my first time using package manager, on a new installation, first time user..   Oops.  I think I figured it out... I need to check All the boxes on what's available for package manager (Package manager, Settings, Repository, tab for Ubuntu software, check Canonical... community maintained... proprietary drivers... software restricted...)  Now I see it!  Yow, there is a lot of stuff available!

Question posted and answered for any other virgins who might stumble here!

thanx, zip.

---

### Post by santiagoward2000 on 2007-11-30
> **Zipzit said:**
> I'm getting exactly the same errors.  What I don't understand is, how do you 'get' the Gstreamer version of Totem?  My Add/Remove Applications shows the Gstreamer codecs, but I don't see Totem-Gstreamer listed anywhere (either on the Add/Remove Applications menu, when set to 'all available applications'  or in the Synaptic Package Monitor.  I can see a generic Totem (which appears to be a place holder?) and the Totem xine in the Package Monitor.  

Am I doing something wrong?  this is really my first time using package manager, on a new installation, first time user..   Oops.  I think I figured it out... I need to check All the boxes on what's available for package manager (Package manager, Settings, Repository, tab for Ubuntu software, check Canonical... community maintained... proprietary drivers... software restricted...)  Now I see it!  Yow, there is a lot of stuff available!

Question posted and answered for any other virgins who might stumble here!

thanx, zip.

Sorry for the delay, I hadn't seen your post before. In case you haven't figured it out, in **Add/Remove Applications** Totem for Gstreamer appears simply as **Movie Player**.
I had to uninstall **Movie Player Totem (xine backend)** before installing it.
Cheers!

---

