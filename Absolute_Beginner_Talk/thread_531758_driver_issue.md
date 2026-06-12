---
title: "driver issue"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by shopmanual on 2007-08-21
I tried to install a driver (mrv8335.inf) for my Netgear WG311v3  using the graphic interface in ndiswrapper, I navigated to the .inf file, and then clicked install, and nothing happened, no driver popped up in the window. So I tried to install it using the terminal and when I do it says driver already installed. Then I input "ndiswrapper -l" and the it says invalid driver, or if go ndiswrapper -a (wireless card id) mrv8335  it says that the driver was not installed properly. Is there a way to uninstall it, and then try to install it again, or is there something else I'm missing?

---

### Post by jw5801 on 2007-08-21
Run ```
 sudo ndiswrapper -r mrv8335
``` then navigate to the folder where the .inf file is using cd (the change directory command) and run ```
sudo ndiswrapper -i mrv8335.inf
``` That's the command line way to install a driver. Also check that you have the equivalent .sys file in the folder as well (I'm reasonably sure it uses both). Use "ndiswrapper -l" to check after you're done and report back!

---

### Post by shopmanual on 2007-08-22
Thanks for the help. I did that, removed the driver successfully and then when I do the install it says the driver is already present. So I hit the ndiswrapper -l and it tells me that mrv8335 is an invalid driver. Why does it think it's already installed if I delete it (I know it's gone cuz I bring up the driver list and it's not there).

---

### Post by jw5801 on 2007-08-22
Hmm... it might be a problem with your ndiswrapper install. What is the output of "sudo ndiswrapper -v"? If it gives you something other than the version you think you have installed (or something weird like telling you the version required by the module is '0') then you may want to try reinstalling it.
Make sure you're definitely in the folder containing mrv8335.inf and mrv8335.sys (use the ls command before you run the install). Ndiswrapper isn't very smart, if you try to install a driver that isn't in the folder you're in, it won't return an error it'll just mess up whenever you try to run it as it doesn't actually have anything to work off.

---

### Post by shopmanual on 2007-08-23
Thanks a lot for the help. When I checked the version, it said that there was no version. I just reinstalled ndiswrapper and it all worked fine.

---

