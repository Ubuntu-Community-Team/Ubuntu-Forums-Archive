---
title: "Resolution"
date: 2005-05-29
forum: Absolute Beginner Talk
---

### Post by Shaun on 2005-05-29
Hi everyone, I'm 100% new to the world of Ubuntu or anything non-Windows as a matter of fact.

I've just had 1 problem so far. In the initial Ubuntu setup, it asked me which resolutions not to show. I usually like to use 1280x1024 but I hit Enter to select that resolution to show it but instead it gave it the go-ahead to only use 640x480, 800x600 and 1024x768 :(  ](*,) 

It now only shows those 3 resolutions under System/Preferences/Screen Resolutions.

So the question is, how do I enable the greater resolution?

Thanks  :grin:

Edit: I have sorted it out, thanks ;)

---

### Post by Mez on 2005-05-29
[QUOTE=Shaun]Hi everyone, I'm 100% new to the world of Ubuntu or anything non-Windows as a matter of fact.

I've just had 1 problem so far. In the initial Ubuntu setup, it asked me which resolutions not to show. I usually like to use 1280x1024 but I hit Enter to select that resolution to show it but instead it gave it the go-ahead to only use 640x480, 800x600 and 1024x768 :(  ](*,) 

It now only shows those 3 resolutions under System/Preferences/Screen Resolutions.

So the question is, how do I enable the greater resolution?

Thanks  :grin:

Edit: I have sorted it out, thanks ;)[/QUOTE]
 although you've sorted it out, this might be useful to someone else

To reconfigure these options, run the command

```
sudo dpkg-reconfigure xserver-xorg
```

Assuming you're using Hoary of course ;)

---

### Post by thekore on 2005-05-30
I two had issues with the initial resolution. I was stuck at 640x480 on a 17" LG (L1715S) TFT with a GeForce (64MB) Dual head VGA Card.

I tried the above reconfigure command but to no avail, i had to edit the xorg.conf file in /etc/X11/ to add im my Horizontal Sync rates and Vertical Refresh rates :)

---

### Post by Mez on 2005-05-30
if you use the above command, then it will let you enter your sync rates (if you use the advanced monitor setup)

and also means that dexconf will still continue to edit the files ;)

---

