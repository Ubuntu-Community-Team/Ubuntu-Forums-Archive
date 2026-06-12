---
title: "Downloading updates with dial-up -- is there a better way?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by lee292 on 2007-04-10
I've been using Edgy for a couple of months now on my laptop and I'm enjoying the experience.
You've got me hooked and I'd like to install Edgy on my desktop at home.  The only problem is that dial-up is the only way to connect to the Internet from my home, and it's going to take forever for all the updates to download and install.  Is there a way I can use my broadband connection at work to download the updates I need to a CD or a memory stick, and then install them on my home computer?

I'm not fluent in the Linux command line, but I envision something like a script that copies a list of the available updates on the home computer to a text file on, for example, a memory stick and then a second script that would be invoked when my laptop is plugged into the broadband connection that would read the needed filenames from the text file and download them to the memory stick.  Back home, a third script would copy and install the updates from the memory stick.  Could this be done?

---

### Post by mac.ryan on 2007-04-10
From a system that you have just updated, you could copy on a CD the content of: /var/cache/apt/archives

Alternatvely you might try to use [aptoncd]("http://aptoncd.sourceforge.net/") (apt-on-cd).

You should then probably proceed manually to install the packages with "aptitude" or "apt-get", as chances are your "update manager" would ignore the content of that CD.... (but I never tried myself, so...)

---

### Post by lee292 on 2007-04-10
> **mac.ryan said:**
> From a system that you have just updated, you could copy on a CD the content of: /var/cache/apt/archives

Alternatvely you might try to use [aptoncd]("http://aptoncd.sourceforge.net/") (apt-on-cd).

You should then probably proceed manually to install the packages with "aptitude" or "apt-get", as chances are your "update manager" would ignore the content of that CD.... (but I never tried myself, so...)

Thank you!  Once I get Edgy installed on my home computer, I'll try your suggestions.  I especially like apt-on-cd. :)

---

### Post by john_spiral on 2007-04-11
**apt-on-cd** looks like really good news for Ubuntu/Debian users on dial-up.

i.e most of the 3rd world.

---

### Post by lee292 on 2007-04-11
> **john_spiral said:**
> **apt-on-cd** looks like really good news for Ubuntu/Debian users on dial-up.

i.e most of the 3rd world.

The bad thing is that I'm in the eastern U.S.! :(  I live too far away from a "switch" to get DSL, the cable company says there aren't enough potential subscribers to give me cable even though it's only a mile from my house, and I'm too far away from a wi-fi node.  I could get a satellite internet system, but right now it's a bit too pricey for my budget.  Hmmm... I could have my phone disconnected and cancel my satellite TV subscription...

---

### Post by LaurelLynn on 2007-04-11
Dear lee292,

I have read of homebrew built antennas etending the wifi range to as much as 20 miles (might violate FCC regs though, not friendly people).

5 or 6 is actually a more practical number though.

A Google of ¨wifi antenna¨ turns up several sites, here is one:

[http://www.turnpoint.net/wireless/has.html](http://www.turnpoint.net/wireless/has.html)

Yes, you can boost wifi with a Pringles can!

It one option to consider.

---

### Post by D10 on 2007-04-11
Dial up is also my only available option for internet connectivity at home too. What I do is use synaptic to just download the list of packages needed, and take that to work with me.

I installed Unix tools for Windows [http://unxutils.sourceforge.net/]("http://unxutils.sourceforge.net/") on my Work PC and use wget to download all the debs to my thumb drive, and then add them back to synaptic on my home PC.

Works out pretty well

D10

---

