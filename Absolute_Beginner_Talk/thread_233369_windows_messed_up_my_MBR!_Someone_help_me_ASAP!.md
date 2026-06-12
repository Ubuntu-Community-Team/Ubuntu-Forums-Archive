---
title: "windows messed up my MBR! Someone help me ASAP!"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-08-10
Hello everyone,
	In a bid to get my wireless card working, i tried installing windows as a second OS to my Ubuntu. Windows wiped out my MBR, and also cannot boot itself (i dont know why). So now i am stuck with a brand-new laptop which doesnt boot into any OS :-( .
	How do i restore GRUB? i have searched the internet and these forums, but the solutions dont seem to work in my case. 

sudo grub-install /dev/hda ... returns this:
Could not find device for /boot: Not found or not a block device.

Also, i am not able to get into the rescue mode..am i supposed to add "rescue" parameter at the very start of the boot-parameter list or at the end??

I would be very glad and thankful if anyone can help this desperate soul and get his ubuntu to start booting again.

(PS. I really miss Ubuntu :-( )

---

### Post by orb9220 on 2006-08-10
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by kitt on 2006-08-10
I have gone-through the above mentioned thread..none of the techniques worked for me

---

### Post by orb9220 on 2006-08-10
Using the LiveCD and Overwriting the Windows bootloader

1. Pop in the Live CD, boot from it until you reach the desktop.

2. Open a terminal window or switch to a tty (Ctrl + Alt + F1).

3. Type "grub"

4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).

5. Type "setup (hd0)", ot whatever your harddisk nr is.

6. Quit grub by typing "quit".

7. Reboot.

---

### Post by kitt on 2006-08-10
root (hd0,x) says selected disk does not exist!

---

### Post by GuitarHero on 2006-08-10
You have to replace the x with whatever your hard drive is numbered as.

---

### Post by kitt on 2006-08-10
yes, i have replaced it with all the numbers..nothing is working..

---

### Post by gn2 on 2006-08-10
Have you tried to re-install Windows?

If you have a Windows CD re-install it first.

After it's installed then install Ubuntu.

You can't easily install Windows after another OS or it will over write the MBR.

I had this problem and cured it by removing the hard drive, putting it in a USB enclosure and formatting it with another PC. Obviously there are warranty implications so you may not wish to do this...

---

### Post by bigken on 2006-08-10
this is how I would try and do it 1st boot from your win xp disc and go into repair console at the promt type fixmbr then fixboot then exit this will get back into windows then if you dont have anything to lose just reinstall ubuntu or follow the above answers to reinstate the grub menu ;)

---

