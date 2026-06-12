---
title: "Ubuntu 7.10 Splash Issue"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by AdemoS on 2008-02-06
First of all, hopefully I'm using the right term.

By "splash" I mean the loading bar right before the login screen.


Back when I used Ubuntu 7.10 32 bit, I had no issue displaying the loading bar.

But recently, using Ubuntu 7.10 64 bit, I get a black screen while it's loading, and nothing else.

Fortantatly, it does LOAD. And if I wait, the login screen comes up eventually.


But in order to get better feedback (and a more pleasant booting experience) I want to fix the loading bar. (or Splash)




I can post any applicable logs or settings files. I didn't post any yet, because I didn't know where to start, but let me know and I'll put them on a pastebin, or attach a TXT file, whatever is easier for you guys.

NOTE: Please make sure to tell me the default location of the logs and settings files, otherwise (being somewhat of a newbie) I won't be able to find them.

---

### Post by Existentialist on 2008-02-06
You can make sure the splash option is enabled in grub.  If you post the last part of your /boot/grub/menu.lst where the boot options are listed it will provide a starting place.

---

### Post by plucky on 2008-02-06
AdemoS,

Here is something you can try, ```
gksudo gedit /etc/usplash.conf
``` and add ```
xres=1024
yres=768
``` to that file, save and reboot.

Another thing you could try is add **vga=791** to the end of the kernel line in **/boot/grub/menu.lst**

Good luck

---

### Post by AdemoS on 2008-02-06
Thanks for the quick replies.

Existentialist: Here's the setup file requested:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d1f8e8ae-d388-41d8-bdfb-3119113b0f96 ro quiet vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d1f8e8ae-d388-41d8-bdfb-3119113b0f96 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet



Plucky: (cool avatar btw)

Both of your suggestions were already in use, but thanks for the advice.

---

### Post by erfahren on 2008-02-06
AdemoS - back up your current menu.lst and then open in Gedit with root permissions to edit
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_back

```
```

gksudo gedit /boot/grub/menu.lst

```
scroll down to that first kernel line that you posted and add "splash" - so it looks like
```

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d1f8e8ae-d388-41d8-bdfb-3119113b0f96 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

```

Also - as **plucky** mentioned, the wrong resolution for your display in usplash.conf is a common cause for slow boot up times and the splash not showing (it's a bug) - [the post here](http://ubuntuforums.org/showpost.php?p=3741687&postcount=21) mentions another step for that though. I don't know if it's completely necessary but it always worked for me.

---

### Post by erfahren on 2008-02-06
oh - also look for this section in the menu.lst and make sure there is "splash" there (the line is supposed to have a hash ( # ) before it)
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

```
note: for excellent information about GRUB's menu.lst see: [hermanzone's GRUB page](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by AdemoS on 2008-02-07
erfahren:

Thanks for your indepth reply.

I tried to edit the part you explained, but following this step:

> scroll down to that first kernel line that you posted and add "splash" - so it looks like

Caused my main boot not to load at all.

So, I had to boot into recovery mode, and remove the word "splash" from the line mentioned.

After doing that, I was able to boot regularly, though without a loading bar.


At the moment, this is what my menu.lst file looks like:
[http://pastebin.ca/895717](http://pastebin.ca/895717)

This is what my usplash.conf looks like:

```
# Usplash configuration file
xres=1024
yres=768

```

---

### Post by erfahren on 2008-02-07
hmmm... ok - did you check the /etc/usplash.conf file to see if the resolutions were correct in there?

---

### Post by erfahren on 2008-02-07
oh, you added that - disregard my last post

what resolution do you use for your display normally?

---

### Post by AdemoS on 2008-02-07
1440x900

But, I tried those values in the usplash.conf file, and go no difference in results. (even after using the update commands)

---

### Post by erfahren on 2008-02-07
I wanted to mention this - there;s a package called "startupmanager" (available in the repos) that can be used to adjust some settings in the menu.lst file (- like boot resolution, etc.) through a GUI.

it can come in handy

---

### Post by AdemoS on 2008-02-07
*nods*

I installed that in the past.

It unfortunately broke my regular boot, just as your suggestion did.



I feel as though the 64 bit part is somehow breaking the Splash on my system. 

It's annoying, because of how easily 32 bit Ubuntu booted with a Splash.



Thanks for your help though, if you have any other ideas let me know.

---

### Post by erfahren on 2008-02-07
well, I was just going to ask you do try setting those resolutions to 1280x800 in usplash.conf - just a "step" lower from your normal resolution - and do the update theme again.

if it doesn't seem to do anything you can just leave it, and go and change it to your correct values later if you work out another fix.


I wanted to give you this link, it's pretty informative [HOWTO: Change bootup resolution](http://ubuntuforums.org/showthread.php?p=1541970)

I don't know, good luck with it

---

