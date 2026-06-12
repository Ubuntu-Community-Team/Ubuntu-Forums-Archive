---
title: "Running an MSDOS Application"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by PaperPilot on 2006-11-21
I am a new user to ubuntu, but not to Linux who is in the process of changing desktop machines.  The one I am replacing runs a proprietary e-mail application on MSDOS 6.22.  I would like to move the hard disk drive and modem from the old machine to the new one, keeping the application and associated data files intact.

Should I make the new maching duel boot, or would it be better to use one of the Linux programs which can run the MSDOS Application?  I am open to any solution which will keep my past e-mails intact.

Thanks for your help.

---

### Post by IYY on 2006-11-21
DOSbox might do what you're looking for. It's a DOS emulator.

---

### Post by LLRNR on 2006-11-21
DOSBox is a DOS emulator, it's found in the repositories (search for it in Synaptic / Adept) or get it from [here](dosbox.sourceforge.net). There's another way, you could have a virtual machine through VMware to run "pure" DOS. (To learn how to set up a virtual machine, take a look [here](http://ubuntuforums.org/showthread.php?t=183209).)

---

### Post by PaperPilot on 2006-11-21
> **IYY said:**
> DOSbox might do what you're looking for. It's a DOS emulator.

Great.  Is it included with the ubuntu distribution?  If not, can you give me a link to it.

Thanks a lot.

---

### Post by Perfect Storm on 2006-11-21
```
sudo aptitude install dosbox
```

and it's downloaded and installed.

---

### Post by Phototrek1 on 2006-11-22
Dosbox is a great application.  I duel boot my computer with Dos and use Dosbox .65 so this way i have the best of both worlds. If you boot natively  you have the choice to run any dos application or game.  If you use dobox most likely it will work. However some applications may not work and if you want to play protected mode games you might want to play them natively.  I'm not putting Dosbox down i use it everyday it's just some games are better played natively. Plus I don't know how good the communications are with Dosbox.  

If you have Ubuntu 6.06 do a form search for dosbox .65 you can find a link to download a binary ready for drapper. Drapper has .63 which isn't all that great compared to .65

Dosbox has it's own Dos so you don't need to use ms dos. Just copy the over the appliations you want to use.

P.S  Try this first. Install Dosbox and copy you dos drive over to home and call it DOS. Then  run dosbox at the z prompt type ( mount c "/home/paperpilot/DOS" )(Case sensitive) this will mount the dos folder as drive C.  Then you can test it out. If your happy with it then add the mount command to your .conf file and your good to go. You can alway add the 2nd drive for duel boot.

Have fun. 8)

---

