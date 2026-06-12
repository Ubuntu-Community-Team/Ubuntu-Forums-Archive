---
title: "How do I get Real Player to work?"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by adarsh on 2005-12-02
Hi.. my problem is that after installing RealPlayer10GOLD.bin successfully on a Ubuntu machine, i am not able to run the program. I have installed it into a subdirectory within the home file. I know it must be simple, but how do I run the program.

---

### Post by invalid on 2005-12-02
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)

---

### Post by bfonseca on 2005-12-02
[QUOTE=adarsh]Hi.. my problem is that after installing RealPlayer10GOLD.bin successfully on a Ubuntu machine, i am not able to run the program. I have installed it into a subdirectory within the home file. I know it must be simple, but how do I run the program.[/QUOTE]

Hi, I think that all you would have to do is ./RealPaly... or if there is an realplayer...sh then sh ./real...sh

I think that might work...Or you may wanna go to the folder where you installed it and look for the the real...sh or just realplay and click on and run (when prompt comes up)

I hope this helps and if not sorry... One of those usually works for me.
Brian

---

### Post by adarsh on 2005-12-02
Hi. i think i understand but what is the extension of executable files?
Thanks

---

### Post by invalid on 2005-12-02
[QUOTE=adarsh]Hi. i think i understand but what is the extension of executable files?
Thanks[/QUOTE]

>

[QUOTE=Invalid][http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies)[/QUOTE]

---

### Post by AndyCooll on 2005-12-02
There are two ways to get Realplayer.

1. Use Synaptic or apt-get install realpayer. That loads version 8 IIRC.

2. As you have done download the bin file from the website. On the website download page itself there are some instructions on the procedures you need to take to install: [http://www.real.com/moreinfo/playerplus_install.html?system=linux&pageid=linuxPage&pageregion=install_instructions&src=freeplayer_partner%2Clinux&pcode=rn&opage=linux',%20'install_instructions',%20'570','400','');]("http://www.real.com/moreinfo/playerplus_install.html?system=linux&pageid=linuxPage&pageregion=install_instructions&src=freeplayer_partner%2Clinux&pcode=rn&opage=linux',%20'install_instructions',%20'570','400','');")

I've copied them for you here:
Installation Instructions
- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

:cool:

---

### Post by confused on 2005-12-07
After having done all this Realplayer 10 doesnot work for me? Anyone with new suggestions plz

---

### Post by skeezer65134 on 2005-12-08
I've asked before with no help, so I thought I'd ask here....

I too have installed Realplay with no luck. The program opens and seems to run fine, but when I try to play back .rm files with, it gives me the error "This player does no have the capabilities to play back this content". clicking "Details..." gives me the following info:
```
The following components are required:
application/x-pn-imagemap

URL:
file:///home/user/file.rm
```

I immagine I'm missing a package somewhere, but I have no idea what. I have installed both by the binary from the Real website and from a third party repository with no success.

The Helix player tells me it can't find x-pn-realaudio or something along those lines, so it's no better.

BTW, running the Real updated says I have the latest version. I also tried getting the RPM version, renaming it to 'rp8_linux20_libc6_i386_cs2_rpm' and running the realplay install from apt-get, but as you may have guessed, the install fails.

Any thoughts?

---

