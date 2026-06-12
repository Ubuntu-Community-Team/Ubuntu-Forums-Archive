---
title: "Why isn't flash working?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by Airforcefalco on 2008-03-01
I thought I installed Adobe flash but it still won't display flash files and it isn't giving me the option to install anything else. Any suggestions?

Thank you!!!

---

### Post by Bubba64 on 2008-03-01
If your using Firefox did you install from Mozilla addons if not that would be your probably best way also here is a link to how to install everything you need.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by Airforcefalco on 2008-03-01
Thank you for the link! I went there and read and tried to follow the directions but something came up. I replied in that thread but i am not sure how long it will be to get a reply so i am posting my reply here also.

I have Gutsy and when i typed in the command line

sudo apt-get install alsa-oss compizconfig-settings-manager faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll icedtea-java7-jre icedtea-java7-plugin liblame0 msttcorefonts unrar w64codecs

it came back with

E: Couldn't find package gstreamer0.10-pitfdll

I dont know how to edit a command line yet but i was hoping someone could help me out!

Thank you!

P.S. Can someone explain to me what all that stuff means anyway?

---

### Post by SunnyRabbiera on 2008-03-01
well firstly how did you install flash?
I remember there being an error with it not so long ago so lets start from there.

as for what those commands you typed in the terminal are:
apt-get: apt/apt-get is a tool ubuntu uses to install packages
Sudo: a way to get into administrative mode

It looks like you had an error downloading a package, for beginners I say ignore the terminal and go to system> administration> synaptic package manager.
Synaptic is a graphical front end to apt

---

### Post by Airforcefalco on 2008-03-01
Well i first installed adobe (i think) when a website said that it needed it. But even doing that has cause a lot of problems because the flash still doesn't work.

I followed the guide that Bubba64 linked too up until the system specific code that i copied there (i have dual opterons so i am using the 64bit ubuntu) and then when i used that command that was what came back. I'll post the whole thing

nick@The-Falcos-Box:~$ sudo apt-get install alsa-oss compizconfig-settings-manager faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll icedtea-java7-jre icedtea-java7-plugin liblame0 msttcorefonts unrar w64codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
E: Couldn't find package gstreamer0.10-pitfdll

I tried using synaptic but i can't find flash :-(

---

### Post by Airforcefalco on 2008-03-01
Oh and how do i use the multi quote button on the forums?

Thanks again!

---

### Post by zetjee on 2008-03-01
what worked for me is this:

Download the adobe flash package to you desktop (manual) Than extract it all and put this in /home/user/.mozilla/plugins

than it should work.

---

### Post by forrestcupp on 2008-03-01
The easiest way to get flash working is to open up Synaptic and go to Settings->Repositories.  Then click the 'Updates' tab and check the boxes next to 'Pre-released updates' and 'Unsupported updates.'  That gives you extra repos with newer versions of things.  Then close that window, and in Synaptic click the Reload button.  Then you can do a search in Synaptic for flashplugin-nonfree, install it, and it will work.

You will have to restart your browser, though.

And you use the multi quote button by pressing the button directly to the right of the normal quote button on as many posts as you would like to quote, then click the Post Reply button and it will bring up a Reply box with all of the quotes you chose.

---

### Post by Airforcefalco on 2008-03-01
> **forrestcupp said:**
> The easiest way to get flash working is to open up Synaptic and go to Settings->Repositories.  Then click the 'Updates' tab and check the boxes next to 'Pre-released updates' and 'Unsupported updates.'  That gives you extra repos with newer versions of things.  Then close that window, and in Synaptic click the Reload button.  Then you can do a search in Synaptic for flashplugin-nonfree, install it, and it will work.

You will have to restart your browser, though.

And you use the multi quote button by pressing the button directly to the right of the normal quote button on as many posts as you would like to quote, then click the Post Reply button and it will bring up a Reply box with all of the quotes you chose.

Ahh thank you very much i will see if that works here in a minute!

---

### Post by goldsniper on 2008-03-01
go to synaptic... search for ubuntu-restricted-extras and install it!

---

### Post by Bubba64 on 2008-03-01
gstreamer0.10-pitfdll is in synaptic just copy and paste into search. Hope your quest is working it takes a few times of figuring out the extras and for me having a desktop and a laptop to refer to when working on a new distribution. I just realized that the gstreamer package might be in my synaptic due to it being part of an install.

---

