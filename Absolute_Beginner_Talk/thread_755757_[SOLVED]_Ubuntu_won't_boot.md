---
title: "[SOLVED] Ubuntu won't boot"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by ben2talk on 2008-04-15
I recently deleted .gnome .gnome2 and other config folders, and reconfigured a lot of basics for my desktop. However, I had the problem that whenever I selected an audio file and selected to 'open with' a program (e.g. vlc) then it failed and locked up. vlc couldn't play anything at all! I then tried to follow a guide editing the /etc/modprobe.d/alsa-base which caused failed reboot. I deleted it and restored alsa-base~

Now I can't get to the login screen and I don't understand the contents of /var/log files...

Can anyone help with troubleshooting? I don't want to lose the hours spent setting up my virtualbox installation. From liveCD I'm having trouble with permissions too.

Also I'd like to back up some stuff if I need to reinstall, but using the liveCD I'm told I have no permission to access the files in my folders there....

---

### Post by Duckyspetrie on 2008-04-15
What exactly is it doing when you attempt to boot?

---

### Post by ben2talk on 2008-04-15
I booted the 'recovery' option a few times. It gets as far as:

'Starting Preload: preload.
                                    *Running local boot scripts (/etc/rc.local)                OK
                                                                                                                         __



Then it sits blinking...

---

### Post by forrestcupp on 2008-04-15
So you can't even get to the command line in recovery mode?  Is the 'blinking' you are talking about like a command line, or can you not do anything at all?  If you can at least get to where you can type a command by booting to recovery mode, type this:
```
apt-get --reinstall install ubuntu-desktop
```
Then reboot, and you should be ok.

If you can't even get to the command line in recovery mode, then you may just be screwed.  You may need to work on figuring out your permissions with the Live CD and backup your files so you can reinstall.  Then learn a lesson from all of this.

---

### Post by ben2talk on 2008-04-15
I did get to the command line. I did sudo apt-get purge gnome, and then install gnome....


The problem isn't so much gnome. I could log in to KDE or Enlightenment. Last time I had trouble getting my gnome up, I chose E-gnome and fixed it from there....

I can't get it to load up as far as the login screen.

You're full of beans, and thanks for the input, but I'm pretty confident that 'apt-get --reinstall install ubuntu-desktop' wouldn't get me very far.
The desktop is fine, I cannot get as far as the desktop. 

I need to get as far as the greeter so I can login and start a gnome/kde/enlightenment/xfce session.

This seems a rather hit and run affair - someone throws an answer in and quits? can anyone help with troubleshooting?
I'm now using XP :( is there any way to get access from here?

---

### Post by forrestcupp on 2008-04-15
I really think you should try what I said before dismissing it.  The ubuntu-desktop package isn't just the desktop.  It depends on everything that has to do with the desktop and getting you there including GDM, which is the login screen.  I think your problem came from when you deleted settings and folders that you shouldn't have.  If you reinstall and resetup your ubuntu-desktop package, which will also deal with all of its dependencies, there's a good chance it will work again.

Please try what I said earlier, and if it doesn't work, you won't be any worse off, and we'll go from there.

About people dropping in and leaving, all of the people helping out here are volunteers doing this on their own time.  That really can't be helped.

---

### Post by robertchahine on 2008-04-15
i wish this could help.
In case if you want to backup some files, boot your system from the liveCD

then post this in the terminal assuming your / directory it's /dev/sda1

```

sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu

```

then go to the folder /mnt/ubuntu and backup what you need 
hope this will help
(by the way thanks to TAURUS who told me about this)

---

### Post by ben2talk on 2008-04-15
Thanks, this looks useful. I'll try the previous command too, but it didn't reinstall anything last time...

---

### Post by ben2talk on 2008-04-15
Please accept the humble apology on offer here Mr Forrestcup. I didn't think that '--reinstall install ubuntu-desktop' was going to get me anywhere... it did in fact ask me if I was going to set gdm or kdm as the default.... and around 2 minutes later here I am in my lovely Opera browser answering you!

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif) sing your praises! I'm back on the road again.

I will, however, be trying to make some headway in understanding the boot logs and boot process.
I just spent a depressing hour or so trying to beef up the security in XP (I keep it for games, and didn't connect it to internet for a few months... that's the only way to use XP I think. Now if I want to play games, I need to uninstall lots of antivirus/spyware/autorun crap again so it can work quickly for me.)

Once again, thanks a lot. I hope you're there next time :P

---

### Post by forrestcupp on 2008-04-15
Hey, I'm glad it worked for you.  I can see how one would think what you did from the name "ubuntu-desktop"

Enjoy!

---

### Post by ben2talk on 2008-04-15
Well I came across gnome, kde xfc and enlightenment..... but ubuntu-desktop wouldn't have sprung to mind. Easy to remember though.

Interesting it couldn't have  been 'Desktop'. Ubuntu isn't too fond of English.

---

