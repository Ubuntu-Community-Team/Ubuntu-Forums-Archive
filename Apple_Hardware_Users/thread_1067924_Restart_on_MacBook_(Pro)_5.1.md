---
title: "Restart on MacBook (Pro) 5.1"
date: 2009-02-12
forum: Apple Hardware Users
---

### Post by ercoppa on 2009-02-12
Anybody with MacBook (Pro) 5.1, can correctly restart the notebook? Some good news with other kernel version (>=2.6.28 )?

Some suggestions (some option to the kernel)?

[QUOTE=wiki on the restart issue]
Rebooting doesn't work. The computer stops just before reboot with the screen blank, but still active. Occasionally the screen is blank and also the internal speakers give out three or four short signals. 
[/QUOTE]

Greets, ercoppa.

---

### Post by khelben1979 on 2009-02-12
Have you tried with an older version of Ubuntu? (Ubuntu Hardy for instance)

Other than that: you can try with other distributions as well. [Here's a list for you]("http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions").

---

### Post by P@nk on 2009-02-15
I have the same problem on my macbook 5,1 (not pro). I tried pretty much everything.. First with debian lenny, and now intrepid, tried the new kernel 2.6.28, the reboot=b and acpi reboot options, shutting down the network interfaces in alsa-utils, there was also some suggestions about cpufreq and cpu scaling, that didnt work neither.. NOTHING WORKS.. Please help..

---

### Post by JMey94 on 2009-02-16
i figured it out.
i have a 5.1 MB (Aluminium)
go to the terminal and type
sudo shutdown -h now
this wont do the beeps and it shut downs properly...theres also 
sudo shutdown -r now
 for restart but that does the blasts of error when shuting down sometimes

---

### Post by della on 2009-02-17
Are you using nvidia-glx-180? Since I installed it from intrepid-updates I'm not experiencing that problem anymore. My kernel is 2.6.27-12-generic fox x86_64.

---

### Post by P@nk on 2009-02-20
I originally had the 32-bit version.. I did install amd64 kernel and the nvidia glx-180 drivers but same problem :( hangs at reboot.. maybe I should get the specific kernel version you mentioned? I guess it's an upgrade which has yet to be offcially released right?

---

### Post by kevpatts on 2009-04-16
This problem still exists. Is there any solution for it yet?

---

### Post by inphektion on 2009-04-16
Nope.

---

### Post by cyberdork33 on 2009-04-17
there was some activity on the bug report today:
[https://bugs.launchpad.net/bugs/338083](https://bugs.launchpad.net/bugs/338083)

You should test.

---

### Post by inphektion on 2009-04-17
I'm P. Dunbar, and I tested that mainline kernel today and it didn't help but again had a bunch of nvidia issues (since I switch kernel out from under it) I should try generic vga driver on that kernel i guess.

---

### Post by cyberdork33 on 2009-04-17
> **inphektion said:**
> I'm P. Dunbar, and I tested that mainline kernel today and it didn't help but again had a bunch of nvidia issues (since I switch kernel out from under it) I should try generic vga driver on that kernel i guess.
the nvidia 180 is causing suspend issues too, so it might work if you revert to 177.

---

### Post by inphektion on 2009-04-17
funny i just loaded a beta 185.19 version [[ftp://download.nvidia.com/XFree86/Linux-x86_64/185.19/]](ftp://download.nvidia.com/XFree86/Linux-x86_64/185.19/]) to see if it worked better with the apple cinema display (it doesn't [http://www.nvnews.net/vbulletin/attachment.php?attachmentid=36310&d=1238628437](http://www.nvnews.net/vbulletin/attachment.php?attachmentid=36310&d=1238628437)).

Guess i can try 177...

---

### Post by hajk on 2009-04-19
I also experienced this problem on my new 2.0GHz Mac Mini, first running Jaunty (with 2.6.28 kernel) and now also when running Debian Sid (with 2.6.29 kernel). Further, rEFIt 0.12 could not reboot either, but the latest 0.13 version can (perhaps because I left a message on this issue at the rEFIt mailing list). Just a matter of getting that bug report sent upstream, it would appear.

---

### Post by garand555 on 2009-09-11
A bit of an old thread, but I did find a solution.  Note that I am using Arch Linux with kernel 2.6.30, so it may or may not work on Ubuntu.  If you are using grub, go to the grub config file and at the end of the kernel line add this:

reboot=pci

That's it.

I am curious to see if this bug is totally fixed with 2.6.31, which should make it out of the Arch testing repositories fairly soon.

---

### Post by acobster on 2010-09-20
I'm having a similar problem on my dual-boot MacBook. When I restart, it gets to the first restart screen (before it even actually restarts) and just hangs there forever.

I'm running 10.04 with rEFIt. Can anyone point me in the right direction?

Thanks.

---

### Post by psignosis on 2013-01-03
Old thread but I didn't see a definitive solution here - is restart just broken? I've got 12.10 on a MacBook 1,1 and restart shuts down but hangs on start up.

Shutdown works fine. I am not dual booting and this is a brand new install. I did not install rEFIt before installing Ubuntu and made the blinking question mark/folder go away by blessing the linux partition while booted to a OS X install disc.

---

