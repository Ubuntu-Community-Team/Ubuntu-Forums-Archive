---
title: "I've tried it all, and still can't open website videos on Firefox"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by wmichaelb on 2007-12-08
I'm just a little into Ubuntu, but I can *not* get videos on websites to play on Feisty, although everything worked fine on Dapper. When I go to Youtube, I consistently get a message from Totem that there is no plugin available for SWF. I've enabled and updated everything from Add/Remove Macromedia Flash through Medibuntu and Automatix, but it makes no difference. I can't even see the images on some web sites. I suspect that there is some sort of switch that I'm missing. Does anyone have a suggestion on where to go from here?

Thankyouthankyouthankyou in advance.

---

### Post by Kingsley on 2007-12-08
Read through this guy's guide. If you follow it logically, I guarantee that you'll have Flash working perfectly.

[http://www.smorgasbord.net/2007/06/29/how-to-install-firefox-flash-plugin-in-ubuntu-linux/](http://www.smorgasbord.net/2007/06/29/how-to-install-firefox-flash-plugin-in-ubuntu-linux/)

---

### Post by daradib on 2007-12-08
FYI:

There is a very recent bug, caused by Adobe's update of Flash 9.0 update 3 (9.0.115.0) codename "Moviestar" on December 4th.

[http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html](http://www.adobe.com/aboutadobe/pressroom/pressreleases/200712/120407adobemoviestar.html)

This affects anything using the flashplugin-nonfree package.

This causes Ubuntu to not install the flash plugin, detecting a change in the flash plugin installer file (via MD5 checksums). See [bug 173890]("http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890"). This bug has been fixed in the next release of Ubuntu (Hardy 8.04) and it should soon come as an update to Ubuntu 7.10 and 7.04 and later 6.10 and 6.06.

If you want an immediate fix, do the following.

Using Synaptic Package Manager, remove the package flashplugin-nonfree.

Alternatively, you can run this command in the Terminal (Applications -> Accessories -> Terminal): sudo apt-get remove flashplugin-nonfree

Then just download this package (32-bit only) and install it (it is identical to the current package in the next release of Ubuntu, Hardy 8.04): [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)

If you have 64-bit Ubuntu, you currently need to build a binary package from this source package: [http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2](http://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/9.0.115.0ubuntu2)

---

### Post by daradib on 2007-12-10
For more information on this bug, see [http://ubuntuforums.org/showthread.php?p=3929669](http://ubuntuforums.org/showthread.php?p=3929669)

---

### Post by wmichaelb on 2007-12-18
daradib: thanks for your reply! However, after installing the 32-bit version as above (I'm running a 32-bit board with a Sempron processor), I still cannot run a Youtube video. I get an error message from Totem that says "Totem could not play 'http://www.youtube.com/active_sharing.swf'. There is no plugin to handle this movie". Synaptic now shows that that plugin has been installed. Might you have any other suggestions? 

Thanks in advance for your time and help.

---

### Post by Presto123 on 2007-12-18
The most simple way I have ever found is to just install it from their site, either some people have over complicated things, or it doesn't always work on their systems. But, I will say this, on both of my computers(Entirely different parts, one running 7.10 and other running 7.04), I have never run into problems doing it this way...

First, definitely get rid of your other version if it is having so much problems. Then follow the fix I have posted in this thread:

[http://ubuntuforums.org/showthread.php?t=644147](http://ubuntuforums.org/showthread.php?t=644147)

I wish you luck in it.

---

### Post by Presto123 on 2007-12-18
The only thing I can see that might hinder this is that you are running it in Totem. ??? I haven't tried using totem to play the videos all that much...but it usually works with this install of flash.

---

### Post by daradib on 2007-12-18
> **wmichaelb said:**
> daradib: thanks for your reply! However, after installing the 32-bit version as above (I'm running a 32-bit board with a Sempron processor), I still cannot run a Youtube video. I get an error message from Totem that says "Totem could not play 'http://www.youtube.com/active_sharing.swf'. There is no plugin to handle this movie". Synaptic now shows that that plugin has been installed. Might you have any other suggestions? 

Thanks in advance for your time and help.

Did you use the proposed repository to install the new packages or did you install a debian package? If you used the proposed repository, then you should remove the packages you have installed, and install the packages provided on the thread.

This is why: [https://bugs.launchpad.net/ubuntu/dapper/+source/flashplugin-nonfree/+bug/173890/comments/73](https://bugs.launchpad.net/ubuntu/dapper/+source/flashplugin-nonfree/+bug/173890/comments/73)

---

### Post by Presto123 on 2007-12-18
Are you agreeing that what I have proposed is a good idea or are you thinking something different?

---

### Post by daradib on 2007-12-18
I think the plugin is not actually installed, and that is why Totem is attempting to do something it can't do.

---

### Post by Presto123 on 2007-12-18
Okay, I get what you mean now. ;)

Yeah from what his stuff is saying...It looks as though he HAS the ability to install it now...just not the actual plugin. (If that makes sense...LOL)

---

