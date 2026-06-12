---
title: "want to be open source"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by dwmoulton on 2007-03-09
I have not yet installed Ubuntu on my XPpro PC but have no desire to go to Vista. I have a few questions about this switch in OS.
If I install Ubuntu:
can I import all of my office doc and settings
can I run photoshop CS2, Image Ready CS2, After Affects 6.5, Illustrator 12.0.128,  Turbo Cad 10 and Floor Plan3D 
will all the spyware adware and Macaffee AV programs I use now still work (or maybe not need)
I am very new to this but have read much about open source and like this concept. If it works as well as Firefox than I shall be happy to tell MS to buzz off. Thank you in advance for any help with this.

---

### Post by nanotube on 2007-03-09
you can read your office documents, but not sure what you mean by "office settings"? the office suite used by ubuntu is openoffice, which can read ms office docs, but is not really the same software, so importing settings for it is not a sensible proposition.

as to running all that software, for the most part, that's probably a "no", although some of them may run with wine (windows compatibility layer). depending on what your usage pattern for those programs is, you may be better off using open source alternatives to that software (e.g. GIMP instead of Photoshop, would be good for all but the most advanced PS features).

spyware, adware, antivirus, generally not needed. firewall comes built in. antivirus is available in the repositories, if you really want it anyway. ;)

the best solution for you, i'd say, based on limited information :), is to run ubuntu/winxp as a dual boot, while you explore, at least you have something functional to come back to if it doesn't work out (or better yet, try it on another spare comp, rather than your main work machine).

---

### Post by seshomaru samma on 2007-03-09
You can import all your office docs easily - you can open them in Open Office (there is a Windows version of Open Office so you can try on your Windows)
You might be able to install some of the programmes you mentioned , but it would be quite difficult. These programmes are written specifically for Windows (or Mac) , you can find some alternatives (like the Gimp ,an alternative for Photoshop, has a Windows version as well) ,but they might not satisfy your needs. 
You don't need a spyware addware etc , for Linux. If you run firefox with the no-script and adblock extentions than you should be ok. The same goes for anti-virus, you don't really need it. You get an excellent built-in firewall as well. 

Basically Linux is not a free version of Windows. It's something completly different . 
It takes a while to get used to ,  but it's worth it.
I suggest you download the Live -Cd , you can experience Linux without changing anything on your computer (though the Live CD is much slower than an actuall installed system) .  If you feel it's for you , you can install it alongside Windows in a dual boot. 

This guide has detailed instructions on how to dual-boot :  [here]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by bot42 on 2007-03-09
Pretty much everything nanotube says here is correct. As for for viruses and security hacks, those almost non-existant in Linux because of the freedoms of opensource which allow very fast debugging, that was how linux ended up running about 80% of all webservers in the world.

If you want to dualboot with XP, take out the XP drive and insert your future ubuntu (or whatever linux distribution you have) drive. Go into BIOS, Go into Boot options and set to boot from cd first. Then insert the live cd and follow the install instructions in the GUI. Once the installation has finished shutdown your pc then put in the XP drive except make sure it is set to slave (The windows bootloader isn't designed for linux, however the bootloader for linux supports both linux and windows). 

Another thing i'll note is that due to freedoms of opensource you can file bug reports or suggest new features to any opensource program. Alternatively if you have advanced programming experience you can download the sourcefiles and compile them yourself but I'd stick to bug reports.

---

