---
title: "Second Life install problem"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by arochester on 2007-06-22
I  tried to install Second Life but for some reason I couldn't. Now I can't use Synaptic, KPackage or Adept. I have tried apt-get remove Second Life without success. I get the error message "The package secondlife-install needs to be reinstalled, but I can't find an archive for it." How do I get around this?

---

### Post by jrib on 2007-06-27
How did you try installing secondlife?  Was it a .deb?
You should do 'sudo dpkg -i /path/to/secondlife.deb' in a terminal if you want to give APT one more chance.  Usually what happens is, it asks a question but you don't run it in the terminal so the install never completes.

If you just want to get rid of it, run 'sudo dpkg --purge --force-remove-reinstreq PACKAGE_NAME'

---

