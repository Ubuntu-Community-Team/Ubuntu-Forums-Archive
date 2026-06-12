---
title: "Windows Drivers and ndisk"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by manosdvd on 2008-04-18
I'm new to Ubuntu and it took me a long time to figure out how to get my Linksys wireless card working. All the advice I was seeing was compiling it on the command line, invariably leaving out some key piece of knowledge that a complete and utter newbie like me wouldn't know (in that case it was how to change folder in the command line... I know how now). Then as a last resort I used the built in help function in Ubuntu and who knew... It lead me to ndisk and three clicks later my problem was solved. I highly recommend this method for anyone having trouble with wireless cards with only Windows drivers. 

My problem however is that every time I reboot the computer, I have to go into the Windows Wireless Drivers panel, uninstall my driver, and reinstall the same driver in order to get Ubuntu to even recognize a wireless card is even attached. It works fine and connects as soon as I do so, but it's an extra hassle every time I start up the OS. Even more pressing is the fact that when trying out the boot disk of Hardy (beta), the ndisk upgrade doesn't want to let me uninstall my driver at all... 

So basically I'm looking for some solution to keep me from having to reinstall the drivers every time I start up the OS. I'd appreciate any help (and remember, I'm a pure and complete noob so I need you to speak to me like a windows user...)

EDIT: I mean _ndisgtk_... sorry for any confusion.

---

### Post by spiderbatdad on 2008-04-18
I believe this will help. After setting up the driver run the command: 
```
sudo update-initramfs -u
```

---

### Post by manosdvd on 2008-04-18
Alrighty... done and done. I'll reboot now to see if it worked. Meanwhile, what exactly did I just do?

---

### Post by spiderbatdad on 2008-04-18
[http://www.linuxdevices.com/articles/AT4017834659.html](http://www.linuxdevices.com/articles/AT4017834659.html)

---

### Post by manosdvd on 2008-04-18
Okay, didn't seem to work. No error messages, just came back to the same old issue. I do appreciate the help though. Any other ideas?

---

### Post by spiderbatdad on 2008-04-18
Hmmm. I've seen this issue a number of times. not sure I've seen a fix.
How about (with the card configured) System>>Preferences>>Sessions>>Session Options...click the disk image: "Remember currently running applications...not expecting much, but maybe.

---

### Post by manosdvd on 2008-04-18
And negatory... but at least I was able to get pidgin to start on startup which I'd been trying to do so not a complete loss.

---

### Post by spiderbatdad on 2008-04-18
Check the file /etc/modules for the line ndiswrapper.
If it is not there, add it on a line by itself...can be at the end of the file.

---

### Post by manosdvd on 2008-04-18
WINNER! You are a god among men sir! It was not in the file so I added it (had to open it as root to save the file, but anything that can be done with a right click is okay with me) and upon reboot it connected instantly (faster than windows I might point out), Pidgin fired into action, and all was right with the world. Thank you so much.

---

