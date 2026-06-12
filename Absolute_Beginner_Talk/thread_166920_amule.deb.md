---
title: "amule.deb"
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by Biltong (Dee) on 2006-04-27
Hi Guys

Being very new at this Ubuntu "thing" I am having a great time (albeit a very frustrating one at times...)
I still don't know what the hell to do with a tar.gz, (but I'm sure somebody will help me out...), so when amule screamed at me that it needed updating I hadn't a clue, despite downloading the aforementioned tarball to the desktop.
In frustration I 'Googled' **amule-2.1.0_i386.deb** and came up with the following website: [http://blog.natostanco.it/index.php?/pages/ubuntudeb.html](http://blog.natostanco.it/index.php?/pages/ubuntudeb.html).
This clever Italian has created a .deb version and thus prevented me from tearing anymore hair out!
Remember newbies, download the .deb file to the desktop. In the terminal type:
cd Desktop (and hit enter on the keyboard) then type
sudo dpkg -i amule-2.1.0_i386.deb (press enter again)
That's it.
Enjoy!

Dee the dumb blonde

---

### Post by jazzmuzik on 2006-04-27
It's best to update only through Ubuntu's 'apt-get update' or Synaptic 'Reload' options unless you really know what you are doing.

So if some program (amule) has an update available but there is no .deb package file yet, I think it's best to wait for the Ubuntu package to be released.

If you update system files with a tar.gz, things can get screwed up fast. I'm not saying it's not possible, but you have to know what you're doing, and even then there can be consequences.

One way around this is to install programs to your user directory rather than as root in the main system. For example, I installed Firefox in my user directory and recently got a message that the program had automatically updated me to version 1.5.0.2. This was possible because the program was installed to my own user directory.

---

