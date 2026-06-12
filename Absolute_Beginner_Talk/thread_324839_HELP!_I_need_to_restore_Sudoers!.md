---
title: "HELP! I need to restore Sudoers!"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by vgrisham on 2006-12-24
Hi,

I was trying to get the firestarter gui to startup automatically upon login, so I followed the instructions [here]("http://www.ubuntuforums.org/showthread.php?t=177738"). Now synaptic won't launch. When I try to launch from the terminal, it tells me I'm not running as root. When I use the sudo command to start, it tells me that sudoers is running in mode 600 and should be in 440.

FORTUNATELY, I backed up my original sudoers file as sudoers.bak. How do restore the original file? I no longer care about getting firestarter to load automatically. I just want synaptic back. 

Thank you in advance!

Vaughn

---

### Post by pseudonym on 2006-12-24
You could boot up the ubuntu live cd (or some other live cd like knoppix), mount  your / partition and the medium where your backup is stored, and then just copy it over...

---

### Post by vgrisham on 2006-12-24
> **pseudonym said:**
> You could boot up the ubuntu live cd (or some other live cd like knoppix), mount  your / partition and the medium where your backup is stored, and then just copy it over...

My backup file is in the /etc folder as sudoers.bak. Isn't there some way to just rename it and replace the broken sudoers file? Also, if I boot into a live cd, isn't it going to not allow me to make changes to the / partition?

---

### Post by pseudonym on 2006-12-24
> **vgrisham said:**
> My backup file is in the /etc folder as sudoers.bak. Isn't there some way to just rename it and replace the broken sudoers file? 
Ordinarily, yes, but the way things are at the moment, you're likely to run into the same type of trouble you had with firestarter ie. an inability to perform administrative functions. 
> **vgrisham said:**
>  Also, if I boot into a live cd, isn't it going to not allow me to make changes to the / partition?
No, because the live cd is a completely separate environment, in which you shouldn't have any trouble with 'sudo'. Just make sure to give yourself write permissions when you mount your / partition. There should be a right-click option on the drive/partition's icon.

HTH

---

### Post by vgrisham on 2006-12-24
> **pseudonym said:**
> Ordinarily, yes, but the way things are at the moment, you're likely to run into the same type of trouble you had with firestarter ie. an inability to perform administrative functions. 

No, because the live cd is a completely separate environment, in which you shouldn't have any trouble with 'sudo'. Just make sure to give yourself write permissions when you mount your / partition. There should be a right-click option on the drive/partition's icon.

HTH

Thank you for your help. So just to clarify. I'm going to boot to the Live CD. Am I then going to rename sudoers.bak to sudoers? Or am I going to copy the boot cd's version of sudoers to my /etc folder?

---

### Post by pseudonym on 2006-12-24
> **vgrisham said:**
> Thank you for your help. So just to clarify. I'm going to boot to the Live CD. Am I then going to rename sudoers.bak to sudoers? Or am I going to copy the boot cd's version of sudoers to my /etc folder?
Sorry, I should have made that clear. Yes, you are going to rename your backup to sudoers. The live cd is just the medium which enables this.

---

### Post by vgrisham on 2006-12-24
> **pseudonym said:**
> Sorry, I should have made that clear. Yes, you are going to rename your backup to sudoers. The live cd is just the medium which enables this.

Cool. It's fixed! Thanks so much! I just rebooted to restore mode, switched to the /etc folder, and entered "mv sudoers.bak sudoers". I rebooted, and voila, Dapper is Dapper again. 

Thanks VERY much. Merry Christmas.

Vaughn

---

### Post by pseudonym on 2006-12-24
Well, it was even easier than I thought :)

merry xmas to you, too.

---

### Post by vgrisham on 2006-12-24
> **pseudonym said:**
> Well, it was even easier than I thought :)

merry xmas to you, too.

Well, shoot. Wouldn't you know it? Now Firestarter doesn't work at all. When I click from the System Administration menu, the throbber twirls for a bit, then nothing. When I try to launch from the terminal, I get this message: 

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5836): Gtk-WARNING **: cannot open display:

Any ideas? 

Thanks,
Vaughn

---

### Post by pseudonym on 2006-12-24
> **vgrisham said:**
> Well, shoot. Wouldn't you know it? Now Firestarter doesn't work at all. When I click from the System Administration menu, the throbber twirls for a bit, then nothing. When I try to launch from the terminal, I get this message: 

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5836): Gtk-WARNING **: cannot open display:

Any ideas? 

Thanks,
Vaughn
Firestarter should still be working - it's just the gui that's causing you problems. It sounds like an Xauthority issue. In the past, I've used this to fix it up -
In terminal type ```
sudo export XAUTHORITY=/home/your_user_name/.Xauthority
```
then logout and log back in again.

---

### Post by vgrisham on 2006-12-24
I get this message when I try that: sudo: export: command not found

---

### Post by pseudonym on 2006-12-24
> **vgrisham said:**
> I get this message when I try that: sudo: export: command not found Try and open up the root terminal (is it still in the ubuntu menu?) and do it from there. If you get a similar error to the one with firestarter, type 'sudo -s -H' to become root from your terminal, then run the 'export...' command from that. Basically, you need to be root to run this command.

---

