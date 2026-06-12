---
title: "Migrate Settings"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by abhiroopb on 2008-01-28
Computer Specs:
15.4" HP Laptop
2gb Ram
256mb Nvidia geforce go 7400
100gb HD

Ubuntu 7.10

I have my laptop set up EXACTLY the way I want. I have considered buying a new laptop but the only thing holding me back is the fact that over the years I have cumulatively added numerous settings and changes. E.g. linking ctrl+alt+delete to the gnome-settings manager. and multiple settings for compiz. Even if I can save these I have made so many random settings changes (e.g. tweaking ubuntu so its faster, etc) that I can't even remembe. Plus of course there are numerous keyboard shortcuts, mouse gestuires and program settings.

So is there anyway to just copy and paste ALL the settings for another computer? I want it to be EXACTLY the same. I don't want simply the settings for the programs, (and my files I can manage). Everything is working for me now: webcam, hard drives, mouse, keyboard, speakers, etc. So I want these left intact.

Is there any such procedure? I know the mac allows for this so I need some help with this.

Regards

---

### Post by macogw on 2008-01-28
Er...well, you could copy the entire hard drive to the new computer, but if there are hardware differences, you'll have to work around them (like reconfiguring xorg.conf for if you need a different video driver).

---

### Post by abhiroopb on 2008-01-28
I considered the harddrive copy idea...in fact I use partimage to backup my entire HD...but     like you said I'm confident I'll have numerous hardware issues. I haven't really thought about WHICH laptop to buy so I don't know how different the hardware will be. But I'm guessing the wireless card, sound card, graphics hard, hard drive, will be different....how difficult would it be to reconfigure all of these?

In any case what about this ubuntu migration assistant I heard about somewhere...

---

### Post by macogw on 2008-01-28
Hard drive takes no reconfiguration.  Graphics card is just changing xorg.conf (Gutsy's failsafe X thing should help there, otherwise, it's typing "sudo dpkg-reconfigure xserver-xorg" and picking out the driver and resolution you want).  Wireless card might require installing some new drivers (by the way, I recommend a computer that says "Centrino" because that means it uses Intel wireless which works very well).  Wireless card and sound card might both want you to list which drivers to use in /etc/modules.  Other than that, it should be OK.  I've straight-up booted other computers from my hard drive and had them work fine without changing anything.

---

### Post by abhiroopb on 2008-01-28
thanks a lot! real relief...I guess best is to buy the new laptop and try it out!

Thanks again

---

### Post by dandellion on 2008-01-29
All the personal settings are in your /home folder. Just keep it (and don't forget all the hidden folders - those whose names begins with a dot) and everything will be there, including contents of the trash can.

---

### Post by abhiroopb on 2008-02-28
What would be the easiest way to clean out my system? I usually don't have much Trash, but is there anywhere else I should look for to clean up?

Any system files, install files, etc?

---

