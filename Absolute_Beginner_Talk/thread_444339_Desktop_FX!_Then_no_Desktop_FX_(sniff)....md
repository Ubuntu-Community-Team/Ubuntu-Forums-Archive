---
title: "Desktop FX! Then no Desktop FX (sniff)..."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by kobinasucks on 2007-05-15
I downloaded Edgy onto my Dell Inspiron 6000 about two months ago, updated it to Feisty and haven't looked back since. However Desktop Effects would not work in either Edgy or Feisty, giving me the message:

"Desktop Effects Could Not Be Enabled"

I assumed it was a Beta problem or some Dell/Ubuntu compatibility issue (like loss of use of my media keys) until I had to reinstall Feisty again after one tweak too many. This time I did it from CD and all of a sudden, Desktop FX worked perfectly and I even got to toy with/marvel at Beryl.

In a moment of noob stupidity, I deleted my fglrx driver. Another reinstall later and now Desktop Effects once more doesn't work. 

I love Ubuntu anyway, but since I had a taste of Compiz/Beryl I've become like an internet crack addict, waking up in cold sweats at early hours of the morning, scurrying from forum to forum online for a fix. I can wait happily for the Compiz/Beryl reunion but if I could just get my simple Wobbly Windows and Cube back I'd be a better human being.

Can anyone help me?

Tried completely removing Compiz, Beryl, Desktop FX and all related files in Synaptic PM and  reinstalling them but still... nothing.

What is an addict to do?

---

### Post by netwerx on 2007-05-15
Is it a ATI Radeon Video Card? If so, have you tried going through the following tutorial...

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

I used that do get my dell laptop (c640) working with beryl.

Might wanna run that.  Also, posting your xorg.conf may help as well.

---

### Post by bmk789 on 2007-05-15
I would try reinstalling the video driver, reconfiguring X by running ```
sudo dpkg-reconfigure xserver-xorg
``` and retrying

Good luck

---

### Post by kobinasucks on 2007-05-15
Thankyou  both for getting back to me

> **netwerx said:**
> Is it a ATI Radeon Video Card? If so, have you tried going through the following tutorial...

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

I used that do get my dell laptop (c640) working with beryl.

Might wanna run that.  Also, posting your xorg.conf may help as well.

Erm, is there any command I could type in that would tell me whether I have an ATI card? The best I could think of was to visit [this page]("http://www.larsonsworld.com/misc/linux-on-dell-6000.html") which suggests that I don't.

Oh, and how do I access my xorg.conf files (and post them) :oops: 

bmk789: I tried reconfiguring X but the configuration screen that popped up is the same one that I tampered with last time and ended up crashing my machine, so I started going thru it but chickened out in the end. I really am new at this and wasn't sure if any adjustments I made would cause the same problem as last time. Is there a noob guide for this?

Update: I enabled ATI accelerated graphics driver in my Restricted Drivers. Still not sure if I have an ATI card but now when I click on Desktop Effects it says "the Composite Extension is not available". Going to try Netwerx' suggested tutorial now... (I hope it won't have some disastrous effect if I DONT have ATI!) :eek: 

Thanks again.

---

### Post by netwerx on 2007-05-15
from what i can tell, you have a "64 MB ATi Mobility Radeon X300"

That tutorial may work for you. However it was from a fresh install, i don't know what the state of your machine is now.

Good luck.

---

### Post by kobinasucks on 2007-05-15
Netwerx, you're the man.

Worked like a charm. Upon the first reboot I got a blank white screen and thought to myself "sh*t". Then I restarted it again and everything was working perfectly. Have rebooted a few times since and I think I'm good to go.

Big thanks.

---

### Post by netwerx on 2007-05-15
Don't thank me, thank the person who wrote that article. 
I was just the messenger.  Glad to hear it worked.

---

