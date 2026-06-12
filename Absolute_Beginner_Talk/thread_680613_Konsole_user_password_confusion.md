---
title: "Konsole user password confusion"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by nipplecrippler on 2008-01-28
My first day on Linux, and my first post here.  Be gentle with this virgin  :lolflag:

I'm in middle of creating a dual boot KUBUNTU 7.10 and Windows XP Pro, Install and following this guide - ```
http://www.apcmag.com.au/5459/dualboot_ubuntu_and_windows_xp
```

I'm at the point where I need to modify the boot menu and after opening Konsole I've hit a roadblock.  I enter this command -

[B]vege@ORAC:~$ sudo gedit /boot/grub/menu.1st
[sudo] password for vege:[/B]

But it won't accept my password  :confused:

My login password starts with a capital letter, is this the reason why?  If I type same password I'm told it's wrong, try again.

If I type the correct password I see this message - 

sudo: gedit: command not found

What to do from here guys?

---

### Post by kellemes on 2008-01-28
Gedit is not installed. So instead of gedit you should use "kate".
So you get : 

[B]kdesu kate /boot/grub/menu.lst


[/B]Edit: By the way, it's menu.lst and not menu.1st ;-)

Edit: In response to post 4 changed sudo to kdesu ;-)

---

### Post by nemilar on 2008-01-28
Since you installed Kubuntu, rather than Ubuntu, you don't have gedit installed, which is why it's saying "command not found."  gedit is the editor for the gnome desktop; you have KDE, instead of Gnome (that's what the 'K' is in 'Kubuntu').

Try replacing 'gedit' with 'kate', so for example:

```
sudo kate filename
```

As for the password issue, you're just typing it wrong ;) 
It doesn't display characters as you type (or asterisks) for security reasons.

---

### Post by p_quarles on 2008-01-28
The best practice is to use the graphical sudo command for the respective desktop environments. For Kubuntu, it should be:
```
kdesu kate filename
```
For Ubuntu, it's:
```
gksudo gedit filename
```
Explanation:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by nipplecrippler on 2008-01-28
Thanks for the help  :)

---

### Post by nipplecrippler on 2008-01-28
[COLOR="Yellow"]New Problem[/COLOR] - 

Should I create a new thread?  It is GFX card related.

My intention - Install and run ET, and using this guide - ```
http://ubuntuforums.org/showthread.php?t=5246
```

**Step 1 - Install the nVidia driver**

Using this guide - ```
https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia
```

Attempting to enable this restricted driver results in this error message - 

```
**Error - KDE Control Modul**e
The software source for the package
nvidia-glx-new
is not enabled.
```

Having scanned a few threads I see the problem seems to be the nvidia-glx-new driver.
Maybe I need to uninstall this and use the older nvidia-glx driver.

I'm at a bit of a loss as to what to do from here.

OS - KUBUNTU 7.10
gfx card - nvidia 6800GS

Start a new thread?  Post these questions in that existing ET Install thread?  Just keep my questions in this thread?

Thanks in advance for any help you might have.

---

### Post by p_quarles on 2008-01-28
Yes, please start a new post, in the Gaming & Leisure section.

---

### Post by nipplecrippler on 2008-01-28
Have done, thanks :)

```
http://ubuntuforums.org/showthread.php?t=681284
```

---

