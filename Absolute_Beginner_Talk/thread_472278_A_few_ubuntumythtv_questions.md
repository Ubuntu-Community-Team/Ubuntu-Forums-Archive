---
title: "A few ubuntu/mythtv questions"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by -silent- on 2007-06-12
Sorry for all the questions I'm about to ask, I'm pretty new to this stuff.

I've installed ubuntu feisty alternate AMD64 as instructed here: [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend")

That all went fine, but as I'm trying to set up mythtv, I'm doing all of this on my 32" samsung lcd. Well there is too much overscan or something so I can't see the outer limits of the screen. How do I change the resolution? (when I was trying knoppmyth you could change the modelines in the /etc/X11/xorg.conf, but  I don't seem to have that file.

Second, I need to get the drivers for my hdhomerun tuner as stated here: [https://help.ubuntu.com/community/HDHomeRun]("https://help.ubuntu.com/community/HDHomeRun")

How do I actually get those files? I couldn't get wget to work with those urls.


Those are my 2 big problems right now. I really appreciate the help.

---

### Post by Hendrixski on 2007-06-12
hey, you've come to the right place to ask questions.  That's how we all started out here... and then we just loved Ubuntu so much that we stick around and answer questions for other newcomers.

you DO have an /etc/X11/xorg.conf file... otherwise your computer would not have any visual interface... it would be just a command line.  You can configure your resolution with System-->preferences-->screenResolution... no need to edit a file by hand... 'cause that's the way we used to do Linux back in the 90's ... this is Ubuntu.

I don't have that tuner.. but I've heard it can be a pain to set up...

---

### Post by Hendrixski on 2007-06-12
Most importantly
WELCOME TO THE COMMUNITY!!!
like I said before, we're all here because we love Ubuntu, and want to share our joy with everyone else.  You can also go to IRC for help,  we're on channel #ubuntu.  if you want to ask the guys at mythtv for help on how to set it up, go to the channel #mythtv-users and they may help (or may be asleep and not answer).

Also, find other Ubuntu users in your area with the ubuntu LoCo teams.  Your city probably has one, and they're tons of fun.

---

### Post by -silent- on 2007-06-12
> **Hendrixski said:**
> hey, you've come to the right place to ask questions.  That's how we all started out here... and then we just loved Ubuntu so much that we stick around and answer questions for other newcomers.

you DO have an /etc/X11/xorg.conf file... otherwise your computer would not have any visual interface... it would be just a command line.  You can configure your resolution with System-->preferences-->screenResolution... no need to edit a file by hand... 'cause that's the way we used to do Linux back in the 90's ... this is Ubuntu.

I don't have that tuner.. but I've heard it can be a pain to set up...


Actually, I don't have a visual interface. :p  As per those instructions, I installed command line.

Thanks for the warm welcome! I'm sure I'll have lots of questions and really appreciate the great community.

---

### Post by -silent- on 2007-06-12
Any ideas on how to change the resolution/modeline in command line?

Or how to download those hdhomerun drivers?



Thanks!

---

### Post by -silent- on 2007-06-13
Should I repost/move this to a more specific forum? Is there a ubuntu/mythtv forum here?

Thanks!

---

### Post by mjwhitfield on 2007-06-13
i'm sure someone will have the answer soon :)

---

### Post by baekster on 2007-06-26
> **-silent- said:**
> Sorry for all the questions I'm about to ask, I'm pretty new to this stuff.

Second, I need to get the drivers for my hdhomerun tuner as stated here: [https://help.ubuntu.com/community/HDHomeRun]("https://help.ubuntu.com/community/HDHomeRun")

How do I actually get those files? I couldn't get wget to work with those urls.


Those are my 2 big problems right now. I really appreciate the help.

I have HDhomerun.  The thing you're trying to install isn't quite a "driver" but config tools to upgrade firmware (which you might already have the latest).  Anyhow.  I'm also running feisty amd64 version.  I think I ran into problems of the packages being type i386, which 'dpkg' complains and won't install.  I just installed it from the source.  [http://download.silicondust.com/hdhomerun/libhdhomerun_20070620.tgz]("http://download.silicondust.com/hdhomerun/libhdhomerun_20070620.tgz")

$> tar zxf libhdhomerun_20070620.tgz
$> cd libhdhomerun
$> make
$> export PATH=.:$PATH

After that you should be able to run the hdhome_config, etc from that directory.

As for the driver, you don't need anything.  The new mythTV (feisty version) has the support for hdhomerun built in.  Just follow the mythTV guide in the url you have there.

---

