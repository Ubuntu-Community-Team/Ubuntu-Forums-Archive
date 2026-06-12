---
title: "Would you tell me how to reinstall Ubuntu via Terminal?"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-16
[COLOR="Darkblue"]How are you? My name is Chad Syphrett. I'm a new member of this online-community, so like most newbies, I need help solving a common problem, which most new users of Ubuntu seem to need help solving. I need someone to tell me (step-by-step instructions) how to either reinstall Ubuntu via the "terminal" _or_ fix my screen-resolution via the termiinal.

I'm using a Dell Inspiron 531s with Ubuntu Linux 7.10 [Preinstalled]
Type: AMD Athlon 64 X2 3800+ Processor  
Model: WL400GSA1672 
Video-Card: Integrated NVIDIA GeForce 6150 LE Graphics 
Including: VGA Output

**_Important note_:**[/COLOR]
[COLOR="Red"]**I've been using a LCD Monitor: "HP Pavilion f1503" for that computer**[/COLOR]

[COLOR="Green"]When I started my new Dell computer (with Ubuntu 7.10 preinstalled ), Ubuntu loaded within 1 minute, and as soon as the "Installation-Wizard" window was displayed on my LCD monitor a warning message (seen below) appeared:[/COLOR]
[COLOR="Darkred"][b]"Warning
PC video resolution setting is out of range
Change setting to Recommended resolution
1024x768@60Hz
RED GREEN BLUE"[/b][/COLOR]
[COLOR="Green"]I changed the display-settings to the "recommended resolution", and restarted my computer, then after Unbuntu's login window appeared again, the text within the the Ubuntu GUI was completely illegible  (meaning: the login-page and everything else on Ubuntu, such as the desktop image & icons were completely blurry, overlapping each other in a tile-like pattern). 

EDIT: The person, who sold that computer to me told me to restart my computer, wait for the Ubuntu login-page to appear then push Ctrl+Alt+F1 to make the terminal open, then type the following commands:[/COLOR]
```
sudo nvidia-xconfig
```
[COLOR="Green"]Ater I typed all of that in the terminal, I got this error-message: "command not found". Please tell me what I did wrong & what I need to do to solve this problem.[/COLOR]

---

### Post by peabody on 2008-02-16
That should actually be Ctrl+Alt+backspace.

If that doesn't work, post here and I have another suggestion.

---

### Post by ahuman on 2008-02-16
> **peabody said:**
> That should actually be Ctrl+Alt+backspace. If that doesn't work, post here and I have another suggestion. [COLOR="darkred"]It didn't work for me. I typed the following command after I logged in with my username and my password via the terminal:

*sudo nvidia-xconfig*

After I typed all of that in the terminal, I got this error-message: "command not found". Would you please tell me what I did wrong & what I need to do to either: reinstall Ubuntu (via terminal) and/or reset my screen-resolution via the terminal?[/COLOR]

[color="Red"]**Here is all of the revelant information that appeared in that terminal after I logged in to Ubuntu and typed:[/color]** *sudo nvidia-xconfig*  [COLOR="Red"]**as a command:**[/COLOR]
```
4XLDLD1 login: myusername
Password:
Last login: Sat Feb 16 01:12:32 CST 2008 on ttyl
Linux 4XLDLD1 2.6.22-14-generic #1 SNP Thu Jan 41 23:33:13 UTC 2008 x86_64

The programs included with the Ubuntu system are free software:
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applical law.
myusername@4XLDLD1:&#732;$ sudo nvidia-xconfig
[sudo] password for myusername:
sudo: nvidia-xconfig: command not found
```

---

### Post by peabody on 2008-02-16
Someone responded to your other thread with some good advice, I recommend you follow it.  If even *that* doesn't work, you can try as a last resort:

Let's see if Ubuntu's "bullet-proof" X is a claim they can keep :), try the following in the terminal, but be very careful to type it exactly as shown.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.backup
```

Then alt+f7 to the login window, and press control+alt+backspace again.  In an ideal world, this will bring the xconfig back to square one.

---

### Post by ahuman on 2008-02-16
[COLOR="Purple"]I didn't make more than 1 thread on this website. When you have enough time to help, again, would you please send the url of that thread, to which you mentioned I should go?

I appreciate your kindness & patience.

P.S. Did you mean this thread: "[Desktop visual problems](http://ubuntuforums.org/showthread.php?t=697906)"[/COLOR]?

---

