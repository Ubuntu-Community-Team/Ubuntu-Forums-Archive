---
title: "Help Installing FlashPlayer"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by TimMcDuffee on 2007-10-25
I'm trying to install FlashPlayer.  I've done the first part but now I need to complete the ".rpm" and "YUM" parts.  I open Terminal ... do "cd ./Desktop" ... then the Adobe site says to run "#rpm -Uvh <rpm-package-file>".  This does nothing for me.  Is this command to be entered exactly as stated?  Or should I be replacing <rpm-package-file> with something?  The flash-plugin-9.0.48.0-release.i386.rpm file seems to be in my Desktop.  I've tried replacing <rpm-package-file> with the full filename, filename minus .rpm, filename minus i386.rpm ... but nothing works!!!

Thanks in advance for any help on this.

---

### Post by taurus on 2007-10-25
Why don't you download the .bin instead of the .rpm since .rpm is for Fedora/RedHat/SUSE/Mandriva distros.

Otherwise, you need to install alien and use it to convert .rpm to .deb and then install it.

```
sudo apt-get update
sudo apt-get install alien
alien filename.rpm
sudo dpkg -i filename.deb
```

---

### Post by finn on 2007-10-25
The other thing you can do is just use firefox to go to a site that needs flash. There will be a bar below the address bar saying that you need to install a plugin. Click the get the plugin button, enter your password, and bob's your uncle.  My wife managed to do it herself.

---

### Post by TimMcDuffee on 2007-10-25
Hmmm ... I'm a complete newbie with Linux and Ubuntu.  I tried to open a website that informed me that I needed Flash Player installed. I clicked the website's link which took me to the Adobe website.  The screen showed me "Option 1 - .tar.qz", "Option 2 - .rpm", and "Option 3 - YUM".  I was thinking that I had to run each of these ... but since these are Options I'm now guessing that only one way is needed.  I did complete Option 1 successfully.  I try to same website again and it no longer tells me that I need Flash Player installed.  BUT, the website shows "100% Loaded" but nothing happens.  So, I guess I have  it installed but it just ain't working?  This is way out of my level of expertise!

---

### Post by taurus on 2007-10-25
If you only need a flash plugin, it is available from repos.  Use synaptic and Search for it.  Then, don't forget to restart firefox after you've installed it.

---

### Post by TimMcDuffee on 2007-10-25
Sorry ... but I did warn you that I'm a newbie.  I don't know what you mean by "repos" or "synaptic".

---

### Post by Maestro23 on 2007-10-25
> **TimMcDuffee said:**
> Sorry ... but I did warn you that I'm a newbie.  I don't know what you mean by "repos" or "synaptic".

System>>Admin>> Synaptic

Search, mark for install, apply...

---

### Post by ericartman on 2007-10-25
On search in Synaptic I just searched for "flash" and installed the non-free one and it all came together.

Cart

---

