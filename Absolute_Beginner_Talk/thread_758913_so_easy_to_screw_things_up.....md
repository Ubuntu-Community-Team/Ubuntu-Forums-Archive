---
title: "so easy to screw things up...."
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by waggingwabbit on 2008-04-18
how is it so amazingly easy to screw things up on linux? i just edited some things in xorg.conf that have to do with my tablet and now my graphics is screwed up and i have to go on low graphics mode... how does this happen? i touched nothing outside of wacom tablet stuff.....

---

### Post by Tomatz on 2008-04-18
Always backup your xorg.conf before making changes then if you have problems you can just revert to the backup ;)

You live and learn ;)

```
sudo dpkg-reconfigure xserver-xorg
```

That should fix the problem.

---

### Post by HermanAB on 2008-04-18
Ubuntu is not the easiest Linux around, it is intermediate to difficult, so you need to be careful.  If you want something that is more pointy-clicky with wizards for everything and the kitchensync, then you should look at Suse or Mandriva Linux.

BTW, once I have a working system, I make a tar ball of the /etc directory for reference if things go loopy:
$ sudo tar -zcvf etc.tgz /etc

Cheers,

Herman

---

### Post by waggingwabbit on 2008-04-18
well i thought i was being careful. i know i didnt touch anything unrelated to wacom....so if anything screwed up then it should be just my tablet. does typing in sudo dpkg-reconfigure xserver-xorg bring it back to when i first installed ubuntu? cuz i had a hard time figuring out how to get my max screen resolution and refresh rate up and really dont know how i did it the first time....

---

### Post by houstonbofh on 2008-04-18
Nope.  It starts a clean config.  How did you mod the xorg file?  If you used gedit, you have a backup hidden that may save you.

---

### Post by Tomatz on 2008-04-18
> **waggingwabbit said:**
> well i thought i was being careful. i know i didnt touch anything unrelated to wacom....so if anything screwed up then it should be just my tablet. does typing in sudo dpkg-reconfigure xserver-xorg bring it back to when i first installed ubuntu? cuz i had a hard time figuring out how to get my max screen resolution and refresh rate up and really dont know how i did it the first time....

You are able to select monitor resolutions etc when you run the command. It should detect your h/v refresh rates fine (that doesn't mean that it will). ;)

---

### Post by ayenack on 2008-04-18
Quick suggestion for the future so if your xorg gets messed up you can restore it.

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup** (Copies and renames xorg.conf to xorg.conf_backup leaving the original in place, cp stands for copy BTW.)

Then if all goes wrong you can restore the original like this.

**sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf**

Hope it's helpful for the future.

---

### Post by Oldsoldier2003 on 2008-04-18
> **HermanAB said:**
> Ubuntu is not the easiest Linux around, it is intermediate to difficult, so you need to be careful.  If you want something that is more pointy-clicky with wizards for everything and the kitchensync, then you should look at Suse or Mandriva Linux.

BTW, once I have a working system, I make a tar ball of the /etc directory for reference if things go loopy:
$ sudo tar -zcvf etc.tgz /etc

Cheers,

Herman

Tossed you a thanks there Herman, you brought up a tip there that isn't widely given, and one that can be a real lifesaver when things go south... if they had the forsight to do it beforehand of course!

---

### Post by SlappyPappy on 2008-04-18
The backup is so simple and saves a ton of hassle. I found this out installing a new video card. Not a problem. 

Can you even do something like this in Vista? I'm guessing no.:lolflag:

---

### Post by waggingwabbit on 2008-04-18
oh...i didn't run the comman though x.x i remember i did make a backup copy of my xorg doing "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup" so i just copied over xorg with that one. i didn't touch my wacom settings this time though. 

i have another question though, ubuntu sees my graphics card as (nvidia geforce 6800 (generic)). but its really a 6600gt. is it a mistake? can i check if i have the lastest driver somehow? i downloaded a driver "NVIDIA-Linux-x86-169.12-pkg1.run" but it became too complicated for me to install... =/ theres too many things i had to do before it would install and didnt bother with it any longer.

---

### Post by waggingwabbit on 2008-04-18
> **HermanAB said:**
> Ubuntu is not the easiest Linux around, it is intermediate to difficult, so you need to be careful.  If you want something that is more pointy-clicky with wizards for everything and the kitchensync, then you should look at Suse or Mandriva Linux.

BTW, once I have a working system, I make a tar ball of the /etc directory for reference if things go loopy:
$ sudo tar -zcvf etc.tgz /etc

Cheers,

Herman

so....what exactly am i supposed to do with that when i need it? :confused:

---

### Post by Tomatz on 2008-04-18
> **waggingwabbit said:**
> so....what exactly am i supposed to do with that when i need it? :confused:

In future if you have the same problem you can untar (unzip) the **.tar** archive that command will make of your **/etc** directory. Enabling you to restore your original xorg configuration (xorg.conf). Also you will have a backup of the whole **/etc** directory which could come in very handy in times of need ;)

Backing up xorg.conf as **ayenack** suggested would probably be your best bet though.

---

