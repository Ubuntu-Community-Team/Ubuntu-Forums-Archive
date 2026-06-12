---
title: "help, total noob, ruined my ubuntu 7.10"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by relaxmosphere on 2007-10-30
ok , here I go. I'm a total linux noob, although I've got a great deal of experience with other OS's and hardware. I'm not big on command lines, trying to learn.

Installation went well, I never had an issue. Then, I got a little overconfident. I applied all the tweaks listed here ([http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)), except for the swappiness. Now, the GRUB loads fine, I get the Ubuntu splash screen, kernel starts loading.... then get an almost BSOD that tells me that there was an issue loading the x-something environment, and to seek help. So.... Help?!

---

### Post by overdrank on 2007-10-30
> **relaxmosphere said:**
> ok , here I go. I'm a total linux noob, although I've got a great deal of experience with other OS's and hardware. I'm not big on command lines, trying to learn.

Installation went well, I never had an issue. Then, I got a little overconfident. I applied all the tweaks listed here ([http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)), except for the swappiness. Now, the GRUB loads fine, I get the Ubuntu splash screen, kernel starts loading.... then get an almost BSOD that tells me that there was an issue loading the x-something environment, and to seek help. So.... Help?!

Hi can you back track your steps where you edited the grub in the recovery mode. Recovery mode will be the second option in the grub. Good luck!

---

### Post by relaxmosphere on 2007-10-30
I'll give it a go and report back... don't know what I'm doing, so I will stop as soon as something looks screwy. Thanks for the quick response!

---

### Post by jusmurph on 2007-10-30
Its good to make mistakes in the begining, you learn heaps.

---

### Post by ~chinook~ on 2007-10-30
I have made mistakes and had to reinstall before. It forces you to leard.

---

### Post by HermanAB on 2007-10-31
The nice thing about Linux is that it is so easy to install.  So, simply pop in that CD and do it again.  I re-installed Linux several times before I found my way around with confidence and I actually studied Unix years before.

One tip:  Be sure to create a separate /home directory so that the next time you re-install, you don't have to format /home and lose all your data, desktop settings, email and whatnot...

Cheers,

Herman

---

### Post by oldos2er on 2007-10-31
Did you install 7.10 Gutsy Gibbon? If so, there seems to be a bug if you set CONCURRENCY=SHELL. Try setting your /etc/init.d/rc back to default (hope you made a copy), which is CONCURRENCY=NONE.
 If you made all the other changes correctly, things should be ok. If not, post back.

---

### Post by juantovarm on 2007-10-31
the more you screw up, the more you are forced to learn, i've killed x i don't know how many times, but that got me to use the command line and get used to it, now i don't screw up so often so i just kill things on purpose when i have nothing to do, just to see if i can fix them, it's only a program in the end, you can always reinstall  :)

---

### Post by relaxmosphere on 2007-11-01
alright, so...... I don't know if I made a copy or not..... in recovery mode, couldn't I edit the file? or no? When I boot in recovery mode, i get to the command line just fine. I don't know what to do from there, and I am having some problems trying to find help online. How can I, from the command line, edit that file to set CONCURRENCY=NONE? is it possible if I didn't make a back-up? thanks for the help and cheering on!

---

### Post by Maestro23 on 2007-11-01
> **relaxmosphere said:**
> alright, so...... I don't know if I made a copy or not..... in recovery mode, couldn't I edit the file? or no? When I boot in recovery mode, i get to the command line just fine. I don't know what to do from there, and I am having some problems trying to find help online. How can I, from the command line, edit that file to set CONCURRENCY=NONE? is it possible if I didn't make a back-up? thanks for the help and cheering on!

If the file is there.... At the prompt you can:

> sudo nano -B /etc/init.d/rc

nano is a text editor just like gedit.  The -B flag tells nano to make a backup copy.  Make your changes.  Then you will need to:

Ctrl+O (Writes the File)

Ctrl+X (Exits the program)

---

### Post by relaxmosphere on 2007-11-02
So tried that stuff in the previous post... I can do it, but I cannot save it. It tells me that it is in a read-only portion of the drive. Is there a way to get around that, to be able to save? Thanks for all the help, I do feel like I am making some progress!

---

### Post by dondad on 2007-11-02
> **relaxmosphere said:**
> So tried that stuff in the previous post... I can do it, but I cannot save it. It tells me that it is in a read-only portion of the drive. Is there a way to get around that, to be able to save? Thanks for all the help, I do feel like I am making some progress!

Use sudo in front of the command for nano.

---

