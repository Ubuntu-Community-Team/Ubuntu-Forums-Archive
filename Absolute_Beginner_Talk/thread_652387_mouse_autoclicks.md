---
title: "mouse autoclicks"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by rcl2884 on 2007-12-28
yup... absolute beginner here. I loaded Ubunto 6.06 on an aging Dell Laptop (inspiron 600m) and mostly so far so good. The trouble is the mouse sometimes thinks I clicked it when I haven't. For example, as I move the cursor across a web-site it will "click" on links even when I have not pressed anything.  This lap-top has a touch-pad and two click buttons. I looked through the mouse configuration settings for something that pertained to touch-pad sensitivity, but there is nothing. This is pretty annoying and makes surfing the internet nearly impossible. I note that the laptop did not have this problem when it used Windows XP. 

.. a possible related problem. My kids complain of slow mouse click response when playing games. 

Any suggestions?  

Thanks,
Rick

---

### Post by mejy on 2007-12-28
If you want more control over touchpad settings (one of which should probably fix this), you'll need to install the gsynaptics package (sudo apt-get install gsynaptics).  You'll then see a touchpad option under System -> Preferences.

---

### Post by rcl2884 on 2007-12-28
Thanks for the quick reply. I am such a newbie...I tried the command you suggested (sudo apt-get install gsynaptics) and received the reply "Package not found"

I tried down loading gsynaptics from SourceForge and extracted the files into a TMP folder, but I still do not know how to install. I did not see anything obvious (like a set-up file). What procedure do I follow to install this package?  Thanks for your patience.
...Rick

---

### Post by xeth_delta on 2007-12-28
> **rcl2884 said:**
> Thanks for the quick reply. I am such a newbie...I tried the command you suggested (sudo apt-get install gsynaptics) and received the reply "Package not found"

I tried down loading gsynaptics from SourceForge and extracted the files into a TMP folder, but I still do not know how to install. I did not see anything obvious (like a set-up file). What procedure do I follow to install this package?  Thanks for your patience.
...Rick

Ubuntu has a package management system through which you are able to install a large amount of software. You can either access it through command line tools, such as apt-get or aptitude. You can also use several graphical interfaces, for instance synaptic (different from synaptics) for Ubuntu, or Adept for Kubuntu.

I will assume you are using Ubuntu and you want to try synaptic. Make sure the Universe repository is enabled: Settings -> Repositories. Verify that the lines corresponding to Universe have are checked. Press OK, when finished and then Reload. look again for the program.

Xeth

---

### Post by Lostincyberspace on 2007-12-28
Have you tried loading a newer version of ubuntu? 6.06 is pretty old now, at least in computer time.

---

### Post by mejy on 2007-12-28
I'd definitely try using Ubuntu 7.10 - it's likely to have better support for your hardware and newer applications.  If you want to stick with 6.06, try searching for ksynaptics or qsynaptics which provide the same functionality.

---

### Post by rcl2884 on 2007-12-28
yes, I could not find gsynaptics, ksnynaptics, or qsnyaptics... and I did have the community repositiries checked. I believe I encountered an error installing version 7.04. originally, and rather than trouble-shoot, I installed an older version (6.06). I want to upgrade to 7.10. Do I need start boot off of a CD to do this, or is there some way to perform this upgrade from within my current version?

Thanks,
Rick

---

