---
title: "My head hurts...flash player hates me...deaden my pain"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by CRIMPS on 2007-04-11
To Start, I am still very new to Linux.  My primary problem, I believe, is that I still am very unfamiliar with the inner workings of Linux.  I have been unable to comprehend how to consistently install programs/apps, etc.   Just trying to get flash to work at all has been a nightmare.  I have done some extensive research through these forums as well as browsing through psychocats.net and monkeyblog.org/ubuntu/installing/#source.  I have installed through cutting and pasting scripts provided  by these websites but I cant seem to get any of these to work.  Websites such as YouTube, etc will show no video or just keep telling me to install plugins(shockwave-flash).   When I try to manually install using the "sudo make install", "make", and a couple others, I usually get errors such as "not a directory".  Here is another attempt:

zach@zach-desktop:~/Desktop/install_flash_player_9_linux$ $ ./flashplayer-installer
bash: $: command not found
zach@zach-desktop:~/Desktop/install_flash_player_9_linux$  ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

I feel like I should take drastic measures, but I know I feel this way because I really don't have a good understanding of the command line yet.  I actually want to reinstall Ubuntu and just start over.  Should I just stick it out and keep looking for other methods?

Thanks and sorry I wasn't more forthcoming with a question

Athlon 64
dual boot with Win XP
dapper drake


Z

---

### Post by Outrunner on 2007-04-11
There might be something about this here: [http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox](http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox)

---

### Post by Bachstelze on 2007-04-11
If you're using the default Firefox that comes with Ubuntu, all you need it :

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by aysiu on 2007-04-11
> **Outrunner said:**
> There might be something about this here: [http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox](http://ubuntuforums.org/showthread.php?t=202537&highlight=firefox)
Read outrunner's link.

They don't make Flash native for 64-bit on Linux. You need a workaround. That link is the workaround.

---

### Post by dhtechs on 2007-04-11
Try using Automatix2...this simplifies running install scripts...especially for the inexperienced.

[http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.17-6.06dapper_i386.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.17-6.06dapper_i386.deb)

---

### Post by aysiu on 2007-04-11
> **dhtechs said:**
> Try using Automatix2...this simplifies running install scripts...especially for the inexperienced.

[http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.17-6.06dapper_i386.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix2_1.1-2.17-6.06dapper_i386.deb)
Automatix now installs the 32-bit Flash player to a 64-bit system? That's news to me.

---

### Post by Bachstelze on 2007-04-11
Oh, 64 bits, I guess I didn't read carefully enough, please ignore my post.

---

### Post by dhtechs on 2007-04-11
Sorry gave u the wrong link...try this:

[http://www.getautomatix.com/apt/dists/dapper/main/binary-amd64/automatix2_1.1-2.16-6.06dapper_amd64.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-amd64/automatix2_1.1-2.16-6.06dapper_amd64.deb)

---

### Post by matthew on 2007-04-11
> **dhtechs said:**
> Sorry gave u the wrong link...try this:

[http://www.getautomatix.com/apt/dists/dapper/main/binary-amd64/automatix2_1.1-2.16-6.06dapper_amd64.deb](http://www.getautomatix.com/apt/dists/dapper/main/binary-amd64/automatix2_1.1-2.16-6.06dapper_amd64.deb)

Rather than using a script, I recommend the OP read Outrunner's link.

Side note: we have an official forum statement on the use of scripts to install things: [http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)

---

### Post by CRIMPS on 2007-04-11
Outrunner, 
Thanks for the link.  This seems to be a great starting place.  Anyone else had problems installing firefox or swiftfox or Iceweasel?  On the link provided by Outrunner, I am told to first download and install "ia32-lib-firefox-amd64", then install firefox or swiftfox or iceweasel.  The "ia32" file downloaded and installed successfully, but when I try to install any of the other files I get this error

error:  Cannot install "ia32-libs".  It seems no matter what I try I get errors.  I am using firefox right now.  Does that mean I am using a 64bit version?  

Thanks for all the help!

---

### Post by jputman01 on 2007-04-11
I wasn't ever able to get flash working on 64bit firefox, and as far as i knew it couldn't work (at the moment anyways). my solution was to install 32bit opera browser on my 64bit ubuntu using the force architecture command. after that it was pretty simple to get flash and java working properly, and i was pleased to notice opera actually ran a bit faster than my firefox (in my opinion) this way i got to keep my default 64bit firefox and i have opera with flash in case i need it until a simple way for getting flash in 64bit firefox comes around. I think i saved my steps on my laptop if you would like to try it this way. let me know and ill post them up!

---

### Post by CRIMPS on 2007-04-11
Jputman-

I think you might have the best idea so far.  Nothing is working for me in regards to updating from firefox to firefox32.  I must be doing something completely wrong because there should be no reason for compatibility issues between AMD64-firefox-flash.  These are major apps/chips...

Maybe an upgrade to edgy or feisty soon could help?  Anyone know?

Z

---

