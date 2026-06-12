---
title: "Plz Help, computer not booting"
date: 2006-09-16
forum: Absolute Beginner Talk
---

### Post by solo88 on 2006-09-16
I apologize if I am asking some dumb questions, but I have only been using ubuntu for a few weeks now.  And, I am still trying to figure things out.

So, I was attempting to install xgl on my machine.  I used the second part of the following guide:

[http://www.ubuntuforums.org/showthread.php?t=219336&highlight=install+xgl+compiz+ati](http://www.ubuntuforums.org/showthread.php?t=219336&highlight=install+xgl+compiz+ati) 

I skipped the first part, because I already had my radeon drivers installed and working properly (ATI Radeon 9200).  I logged out and back in and everything was still working when I selected the Gnome session.  With the XGL session, the only apparent problem was that when I was typing the letters would appear very, very slowly (a couple of seconds between each one).  I rebooted the machine and now I see the Ubuntu login splash screen for just a second then it goes blank with a flashing cursor but know login prompt.

So, how do I recover without re-installing?  Is it possible at this point?  And is there a way to get a login prompt without trying to start the X server?  I could reinstall without losing much data, but I don't really want to fight with my video card again (dumb me didn't write down the exact guides/steps that I used before).

This may be getting a bit ahead of myself, but after I fix the machine and get back to gnome, what do I need to do to get xgl / compiz up and running. All I really want is the cube animation (or something similar) and true transparency on my terminal window, so if there is another (simpler) way to get those things, I might be happier without xgl.

In case it helps here are my system specs (that I can remember):
AMD 1.4GHz processor
ATI Radeon 9200
1.5 Gb Ram

Thanks

---

### Post by threethirty on 2006-09-16
I'm having trouble with xgl too, the way i get my cube fix is 3ddektop, just go into synaptic it will be in the frist couple of packages in the all catagory.

---

### Post by xhaan on 2006-09-16
> **solo88 said:**
> I apologize if I am asking some dumb questions, but I have only been using ubuntu for a few weeks now.  And, I am still trying to figure things out.

So, I was attempting to install xgl on my machine.  I used the second part of the following guide:

[http://www.ubuntuforums.org/showthread.php?t=219336&highlight=install+xgl+compiz+ati](http://www.ubuntuforums.org/showthread.php?t=219336&highlight=install+xgl+compiz+ati) 

I skipped the first part, because I already had my radeon drivers installed and working properly (ATI Radeon 9200).  I logged out and back in and everything was still working when I selected the Gnome session.  With the XGL session, the only apparent problem was that when I was typing the letters would appear very, very slowly (a couple of seconds between each one).  I rebooted the machine and now I see the Ubuntu login splash screen for just a second then it goes blank with a flashing cursor but know login prompt.

So, how do I recover without re-installing?  Is it possible at this point?  And is there a way to get a login prompt without trying to start the X server?  I could reinstall without losing much data, but I don't really want to fight with my video card again (dumb me didn't write down the exact guides/steps that I used before).

This may be getting a bit ahead of myself, but after I fix the machine and get back to gnome, what do I need to do to get xgl / compiz up and running. All I really want is the cube animation (or something similar) and true transparency on my terminal window, so if there is another (simpler) way to get those things, I might be happier without xgl.

In case it helps here are my system specs (that I can remember):
AMD 1.4GHz processor
ATI Radeon 9200
1.5 Gb Ram

Thanks

I think something broke your xorg.conf
Try rebooting into recovery mode and replace xorg.conf with the backup that  you hopefuly made, or try
dpkg-reconfigure xserver-xorg

---

