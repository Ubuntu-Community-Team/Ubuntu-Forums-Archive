---
title: "No sound"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by BobLand on 2007-05-10
Today, for no apparent reason, sound stopped.  I cannot play any sound in any application.  The only thing I did was change the system fonts.  Prior to this event, sound worked in all applications.

One app flashed a quick message saying something wasn't installed but it was too quick for me to jot down.

Is there a set of libraries that I can run that will play all of the popular Windows and LInux sound files and enable xine and VCL?

Thanks,
Bobland

---

### Post by paydaydaddy on 2007-05-11
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)
hopefully the above works as a link. If not, go to the multimedia forum and search for comprehensive sound. you should find a very useful thread for troubleshooting sound problems.

---

### Post by just learning on 2007-05-11
I don't know about you bobland but i tried muting and unmuting various controls in volume control in my panel and found out if i muted pcm control my sound came back.have not had a problem since.hope you figure it out.

---

### Post by crete_des_izards on 2007-05-11
This sounds very much like the problem dicussed in [[COLOR="Red"][COLOR="RoyalBlue"]this thread[/COLOR][/COLOR]]("http://ubuntuforums.org/showthread.php?t=437640"). I had the same problem and this fixed it good. Good luck

---

### Post by BobLand on 2007-05-11
After running the steps in the above link, going all the way and finding the chipset driver, I still got no sound.

I went to the sound panel in System/Prefs/Sound and had 4 of the same driver - ca0106 for my Sound Blaster Audigy LE.  Interestingly enough, the literal name of the card was not listed.  By doing some digging I found that I could use this driver.  Since I did not download it, it must have been in the kernal or elsewhere.

It wasn't until I selected the 4rh iteration of the driver that I got the test tone.  I ran a DVD for testing but it did not work so I rebooted.  When U came up I got the login in sound and after logging in the rest of the music.

I'm not clear if I did a lot of smoke and mirrors, meaning that the drivers were there and I some how selected wrong ones (defaulted to autodetect which didn't) or the routine did do something.  Either way, I learned a lot about how sound works and how to troubleshoot.

This is one of the things I love about Linux - total control.  I suppose this is a good thing and a bad thing.  Good for me as a learning effort, but bad for the very novice user.

Thanks guys.  I'm up and running!
Bobland

---

### Post by SaddaGocaraRupa on 2007-05-11
have you restarted your machine yet? i had that problem sometimes, like my sound would work just fine, i'd turn it it off and the next day it was gone. well, what it did it it replaced my soundcard with the webcam, which of course isn't able to play any sound whatsoever.

 there's a terminal line that permantly stores your sound settings, it's further down in the 'Comprehensive Sound Problem' thread. Worked for me..

---

### Post by BobLand on 2007-05-11
Bizzare.  Lost the sound again.  Ran thru the above link.  All of the configuration had changed.  My card was slot 0-ca0106 (the correct driver) where before it was card1.

Since everything was really there, just masked as something else, I believe all I had to do was run the "...-purge remove linux-sound-base..."; "...install linux-sound-base..." followed by a reboot.  Then everything came back.

As the configuration is "saved" I'm hoping that it stays put.

bobland

---

