---
title: "Rescue my installation"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by GrootBrak on 2006-07-30
Man, I buggered up something. The only piece of equipment I cannot get to work is  my scanner. So I chatted on the sane IRC. Ater trying a couple of things, I got advice to install the hotplug package. I was reluctant when I saw it wants to install from my Breezy CD, but I went for it anyway. 

So after I restart, Kubuntu boots normally, then it hangs for uncharacteristically long on "Network configurations" finished booting, then the black screen as usual. Then it throw the Kubuntu logo with the "boot status bar" as if it justs starts booting in stead of the normal logon screen.
CTRL ALT F1 gives me the command line. I tried startx, but get rows and rows of error messages.

I am unable to connect to internet from command line at this stage because I cannot get the rfcomm devices to be reported or working. (Bluetooth modem) 

I have the Kubuntu Dapper live CD and tried to rescue, but I don't have a clue what to do.So now I am waiting for you good folks to save me once again from myself!!!:-& PS. I was unable to find relevant info as to my problem.

---

### Post by GrootBrak on 2006-07-30
Problem solved by me.
from command prompt$ > sudo apt-get remove hotplug
 sudo apt-get install kde --reinstall
The latter failed dismally, but *maybe* something was hooked in right.
Still does not solve my scanner problems any reason why hotplug was dropped and how to get my USB scanner working?

---

