---
title: "Installer Files? Where do they go?"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by sibot on 2007-05-31
Hey all,
Today is my first day on ubuntu! And I'M LOVING IT!  :D Its superb, I can't imagine theres something so powerful out there! Well its amazing! anyway, i wanted to ask where do the installer files go? All the softwares i'm downloading from the application manager et al? Is it possible to save their installers, so i can use it next time i format? cause i have very slow internet speeds, around 128kbps, its not possible for me to download again n again. If anybody has any clue, please do let me know.
thanks
sibot

---

### Post by xela321 on 2007-05-31
Glad you like Ubuntu as much as the rest of us!

The installers you download through the package manager are stored at: /var/cache/apt/archives.  They are stored there to prevent having to download repeat copies of what you already have.  The cache is intelligently maintained so that you a) don't have to continually download the same packages and b) your hard drive doesn't fill up with a bunch of deprecated packages.

Hope that helps!

---

### Post by sibot on 2007-05-31
Hmmm awesome! AMAZING :D I am never going back to windows!

---

### Post by sibot on 2007-05-31
Been trying to install amarok for the last 1 hr, i dont know what 36 files it has been downloading =(

---

