---
title: "Change Default Operating System"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by MotorCityMadMan on 2006-02-06
[SIZE="2"]Hello ubuntu community, I need your help changing the default operating system on my machine at boot-up. The first boot screen reads like this.

GNU GRUB v0.95 (639k lower / 784640k upper)

ubuntu,kernel 2.6.12-10-386
ubuntu,kernel 2.6.12-10-386 (recovery mode)
ubuntu,kernel 2.6.12-9-386
ubuntu,kernel 2.6.12-9-386 (recovery mode)
ubuntu,memtest 86 +
other operating system:
Linspire 5.0.59 on /dev/hda5 (on /dev/hda5)
redetect (on /dev/hda5)
diagnostics (on /dev/hda5)
microsoft windows xp professional

The ubuntu,kernal 2.6.12-10-386 being the boot default operating system after 10 seconds.

How do I change the default boot operaing system to windows xp pro ?
How do I change the seconds for boot ? 
Can I have no seconds at the boot menu ?

The MotorCityMadMan[/SIZE]

---

### Post by Sutekh on 2006-02-06
[QUOTE=MotorCityMadMan]

How do I change the default boot operaing system to windows xp pro ?
[/QUOTE]
You should make a backup of your GRUB menu first
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```
Then start counting from 0 and every time you see something like
```

title Ubuntu 2.6.12.10-386

```
that uses **title** count up one.
When you get to Windows, find the line (near the top) that is
```

default 0

```
and change it to the number you counted to.  (Yours may very well be 9)

> How do I change the seconds for boot ? 
Look for this section in your GRUB menu.lst
```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout		5**
```
Just change the time here

> Can I have no seconds at the boot menu ?

The MotorCityMadMan[/SIZE]As far as I'm aware, no.

---

### Post by krusbjorn on 2006-02-06
You beat me to it, Sutekh! :P

[QUOTE=MotorCityMadMan][SIZE="2"]
How do I change the default boot operaing system to windows xp pro ?
How do I change the seconds for boot ? 
Can I have no seconds at the boot menu ?

The MotorCityMadMan[/SIZE][/QUOTE]


All these changes are done in the /boot/grub/menu.lst file. Open it with the command "sudo gedit /boot/grub/menu.lst". The file itself is quite self-explanatory, but here are a few hints.

To make WinXP your default operating system you need to change the line "default     0" to the corresponding number for WinXP in the list. I guess that would be 8 in your case (it starts counting from 0). However, I always found it easier to just cut/paste the WindowsXP from the list and place it right above "### BEGIN AUTOMAGIC KERNELS LIST". Your Windows XP entry probably is near the end of the file, and should look something like this:

> title           Windows XP Pro
root            (hd1,0)
map             (hd1) (hd0) 
makeactive
chainloader     +1
savedefault

If you cut/paste it, you mustnt change the "default   0", since if you place it above the Automagic list-start, it will be the first entry, meaning 0.

To change the number of seconds the menu is displayed, just change the value in the "timeout		10" line. I guess, if you put a zero there, the menu wont be showed at all. But if you do this and have WinXP as default OS, you probably wont be able to boot into linux and therefore never be able to change the file back. That would mean that you are eternally trapped in Windows ;).

---

### Post by Sutekh on 2006-02-06
[QUOTE=krusbjorn]However, I always found it easier to just cut/paste the WindowsXP from the list and place it right above "### BEGIN AUTOMAGIC KERNELS LIST". Your Windows XP entry probably is near the end of the file, and should look something like this:[/QUOTE]

If you do this you will have problems when upgrading the kernel using apt-get or Synaptic.

Look here;
[Ubuntu Forums - GRUB Help - Post #4]("http://www.ubuntuforums.org/showpost.php?p=694661&postcount=4")

---

### Post by krusbjorn on 2006-02-06
> **Sutekh]If you do this you will have problems when upgrading the kernel using apt-get or Synaptic.

Look here said:**
> Ubuntu Forums - GRUB Help - Post #4[/URL]


Thats why i said "right above". Or am i misreading you now?

Anyways, I placed my Windows 2k entry just before the automagic list starts, and it worked like a charm.

---

### Post by Sutekh on 2006-02-06
[QUOTE=krusbjorn]Thats why i said "right above". Or am i misreading you now?

Anyways, I placed my Windows 2k entry just before the automagic list starts, and it worked like a charm.[/QUOTE]
No you're completely right!  I misread you!  

Above those lines is fine as you said.

---

### Post by soundguy on 2006-02-06
Ok, I'm having a similar problem.  I get an error when I use "sudo gedit /boot/grub/menu.lst"  The error is:  GTK-warning **:cannot open display:" and then I go back to the prompt.  I'm a fresh brand new linux and ubuntu user so I know squat!  I'm a windows man trying for something new.  Any help is appreciated.  Thanks.

---

### Post by MotorCityMadMan on 2006-02-06
Thank you for your help. Very kind  :D 

Now windows is default o/s. 

Playing around with the boot seconds: I first changed it to 120 sec,
Trying to be funny as more than I use this machine.
Then I put this code in:

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		You have 30 seconds before kboom

No more sec. count. Now there's just the boot screen waiting for your desire.

---

### Post by Sutekh on 2006-02-06
[QUOTE=MotorCityMadMan]
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		You have 30 seconds before kboom

No more sec. count. Now there's just the boot screen waiting for your desire.[/QUOTE]
That's very interesting, thanks for sharing.  I wasn't sure if an indefinite wait was possible.

---

