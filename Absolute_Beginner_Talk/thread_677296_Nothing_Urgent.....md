---
title: "Nothing Urgent...."
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Jake90 on 2008-01-24
Hi, I only recently started using linux so keep it simple please. I have 2 problems that aren't so urgent but I'd still rather get rid of them.
1 When I select  Ubuntu from Grub I get this message (everything works fine if I wait 30 sec but I'd rather not wait)
".Starting up....
You passed an undefined mode numberpress <Return> to see video modes available <Space> to continue or wait 30 seconds"
2. Is there a way to change the default color of Splash. I changed the wallpaper, login background and everything I could think of. When it boots before it goes into the log in screen I changed it to blue. Then after I log in it goes to that ugly brown then shows the Splash picture I selected then goes back to that ugly brown then shows my wallpaper. When I log off it just shows blue, now brown.


Oh also I posted on an existing thread on a little more urgent problem but haven't gotten a response if you can help me out I would appreciate it. Here is the thread
[http://ubuntuforums.org/showthread.php?t=582934]("http://ubuntuforums.org/showthread.php?t=582934")

---

### Post by PeterJS on 2008-01-24
> **Jake90 said:**
> Hi, I only recently started using linux so keep it simple please. I have 2 problems that aren't so urgent but I'd still rather get rid of them.
1 When I select  Ubuntu from Grub I get this message (everything works fine if I wait 30 sec but I'd rather not wait)
".Starting up....
You passed an undefined mode numberpress <Return> to see video modes available <Space> to continue or wait 30 seconds"

That's related to your grub configuration. If you open up your grub config file with:
```

sudo gedit /boot/grub/menu.lst

```
Near the bottom you will find your boot stanza's they look like this:
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=93b858f0-9935-4769-a6dd-c571bc66b3db ro splash quiet
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
quiet

```
Note that mine doesn't have a vga option on the kernel line, yours will, and that's your problem, you can google around to find the right code for it, or just consign yourself to having ugly physical terminals and delete the option entirely like I did.

> 
2. Is there a way to change the default color of Splash. I changed the wallpaper, login background and everything I could think of. When it boots before it goes into the log in screen I changed it to blue. Then after I log in it goes to that ugly brown then shows the Splash picture I selected then goes back to that ugly brown then shows my wallpaper. When I log off it just shows blue, now brown.

You're supposed to be able to change that in gdmsetup but due to a bug that doesn't work, but you can go hard code in a color in the loading script see here:
[http://ubuntuforums.org/showpost.php?p=4185706&postcount=5](http://ubuntuforums.org/showpost.php?p=4185706&postcount=5)

> 
Oh also I posted on an existing thread on a little more urgent problem but haven't gotten a response if you can help me out I would appreciate it. Here is the thread
[http://ubuntuforums.org/showthread.php?t=582934]("http://ubuntuforums.org/showthread.php?t=582934")
I'll go take a look at that.
EDIT:
We'll I looked at it, never used banshee so I can't be specific, but have you installed the restricted extras package for codecs? Have you tried Rhythmbox or Amarok?

---

