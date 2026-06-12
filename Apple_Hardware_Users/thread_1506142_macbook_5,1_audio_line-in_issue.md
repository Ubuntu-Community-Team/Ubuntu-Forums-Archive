---
title: "macbook 5,1 audio line-in issue"
date: 2010-06-10
forum: Apple Hardware Users
---

### Post by undeuxtrois on 2010-06-10
Hi everyone,

I've seen the many posts on the Ubuntu forums concerning the audio issues of the MacBook 5,1 ...

I was just wondering, did someone manage to find a way to get the audio line-in to work ?

I'm using Karmic with 'linux-backports-modules-alsa-karmic-generic' version 2.6.31.22.35 and specifying 'options snd-hda-intel model=mb5' in /etc/modprobe.d/alsa-base.conf makes everything work, except the line-in (line-out, internal speakers and internal mic are all functional).

However, I've found that with 'options snd-hda-intel model=auto', both audio line-in and internal mic work, but no speakers and no line-out...

Can anyone confirm this ?


Patrick

---

### Post by alexmurray on 2010-06-10
Line-in doesn't work on my MacBook Pro 5,1 either - I was just thinking of looking into this and wondered if it didn't work on the non-Pro as well, so thanks for the confirmation. Interesting that model=auto works - can you post the output of running:

```

cat /proc/asound/card0/codec#0

```

for both when using model=mb5, and then when using model=auto - will hopefully be able to cook up a fix in the next few days with this info.

---

### Post by undeuxtrois on 2010-06-11
Hi Alex,

Here it is... I hope it helps !

---

### Post by alexmurray on 2010-06-13
I've written a short patch against alsa-driver-1.0.23 which should enable line-in correctly on the mb5 model which you can grab from my Dropbox account.

To use it, you'll first need to uninstall any version of linux-backports-modules-[karmic|lucid]-alsa that you've got installed (as these will override the manually compiled and installed modules which we're about to build).
Then download alsa-driver-1.0.23, patch it, compile and install the new drivers:

```

cd ~
wget http://dl.dropbox.com/u/174251/alsa-driver-1.0.23-mb5-inline-fix.patch
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2
tar xjf alsa-driver-1.0.23.tar.bz2
cd alsa-driver-1.0.23
patch -p1 < ../alsa-driver-1.0.23-mb5-inline-fix.patch
./configure
make
sudo make install

```

Then simply reboot and with any luck line-in will now work as expected.

Let me know if you have any problems.

---

### Post by alexmurray on 2010-06-14
As an update, this patch has been [accepted upstream]("http://git.kernel.org/?p=linux/kernel/git/tiwai/sound-2.6.git;a=commit;h=b8f171e7e7ed5c9b77324bcc6bb580ddcc84da49") by the ALSA developers so with any luck this change will make it into Maverick Meerkat 10.10 so that the line-in will work automatically without having to manually patch and recompile the drivers.

---

### Post by undeuxtrois on 2010-06-14
Alex, this works like a charm. Thank you very much for that.

---

### Post by alexmurray on 2010-06-15
No worries, thanks for providing the info and impetus to fix it - I had been meaning to track this down for a while as it was the only thing on my MBP5,1 that still wasn't working (compared to OSX). Cheers.

---

### Post by Sh4dounet on 2010-09-04
Just a message to thanks Alex if it will works in Maverick it will be so cool.

But does will work for not macbook too ? I mean, I didn't managed to enable sound on my line-in speakers on my computer (which is not a Mac Book).

Any solution ?

(Or I simply have to way the release of Maverick ?)

Thanks

---

