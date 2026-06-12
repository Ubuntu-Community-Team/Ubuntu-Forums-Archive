---
title: "Kubuntu Boots Into Unsupported Resolution"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by walesmd on 2007-04-30
I've decided to give Ubuntu another shot after Windows died on me - again. I don't have any pressing development projects to work on at the moment (the reason I went back to Windows previously), so I have plenty of time to dedicate to the OS.

Last night I popped in my Ubuntu 6.06 ShipIt CD (didn't feel like waiting to download Feisty), installed it, updated to Fiesty, and then decided to give Kubuntu a go. A quick 'sudo apt-get kubuntu-desktop' took care of that and I was good to go.

Unfortunately, I have a minor annoyance:

When Kubuntu boots everything is fine, I get the login screen and login, but as it loads my desktop it switches into a display mode my monitor does not support. I get a 30 second to 1 minutes error from my monitor and then it finally switches over to a mode that is supported. Why is this and how can it be eliminated?

Note: Not at my computer at the moment, so I can't check if the error message tells me what resolution/frequency the OS is trying to push out to the screen.

---

### Post by mejy on 2007-04-30
Run 'sudo dpkg-reconfigure xserver-xorg -phigh' in the terminal and select the correct resolutions.  Not sure why it's switching to the correct one after a while, but that should fix it.  If that doesn't work, you should probably just do a fresh kubuntu install, since you seem to have followed a pretty odd upgrade path.

---

