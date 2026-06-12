---
title: "[SOLVED] Resetting Xorg and"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by jdfoote on 2008-01-24
I'm still a Linux newbie, so bear with me.

I've been having a few problems with xorg using up a lot of resources, and I found a post saying that

 sudo dpkg-reconfigure xserver-xorg

might help. I didn't know which option to choose for a lot of the choices, and I'm afraid that I've made things worse. Sometimes on restart the GUI doesn't load correctly, and gives me a lower resolution until I mess around with the XORG GUI, and reset things.

In addition, I was watching a DVD tonight on VLC, and Xorg was using almost all of my cpu, and the video was choppy, etc.

Is there a way to restore my original settings?

I have a GEM GM-171B crappy LCD monitor, but I don't know how to check my video card. Let me know if you need to know anything else.

Thanks!!

---

### Post by emarkd on 2008-01-24
The only way to recover your old settings is to have made a backup of them before you reconfigured.

You can find your video card by running:

```
lspci
```

It'll be listed there somewhere.

Did you check to see if there are restricted video drivers available to you?  Click on System > Administration > Restricted Drivers Manager to check it

---

### Post by jdfoote on 2008-01-24
Darn - I knew I should have made a backup!

It says I don't need any restricted drivers - my VGA controller is:

Intel Corporation 82865G Integrated Graphics Controller (rev 02)



What should I do from here? :)

Thanks!

---

### Post by jon.reeve on 2008-01-24
In addition to your xorg maybe not being setup properly, if you're still experiencing choppy playback on VLC you could try changing the output module from within VLC. (settings -> preferences -> video -> output modules). But I'd say mess around with your xorg settings first though. A good way of reverting to autoconfigured settings is just to run the xorg wizard with the command you mentioned above, and just keep hitting enter, which selects all the default configurations. But definitely use 

lspci | grep VGA 

to get your video card first.

---

### Post by emarkd on 2008-01-24
dpkg-reconfigure is probably the right thing for you to do.  when you did it last, did you accept the defaults or did you go out on your own?  it's usually pretty good about getting things right without much input from you.

---

### Post by jon.reeve on 2008-01-24
ok. so you're probably going to want to use the i810 driver or something similar, it looks like. 

another way to revert to your old xorg.conf is to 

```
cd /etc/X11
cp xorg.conf~ xorg.conf
```

or, check your directory for files named similarly to xorg.conf, because there should be a few automatic backups if you've changed your configuration. for example, I have a file labeled xorg.conf.20080112165905 in my /etc/X11 directory, so to revert to that version I'd run
```

cd /etc/X11
cp xorg.conf.20080112165905 xorg.conf
```

---

### Post by jdfoote on 2008-01-24
Thanks so much! I'll play around with these when I have time (probably tomorrow) and post what I figure out.

I really appreciate your help - the Ubuntu forums are an amazing resource!

---

### Post by jdfoote on 2008-01-26
Resetting the Xorg settings (just through pressing OK on every screen) worked like a charm. Thanks so much for all of your help!

---

