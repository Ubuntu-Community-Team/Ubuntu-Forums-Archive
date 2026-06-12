---
title: "Synaptic Package Manager problem!"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by smartsaah on 2007-06-21
Hello,

I guess I am in serious trouble! I tried to install Second Life  ( a game) deb package from getdeb.com and I was doing that perfectly! It was actually downloading the stuff! But meanwhile I had to leave my place and therefore I canceled the  downloading of that file (secondlife-install_1.17.0.12-1~getdeb1_i386.deb) . After this, even beofre shut down, I noticed that Synaptic is not working at all! It is displaying an error message **An error occcured.** and in the details section it is saying[B]E: The package secondlife-install needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/B]

Moreover I can see the update icon on the top right flashing. When I am hovering the mouse over it is displaying a balloon with the details of the error and asking to run the Package Manager with the right click menu with or apt-get in a terminal to see whats wrong!

Being a newbie in Linux and Ubuntu, I can't comprehend whats wrong and how to correct it.

Previously I had successfully updated the Ubuntu and downloaded various packages through the Manager.

Please help me out and tell me if there is a way to reinstall the Package Manager itself! Thanking you all in advance....:(

---

### Post by taurus on 2007-06-21
Try

Applications -> Accessories -> Terminal
```
sudo dpkg --config -a
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by deadlikeoscar on 2007-06-21
Yeah that usually happens when something doesn't install correctly. Usually you can just open Synaptic and search for the package and uninstall it. Sometimes you need to take a more aggressive approach and go into the terminal to fix it (as per the above post.)

---

### Post by smartsaah on 2007-06-21
After following your suggestion this is what I got it the Terminal:

[B]E: I wasn't able to locate a file for the secondlife-install package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?
[/B]

Please tell me what to do next?

---

### Post by smartsaah on 2007-06-22
Anywayz thanks guys...I just used dpkg -i command in the terminal to reinstall the second life...and everything is working fine thereafter!

---

