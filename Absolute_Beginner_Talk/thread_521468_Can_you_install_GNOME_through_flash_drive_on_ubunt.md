---
title: "Can you install GNOME through flash drive on ubuntu server?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by uberhaxor??? on 2007-08-09
Hi, can you install the GNOME desktop environment through a flash drive on ubuntu server?

---

### Post by Dr Small on 2007-08-09
Why don't you just run:
> sudo apt-get install ubuntu-desktop

Dr Small

---

### Post by Rocket2DMn on 2007-08-09
In Dr Small's case, you need to enable the universe repositories by editing /etc/apt/sources.list.

If the computer isn't connected to the internet you can download the ubuntu-desktop deb file to a flash drive from another computer and run it from the flash drive on the server.  
However, there are other dependencies (like gdm) that might need to be fetched as well, but I can't seem to find any site telling me exactly what the dependencies are.  Try just ubuntu-desktop and if it tells you about other dependencies, we can get those separately.
[http://packages.ubuntu.com/feisty/metapackages/ubuntu-desktop.html](http://packages.ubuntu.com/feisty/metapackages/ubuntu-desktop.html) - click in i386 at the bottom if that is your computer architecture (it probably is), and you can download the deb file to put on the flash drive.

---

### Post by uberhaxor??? on 2007-08-09
Thank you very much. What's the command to run from flash drive?

---

### Post by Rocket2DMn on 2007-08-09
After you mount the flash drive (might be done automatically), change directory to it and run
```
sudo dpkg -i *filenamehere.deb*
```

---

### Post by uberhaxor??? on 2007-08-09
It says error processing the file. How do i mount the drive or whatever? Please give me a full, step by step instruction. 

Thanks

---

### Post by Rocket2DMn on 2007-08-09
Maybe you should have a read here: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

It seems to me like you're in a little bit over your head right now (not that this is necessarily bad).  Why have you installed Ubuntu server exactly?  You might have more luck and less frustration if you used the Desktop edition - you will still be able to perform server functions if you wish, and having the GUI would make life easier.  Then you can ease into learning the command line while still being productive.

If you have errors, please be as detailed as possible and copy/paste the command given and errors output if at all possible.

---

### Post by Dr Small on 2007-08-09
> **Rocket2DMn said:**
> Maybe you should have a read here: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

It seems to me like you're in a little bit over your head right now (not that this is necessarily bad).  Why have you installed Ubuntu server exactly?  You might have more luck and less frustration if you used the Desktop edition - you will still be able to perform server functions if you wish, and having the GUI would make life easier.  Then you can ease into learning the command line while still being productive.

If you have errors, please be as detailed as possible and copy/paste the command given and errors output if at all possible.
Yeah, because I installed Ubuntu, and then went to apache friends and downloaded XAMPP for my box, and now I use it as a server with GUI, and it's easier to learn that way, instead of not knowing all of the commands at first.

Dr Small

---

### Post by uberhaxor??? on 2007-08-09
I chose server edition because i am a web developer and would like to start in-house hosting. This would be the more economically viable option for me. 

I thought that it would have a GUI but it didn't. It also suited me because it didn't use so much bandwidth to download (bandwidth is very expensive in South Africa). So i bought a cheap old PIII box and it's all good. I have to wait a long time for my requested CD.

---

### Post by Rocket2DMn on 2007-08-09
Hrmm, well it might be a few hundred MB just to download all the GUI stuff anyway.  It might be in your best interest to put in a request for a desktop cd in that case.  However, I'm not here to make decisions for you, just offer suggestions.  
You should be able to achieve what you want without the use of a GUI, the CLI is a very powerful tool.  If you want go to straight command line and have specific questions about getting certain aspects of your hosting project setup, start a new thread for each question and people with expertise in each area can help you out.

---

### Post by uberhaxor??? on 2007-08-09
Thanks very much. I think i'll just install DSL, then when i get the Desktop Edition of Ubuntu, i'll install that one. Once again, thanks a lot!

---

### Post by Rocket2DMn on 2007-08-09
No problem.  If you want, you can setup a dual boot between DSL and Ubuntu.  How much RAM does that computer have anyway?  If it's less than 256, Ubuntu probably won't work too well.  DSL or Puppy Linux may be a better option.

---

### Post by uberhaxor??? on 2007-08-09
Well its got 128 RAM i think. I don't think i'll set up a dual-boot

---

### Post by Rocket2DMn on 2007-08-09
Yeah, I'd say use Puppy Linux or DSL, they will be better suited for your hardware.  Good luck.

---

### Post by uberhaxor??? on 2007-08-09
sorry, how do i run dsl from within ubuntu?

---

### Post by Rocket2DMn on 2007-08-09
Hold up, are you referring to DSL = digitial subscriber line, or DSL = damn small linux?

---

### Post by uberhaxor??? on 2007-08-09
My bad, Damn small linux.

---

### Post by Rocket2DMn on 2007-08-09
OK just checking.  You can't really run it "in" Ubuntu without setting a VMware server, and I don't think you can use a VM from terminal.  Do you just want to install it over your Ubuntu server?

---

### Post by uberhaxor??? on 2007-08-09
Yes, i would like to install it over ubuntu server.

---

### Post by Rocket2DMn on 2007-08-09
I've never installed DSL before, but if you have a CD for it, you should just be able to pop it into the CD drive, reboot the computer, and boot from the CD-drive (you may have to set your BIOS to have the CD drive above the HDD).

---

### Post by uberhaxor??? on 2007-08-09
Yes, I'll just do that. Thanks very much for the tremendous help. Thanks!

---

