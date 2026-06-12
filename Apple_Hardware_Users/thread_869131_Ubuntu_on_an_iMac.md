---
title: "Ubuntu on an iMac"
date: 2008-07-24
forum: Apple Hardware Users
---

### Post by jarhead14 on 2008-07-24
So I installed Ubuntu 5.10 (Breezy Badger) on my old iMac (a blue 500mhz upgraded to 640mb ram) and it ran painfully slow freezing and not letting me move the mouse.  I couldnt even open firefox.  I thought maybe it was the version so i downloaded a much newer 6.06 version and installed it.  Still the same exact thing happens.  Just slow as hell.  Anyone know what I can do??? I installed 5.10 successfully on my old G4 Titanium a while ago...

---

### Post by cyberdork33 on 2008-07-24
There are newer releases still:
[http://cdimage.ubuntu.com/ports/releases/](http://cdimage.ubuntu.com/ports/releases/)

---

### Post by Vakman on 2008-07-24
How come you pick older versions of Ubuntu. The latest stable release is Ubuntu 8.04 Hardy Heron.

---

### Post by jarhead14 on 2008-07-24
might a newer version (8.04?) work?

---

### Post by Vakman on 2008-07-24
Well I don't see why you should use an old version either way. Try the new version and then if there is still the same issues, come back here and tell us.

---

### Post by cyberdork33 on 2008-07-24
> **jarhead14 said:**
> might a newer version (8.04?) work?
I would make sure to use 7.10 at least.

---

### Post by Vakman on 2008-07-24
> **cyberdork33 said:**
> I would make sure to use 7.10 at least.
I agree Ubuntu 8.04 may not be best if you have an ATI card or something like that.

---

### Post by Nosferax on 2008-07-24
ATI released a new version of their drivers supporting 8.04 

[http://www2.ati.com/drivers/linux/catalyst_87_linux.html]("http://www2.ati.com/drivers/linux/catalyst_87_linux.html")

---

### Post by oswaldkelso on 2008-07-24
> **Nosferax said:**
> ATI released a new version of their drivers supporting 8.04 

[http://www2.ati.com/drivers/linux/catalyst_87_linux.html]("http://www2.ati.com/drivers/linux/catalyst_87_linux.html")

We ppc users can enjoy the fact that there are no horrible bits of ati propriatory drivers to do who knows what on our wonderful machines. 

[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

That machine whilst not a speed demon should not be slow. I would imagine some graphic settings need tweeking. I've just installed etch on a 333mhz 256mb and it runs well for its spec.

---

### Post by stream303 on 2008-07-25
First thing I'd do is to copy, print, or write down your /etc/X11/xorg.conf file, and also your /etc/yaboot.conf file to some other media -- in case you think of trying out Hardy 8.04.

I took a look on everymac.com, and see that your card supports 2X agp.  Be sure to see this faq in regards to some tweaks you can apply to your xorg.conf file:

[https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec](https://wiki.ubuntu.com/PowerPCFAQ#head-ffefeb40b6b03a892fdebfa6e6f633929024f1ec)

Also, do you have anything other than the mouse / keyboard attached?  Are you using a modern mouse, or the older oem one-button unit?  No problems here with a 3-button optical usb.

Do you truly have 640mb memory - even though you may have installed new memory, can you verify it with

```
free -m
```
and looking in the Total column?

I'm assuming that the apps / mouse movement is slow, and also not something else like poor dns resolution times, which is a networking issue, but is easily fixed.

While I don't want to push you into any specific release, if you do feel like running something newer, you can find them here:

[https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

---

### Post by jarhead14 on 2008-07-28
I downloaded 8.04 and installed it.  Now the iMac won't even boot up.  It runs a bunch of processes then it looks as if the monitor turns off or something (since the power light fades in and out).  Im thinking my computer's graphic card can't handle it? I'm pretty sure its a ATI RAGE Ultra 128 card but im not certain.  Should I go with an older version of ubuntu or can I edit something to try and get it to boot???

---

### Post by stream303 on 2008-07-28
You will have to edit your /etc/X11/xorg.conf file, and possibly /etc/yaboot.conf.

You could try using an older version, like Feisty 7.04 just to see what it writes to those files so you can include them yourself in Hardy - but in many cases you'll need to go in and do the dirty work yourself, since the apple hardware doesn't always give back the right values to the Linux probing utilities.

Be sure to have these two faqs handy, and also your machine specs - which machine is it exactly (everymac.com can help), how much ram does it have, does it have any non-oem replacements inside etc:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)
and
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

---

### Post by jarhead14 on 2008-07-28
Alright so in those instructions it says to wait until booting is complete to then do ctrl-option-F1 and that should bring up the command prompt.  This does not seem to be working for me.  Should I not wait until im at the blank screen to do this?  If you couldn't already tell im a real linux newbie...

Also my computer is this:

[http://www.everymac.com/systems/apple/imac/stats/imac_500_indigo.html]("http://www.everymac.com/systems/apple/imac/stats/imac_500_indigo.html")

Blue 500mhz G3
128 MB ram factory with added 512 for total of 640

---

