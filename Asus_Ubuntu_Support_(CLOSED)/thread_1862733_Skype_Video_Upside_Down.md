---
title: "Skype Video Upside Down"
date: 2011-10-17
forum: Asus Ubuntu Support (CLOSED)
---

### Post by kharaku on 2011-10-17
I have an ASUS P50IJ.

In Skype the video of me appears upside down.

I followed the advice on some of the other threads but nothing seems to fix it without breaking something else.

Does anyone have recent news on this issue?  (I'm reluctant to upgrade to 11.10, but would doing that fix it?)

Thanks!

---

### Post by nykilde on 2011-10-17
My Skype on Asus X5DAF is also upside down, but Google Talk and Hangout (Google+) works perfect. The combination Asus laptop and Skype and Linux doesn't seem to go hand in hand. So sorry, don't have any advice on the matter, but would also like to hear what can be done to correct it.

---

### Post by kharaku on 2011-10-18
> **nykilde said:**
> My Skype on Asus X5DAF is also upside down, but Google Talk and Hangout (Google+) works perfect. The combination Asus laptop and Skype and Linux doesn't seem to go hand in hand. So sorry, don't have any advice on the matter, but would also like to hear what can be done to correct it.

My understanding is that skype tries to run in 32 bit mode even when ubuntu is installed 32 bit...

---

### Post by hotweiss on 2011-10-23
Here's the solution that worked for me:

1. sudo apt-get install lib32v4l-0

2. sudo mv /usr/bin/skype /usr/bin/skype.real

3. sudo gedit /usr/bin/skype

4. Paste:

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real

5. sudo chmod +x /usr/bin/skype

Then start Skype from the dash as you would normally.

---

### Post by tahitiwibble on 2012-07-17
This same problem has been driving me crazy.

I have a dual boot W7(64 bit)/Ubuntu 10.04(32 bit) Asus PRO5DIJ. I just installed [the new v4 of Skype for Linux]("http://www.skype.com/intl/en/get-skype/on-your-computer/linux/") and the above solution didn't work for me ......... but [this one did, and perfectly]("http://ubuntuforums.org/showpost.php?p=8925031&postcount=225")!!

---

### Post by venky96 on 2012-08-15
This one here as a perfect step by step guide to fix it.

[http://dealwithubuntu.blogspot.de/2012/07/skype-video-upside-down-solution-here.html]("http://dealwithubuntu.blogspot.de/2012/07/skype-video-upside-down-solution-here.html")

---

### Post by denver on 2013-05-21
I know this is an old thread, but I stumbled across it while searching for the same thing. Actually moving the skype binary is not really recommended. If you ever update the deb you will have to do the same thing all over again. Instead of renaming the file just add a dpkg-divert. That way when you update the deb, dpkg will know where to copy the binary to. You can add a divert like so:

```

dpkg-divert --divert /usr/bin/skype.real --rename /usr/bin/skype

```

And then create a wrapper to preload the video4linux compatibility library.

---

