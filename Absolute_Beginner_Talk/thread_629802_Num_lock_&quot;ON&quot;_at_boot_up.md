---
title: "Num lock &quot;ON&quot; at boot up"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Smittysmit on 2007-12-02
Is there an easy way to get the "Num-Lock" to be on at boot up?  Everything is set in the BIOS and it worked OK in windows (with a regedit).

I'm a noob...so make it simple.  Thanks in advance.

---

### Post by strictly_serious on 2007-12-02
> **Smittysmit said:**
> Is there an easy way to get the "Num-Lock" to be on at boot up?  Everything is set in the BIOS and it worked OK in windows (with a regedit).

I'm a noob...so make it simple.  Thanks in advance.

What is the specific make and model of your keyboard? Is it USB/PS2?

Are you booting into console mode or GNOME or KDE or another GUI?

You should not have to regedit in windows for something like this.

---

### Post by Smittysmit on 2007-12-02
It's a PS2 keyboard with Gnome.  With XP-Pro, I had it set to require pressing C+A+D to logon and that required a regedit (I think).

---

### Post by fineas on 2007-12-02
From [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

[I]Enabling NUM LOCK at boot 

The Default behavior is for the NUM LOCK key to be off; if you are on a desktop and have a keypad though, entering digits from it can be much quicker and you may wish to have it enabled for entering login password, etc. Here's how: 
From Synaptic, download and install "numlockx," or, from the command line; 
  sudo apt-get install numlockx
To get it working, you now have to edit the appropriate startup file. First, make sure you have a working backup of the file: 
  sudo cp /etc/gdm/Init/Default /etc/gdm/Init/Default.bak
Next, modify the gdm/Init file. In terminal: 
  gksudo gedit /etc/gdm/Init/Default
Scroll down to the end of the file, and above the line that says "exit 0" add the following: 
  if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on 
  fi
Next time you reboot, your NUM LOCK should default to "on."[/I]

For me, it worked just after installing numlockx :)

---

### Post by Smittysmit on 2007-12-02
Thanks Fineas!

Just tried that and rebooted twice and all is well.

---

### Post by fineas on 2007-12-03
> **Smittysmit said:**
> Thanks Fineas!



:mrgreen::mrgreen::mrgreen::mrgreen::mrgreen::mrgreen::mrgreen::mrgreen:

It 's the ubuntuguide, not me!

By the way, did you followed all that procedure or just installed the numlockx?

---

### Post by mahiyar on 2007-12-03
Thats why it is always good to keep visiting ubuntuforums even if you do not have a problem, all the time i thought this was not possible in Linux.

---

### Post by steven0451 on 2007-12-03
Wow, seems like a very long-winded way of doing it.

I just booted into Ubuntu *(new user here, so sorry if this is incorrect)*, hit the Num Lock key so that the light went on, then every time I reboot it's just on automatically now. The only exception is that this trick wont work for the logon screen.

---

### Post by fineas on 2007-12-03
> **steven0451 said:**
> 

I just booted into Ubuntu *(new user here, so sorry if this is incorrect)*, hit the Num Lock key so that the light went on, then every time I reboot it's just on automatically now. The only exception is that this trick wont work for the logon screen.

Yep, that's what I did in my last installation. In some of  my previous installation,though, I had to install the numlockx in order to have the Num Locks "ON" when starting an X-session. One of these two cases might be a bug :lolflag:

---

### Post by Smittysmit on 2007-12-04
The num-lock stays on...but now I seem to have a strange boot problem.  I have a dual boot system on different drives.  After I did the num-lock fix listed above, the machine does not recognize the keyboard at bootup.  I would typically press 'F8' to select the boot drive but it says "Keyboard Not Found" in the BIOS screen.  I've tried different keyboards with the same results.  Once Ubuntu (7.10) boots, the keyboard is fine with the num-lock on.  I haven't tried clearing the BIOS...yet   My specs are listed below.

Asus MOBO A8N32-SLI Deluxe
Nvidia 6800GT graphics
2 Gig RAM (Corsair)

Any thoughts???

---

### Post by steven0451 on 2007-12-05
> **Smittysmit said:**
> I would typically press 'F8' to select the boot drive but it says "Keyboard Not Found" in the BIOS screen.  I've tried different keyboards with the same results.  Once Ubuntu (7.10) boots, the keyboard is fine with the num-lock on.  I haven't tried clearing the BIOS...yet   My specs are listed below.

Asus MOBO A8N32-SLI Deluxe
Nvidia 6800GT graphics
2 Gig RAM (Corsair)

Any thoughts???
I can't help you there, but I can **bump** the post for you so that some experts can help you..
That's about the extent of my abilities on Ubuntu so far. :neutral:

---

### Post by Smittysmit on 2007-12-05
I'll try clearing the CMOS tonight.  Another screwy thing is I have the BIOS set to boot from the keyboard.  It starts by tapping the space-bar but is non-functional until Ubuntu is at the logon screen.

---

