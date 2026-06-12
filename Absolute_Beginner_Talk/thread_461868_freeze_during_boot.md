---
title: "freeze during boot"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by enfantterrible on 2007-06-02
Hello all,

when i start ubuntu 7.04 from the live CD everything works fine: it recognizes my internet, videocard, sound...

i then tried to install it.defrag (2x), partitioned (40gb xp, 35 gb ubuntu ext3, 2gb swap, 320gb fat32 datadisc) and installed, everything seemed to go fine.

when i restart i get to the bootmanager and chose ubuntu. it will load the splash screen and then stay there forever (literally). if i choose "recovery mode" it loads a command line but i think it's wrong (Sorry new to linux, but have seen people use the terminal before and it wont do anything whatever i type).

so i am sorry i can't help more, but i dont get any error messages or whatever... maybe it's a known bug. funny thing is that from the livecd everything is smooth so i dont think it's a hardware compatibility issue.

winxp works fine.

thx to anybody who can help !
r

---

### Post by jiminycricket on 2007-06-02
can you try pressing 'e' at the GRUB boot menu and add the kernel option, "acpi=off noacpi"?

---

### Post by enfantterrible on 2007-06-02
hi there... i tried but with no luck: spashscreen and then stop.
i dont understand what acpi=off disables, but anyway it is not doing it for me.

so i guess it is not a known issue? anybody with a frozen splashscreen ?

---

### Post by blue_shift on 2007-06-02
I had this when I upgraded to feisty because of driver issues - my old config file was still in place relying on a driver which didn't exist. What graphics hardware are you running?

Perhaps worth making a note of the contents of /etc/X11/xorg.conf and posting it if you can get to it somehow?

Did you boot from the liveCD in graphics compatibility mode or something?

---

### Post by enfantterrible on 2007-06-02
not really sure how i started the live cd.. i just selected the first option in the bootlist (startup ubuntu and install or something similar)

i have an old (4 years) Nvidia GeForce 4 but i dont guess that's the problem: when i was in the livecd it got recognized immediately and driver were installed (of course though it's pointless cause it requires a reboot and with the livecd is a brand new os every time)

fact is i dont think the issue is x: really the computer hangs the very first second of the ubuntu splashscreen (the orange bar appears and stays there in the very first row on the left, and everything is dead)

i wouldn't even know how to post a file, cause either i boot in xp or i dont boot :)

r

---

### Post by blue_shift on 2007-06-02
But the command line doesn't work at all either? That's odd. I'm at the limit of my knowledge here, perhaps someone else can suggest some grub parameters or something, but all I can think now is a fresh install incase something was installed incorrectly / corrupted etc.

---

### Post by enfantterrible on 2007-06-02
i wouldnt know about the command line: even if i got there (how?) not sure how i would read/edit any file!

if nothing else is possible, i will try re-installing... but i am pretty sure i didn't select anything wrong (partitioning went fine, the rest is just keyboard/timezone changing) and i would be pretty disappointed if the installation was corrupted, i thought that was a stable version!

and if i reinstall (not really ideal situation) and nothing changes? shall i forget about ubuntu forever?

---

### Post by blue_shift on 2007-06-02
All I can say is I've had bad CDs before, which caused fracturing during unstall.

The command line... if you choose "safe mode" at GRUB you should get a text-only boot up and then:
```
root@your-pc-name:~#
```

---

### Post by enfantterrible on 2007-06-02
i will give it a try now and if it doesn't work i'll try re-installing. (even if i am kinda sure reinstall is going to give me the same exact results)

thanks for help, i'll keep you posted.

(sigh, i was so excited about ubuntu, apparently ubuntu isn't that excited about me!)

---

### Post by enfantterrible on 2007-06-02
ok, no luck with that option: if i chose recovery mode i am in some kind of dumb screen, where whatever i type has no effect (like a text editor).

anyway here i am on the livecd... what should i do? re-install or can i get from here some logfiles/configfiles so that somebody can help me having a look at it?

---

### Post by blue_shift on 2007-06-02
Hold up a moment, what does it say in text-only mode? Is there any text on the screen at all?

When you're booting in recovery mode, are there any errors printed during the boot sequence?

---

### Post by enfantterrible on 2007-06-02
it doesn't really say that much: it's too fast scrolling for me to read it, and when i get to the command line (which actually is just a cursor,, it does not interpret any command) the only three lines i can read only deal with something about succesfully recognizing the usb mouse.

---

### Post by blue_shift on 2007-06-02
Very odd indeed. Like I say, unless you can give any commands at the command line (I assume you're tried?), I can't really help you further except to suggest a fresh install could clear the problem.

---

### Post by enfantterrible on 2007-06-03
apparently re-installing did the trick!!!
thanks for help, now i got my videocard recognized, 1440x900 resolution with not so many issues, mp3s.... only one more little problem, but i guess it's about time to start learning how to use linux!

thanks for all the support!

---

### Post by blue_shift on 2007-06-03
No problem, good to hear you're all set.

---

### Post by enfantterrible on 2007-06-04
only problem now is i cant get to sleep there are too many things i need to setup/learn ! :)

---

