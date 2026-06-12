---
title: "Not a noob. Need help G3 iMac lubuntu 12.04 install"
date: 2013-02-18
forum: Apple Hardware Users
---

### Post by imacg3ppc on 2013-02-18
So i had a very interesting, time consuming saturday attempting to install 12.04 precise on my iMac g3 flower power special edition. specs:

600mhz
640mb ram
40 gb HD
airport card

So it took me about 5-8 installs to finally get through the installations. I had to install in cli-expert-powerpc from the alternate iso. I had to change the partition table to set up a separate /home partition in order to even 'install base system'. Then i had to remove installation options sshserver, print server, and email server (which i'll prob need to get back later but anyway) to get the software install to go to 100%.

I was new to lubuntu, as i havent messed with linux since before fedora took over red hat. So i'm not a complete stranger. But i'll tell you, i know that installation ISO fricken inside and out now, every option and command LMFAO.

Problem symptoms:

I turn on imac. I get to yaboot where it automatically loads the phrase "Linux" then screen goes white, prom init and yada yada and then I ACTUALLY DO GET the blue lubuntu screen with the 4 progress dots underneath.

Then... it just goes to a prompt
"lununtu@lubuntu~$"

so i believe i either have a graphics issue (hopefully) or maybe the install didn't take. not sure. Looking for help on this from you powerpc people. I HAD TO PICK UP THE FLOWER POWER IMAC FOR $85 so dont ask me why are you doing this. The purpose of this box is for my kids to use for school, surfing, reports, text, lite games, and for me to manage my torrents and massive media collection (ext ieee1394 HD)

It ran good with OS X on it, but not good enuf. so im looking for this lubuntu to unleash the inner mac and then i will dress up LXDE with the os x lion theme that ive seen around.

Trying to find what i have in there for video hardware.... but the first install fried the OS X installation on my HD! thats how i figured out i had to manually partition and choose the separate /home partition (which is ok i like all my stuff separate)

I'll be checking for replies to this thread and i may be able to help with others who are trying to install on a ppc so shoot me some questions if no one else is answering!

---

### Post by imacg3ppc on 2013-02-18
i have consulted the almighty wikipedia and learned that my "Flower Power" edition came standard in early 2001 with:

ATI Rage 128 Pro graphics processor (AGP 2X) with 8 MB of memory or ATI Rage 128 Ultra (AGP 2X) with 16MB of memory

so i do have at home (where i'm not right now) some documentation on configuring the xorg.conf but the problem is i have no other pc. Have an awesome macbook pro with a bad logic board and this imac is supposed to be a cheap replacement until i can get the logic board replaced!!

anyone have any info on how to boot into lubuntu with this ATI setup? im almost positive I'm just not able to boot into X. i have tried 'start x' and 'run x' but just goes back to "lubuntu@lubuntu~$" waiting for my next command. i don't know too many commands. I need to pick up a linux dictionary.
 :guitar:

---

### Post by danield on 2013-02-18
It sounds like you need to make an /etc/X11/xorg.conf file, or edit one if you already have it.  If you google you can find example files for your model.  Someone posted theirs in this thread:

[http://ubuntuforums.org/showthread.php?t=1573909](http://ubuntuforums.org/showthread.php?t=1573909)

Many more examples here:

[http://mac.linux.be/content/xorgconf-files](http://mac.linux.be/content/xorgconf-files)

Hope that helps!

---

### Post by imacg3ppc on 2013-02-19
Can't wait to try it out, thanks a lot for the links, have a feeling i'm going to find a real home here. I'll let you know how it worked out.

---

### Post by imacg3ppc on 2013-02-19
I found some useful info in the powerpc faq. Hoping someone who has done this install would be able to tell me exactly which settings need to tweaked in the xorg.conf... will be messing around with this for a little while tonight. if i can get it working i will be really excited.

on a side note... does anyone else LOVE VCR's, VHS tapes and old cartoons? (80's and 90's) If you do, PM and well talk business.

---

