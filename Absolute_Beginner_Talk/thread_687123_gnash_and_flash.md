---
title: "gnash and flash"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by nateperson on 2008-02-04
Running ubuntu 7.10; (Duel booting XP, cause I'm still need my M$ methadone....)

Have been using gnash, one my linux partition for a while but many flash sites don't work with it...  Synaptic says I've got adobe flahs player installed but I when the option came up back when, I told Firefox to use gnash (cause I want FOSS), unfortunately flash sites don't work properly...   Question is, how do I get flash sites to either A work properly with gnash or B, get firefox to switch over to proprietary Adobe flash?

---

### Post by oedha on 2008-02-04
get the flash player from here :==> [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

then install it
you can play swf from firefox after that

~E~

---

### Post by nateperson on 2008-02-04
Thanks, 

But can you pretend that your talking to a long time windows user / linux user (cause I am) and go a little farther than that?

---

### Post by Faud on 2008-02-04
The flash in the repos is broken which is why it is saying that its installed and not working properly. So just uninstall it and then reinstall from a trusted source outside of the repos.
Hope that is what you were looking for.

---

### Post by nateperson on 2008-02-04
Cool, but my Firefox is set to use gnash which only supports up to swf7, which is cool, 85% of the time...  But how do I tell it to use adobe?

---

### Post by stchman on 2008-02-04
> **oedha said:**
> get the flash player from here :==> [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

then install it
you can play swf from firefox after that

~E~

Flash 9 is in the repos.

```
sudo apt-get -y install flashplugin-nonfree
```

For Feisty or higher.  Edgy has Flash 9 in the backports.

---

### Post by nateperson on 2008-02-04
And I thank you too,

But,  many flash sites still don't work after doing that... 

But I'm pretty sure gnash is still set to run with my firefox, updating and reinstalling adobe doesn't seem to change that...  

I mean, I'm knocking it, I have found it functional for most applications but for the stupid sites that have to have the newest ****, it don't work when for some specific **** that I need....

So, am I completely off my rocker or is this just not possible with ubuntu and firefox? If not, I got a XP partition I'm trying to to crawl back on the wagon away from...

---

### Post by Vadi on 2008-02-04
Don't use gnash, it's not usable yet. Remove it.

Download this: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

Right-click on it, and extract it. Then, open the terminal and cd to the directory with the files that were just extracted (if you'll need help on this, let me know). Then do "sudo ./flash_installer" (I don't remember the exact name of it.. but just do "sudo ./<name>")

When it asks you for the path - I think you need to give it /usr/lib/mozilla or /usr/lib/firefox, can't remember which. After that it'll be done, restart firefox and it should work.

(that sounds confusing, reading over it.. but at 2am that's the best I can manage. I'll explain better tomorrow if you'll still need help)

---

### Post by juky on 2008-03-22
> **stchman said:**
> Flash 9 is in the repos.

```
sudo apt-get -y install flashplugin-nonfree
```

For Feisty or higher.  Edgy has Flash 9 in the backports.


I have used those instructions and it worked!

But first, gnash was removed trough synaptic package manager.....

Cheers!

---

