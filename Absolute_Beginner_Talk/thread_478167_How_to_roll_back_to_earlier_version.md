---
title: "How to roll back to earlier version"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by Bazzaah on 2007-06-19
I made the mistake of upgrading to the Skype beta release; I have a problem with my microphone in that it doesn't work. The Sound In device sees my microphone chip but doesn't pick it up.

Skype was perfect under the previous version I had installed, as good as Windows in fact.

I'd love to spend ages sorting the beta out but I don't have the time and need to speak to some people today.

Can someone tell me please how to roll back to the previous version I had installed?

Thanks in advance!

---

### Post by Bazzaah on 2007-06-19
got the Skype beta working by changing device under volume control. 

But the question remains, if anyone knows how to chnage back to an earlier version of any program, thanks.

---

### Post by mjwhitfield on 2007-06-19
why would you want to roll back if it's now working?  I'm planning to install the beta tonight, but if you're having other issues maybe i'll stay away.

---

### Post by Bazzaah on 2007-06-19
Skype's great now as good as Windows again, which is good.

I was thinking more generally with any given application.

Just in case you decide to change and if you are having mike problems, teh solution that worked for me was to double left click on volume control and change device to your mike and increae the volume. I have a Logitech mike which doesn't work elsewhere (which I must sort out) but is fine on Skype.

---

### Post by Golyadkin on 2007-06-19
You cannot really roll back to a previous version, but you can uninstall the current version and reinstall the previous version.

---

### Post by Bazzaah on 2007-06-19
I thought so, guess it all depends where the previous version is and that would always depend on the program.

---

### Post by Golyadkin on 2007-06-19
To install a specific version simply run:
> 
sudo apt-get install <package name>=<version>

for example with subversion-tools:
> 
sudo apt-get install subversion-tools=1.3.2-5~bpo1


---

### Post by Bazzaah on 2007-06-19
excellent thanks, good to know these things,

---

