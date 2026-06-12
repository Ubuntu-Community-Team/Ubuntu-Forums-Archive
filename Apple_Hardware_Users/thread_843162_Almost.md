---
title: "Almost"
date: 2008-06-28
forum: Apple Hardware Users
---

### Post by jakem91 on 2008-06-28
I recently got a imac G3 computer from my work and decided to put xubuntu on it. I found the 7.10 version online and put both the desktop and addition versions on cd's and in the end the only thing that ended up working was the addition cd. I got it all loaded on the computer and when i restart the computer it shows up the xubuntu loading screen and it wont fully fill the loading bar under the xubuntu logo and then after 5 min of loading it ends up going to a black screen saying:

BusyBox v1.1.3 (Debian 1:1.13-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

I am able to type in some command after "initrams" but I dont know what command to type in. It would be much appreciated if some one can help. Oh and if anybody does help i am not the greatest with computers so try explaining in much detail.

Thanks

Jake

---

### Post by Bubba64 on 2008-06-28
I think a apple computer will only work with the ppc download did you use this.

---

### Post by stream303 on 2008-06-28
Your first stop should be here:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Basically, at the busybox initramfs prompt, you'd type:

**modprobe ide-core**

then just
**exit**

Also let us know what version of iMac G3 you are running and also how much ram is installed.  Do you know if the hard drive is oem, or has it been replaced with something larger?

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Also, due to the age of most G3's the pram battery may be very weak and you can run into the date-bug.  Keep this handy just in case:

[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

---

### Post by cariboo on 2008-06-28
The hardest thing I found was what boot option to use, not being a Mac person. I upgraded the ram with some old ram I had lying around, I had a 10GB hard drive I added as a second drive. So basically my specs are 350Mhz CPU 256MB Ram 10GB hard dirve running Xubuntu v 8.04. It took quite a while to install it, approx 1.5 hrs, but it runs surprisingly well, considering the age of the hardware. The only other problem I had was there where two ATI Rage 128 video cards installed, I removed one and it installed like normal.

Jim

---

### Post by stream303 on 2008-06-28
As for the ram, that's great - but also maybe a bit lucky.  I think the biggest difference between Apple ram and generic ram is the Cache-Latency CL/2 vs. CL/3 issue.  I'm not a memory expert by any means, but I've seen this crop up from time to time.  At any rate, glad to hear your box is running nicely!

---

### Post by jakem91 on 2008-06-28
> **stream303 said:**
> Your first stop should be here:

[https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

Basically, at the busybox initramfs prompt, you'd type:

**modprobe ide-core**

then just
**exit**

Also let us know what version of iMac G3 you are running and also how much ram is installed.  Do you know if the hard drive is oem, or has it been replaced with something larger?

[http://www.everymac.com/systems/apple/imac/index-imac.html](http://www.everymac.com/systems/apple/imac/index-imac.html)

Also, due to the age of most G3's the pram battery may be very weak and you can run into the date-bug.  Keep this handy just in case:

[https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)

thank you very much stream303 its up and running and works great

---

### Post by jakem91 on 2008-06-28
well now that i have it all up and running does anybody know how to install applications like rhythmbox and adobe flash player on it? When ever I try installing adobe flash player for linux it comes up as 

"What should Firefox do with this file?"
Open with Archive Manager (default)
Save to Disk

I tried both and seemed that the install appliction doesnt work

---

### Post by stream303 on 2008-06-28
Don't forget to make that permanent by editing
/etc/initramfs-tools/modules
as root, (ie gksudo gedit /etc/initramfs-tools/modules)

and adding
ide-core
to the end of it.  Make the system aware of the change with

sudo update-initramfs -u

Unfortunately, flash is a problem due to lack of PPC version.  You can try to get by with gnash, but ymmv.

Rhythmbox should already be installed by default, so I don't know what's up there.  You could also try Movie-Player (totem) or perhaps VLC.  For simple audio streaming, I just use ogg123 (vorbis tools) from the cli for the most part.

---

### Post by jakem91 on 2008-06-28
ok so can you give me step by step on making it perminate? Im quite slow at this.

---

### Post by stream303 on 2008-06-28
Sure.  Bring up a terminal (Applications > Accessories > Terminal) and then issue:

```
gksudo gedit /etc/initramfs-tools/modules
```

Supply your password when asked and the file should come up in the gedit editor.

Add this to the very end of the file:
```
ide-core
```
and save the file.

When you quit the editor, you'll still be in the terminal, and now we need to make the system aware of the change you made:

```
sudo update-initramfs -u
```

Now you are free to do whatever you want, and next time when you reboot, you won't have to type ide-core at the busybox prompt anymore.

---

### Post by jakem91 on 2008-06-28
> **stream303 said:**
> Sure.  Bring up a terminal (Applications > Accessories > Terminal) and then issue:

```
gksudo gedit /etc/initramfs-tools/modules
```

Supply your password when asked and the file should come up in the gedit editor.

Add this to the very end of the file:
```
ide-core
```
and save the file.

When you quit the editor, you'll still be in the terminal, and now we need to make the system aware of the change you made:

```
sudo update-initramfs -u
```

Now you are free to do whatever you want, and next time when you reboot, you won't have to type ide-core at the busybox prompt anymore.

Ok after i Typed in my password, what do i do next because i cannot seem to find the gedit editor. sorry for being so much of a trouble.

---

### Post by stream303 on 2008-06-28
No problem.  Let's use the cli for editing as well.  Instead of calling up Gedit, try this from the terminal - we're going to use the nano editor:

```
sudo nano -w  /etc/initramfs-tools/modules
```

Add ide-core as the last line in that file.

To save your changes, hit CTRL-O.  To get out of the editor, hit CTRL-X.

Now followup with the **sudo update-initramfs -u**  command.

---

### Post by jakem91 on 2008-06-28
> **stream303 said:**
> No problem.  Let's use the cli for editing as well.  Instead of calling up Gedit, try this from the terminal - we're going to use the nano editor:

```
sudo nano -w  /etc/initramfs-tools/modules
```

Add ide-core as the last line in that file.

To save your changes, hit CTRL-O.  To get out of the editor, hit CTRL-X.

Now followup with the **sudo update-initramfs -u**  command.

Ok after i type in the ```
sudo nano -w /etc/initramfs-tools/modules
``` I get this...

[[IMG]http://img108.imageshack.us/img108/5519/comp001hh4.th.jpg[/IMG]](http://img108.imageshack.us/my.php?image=comp001hh4.jpg)

I do not know what to do after this step.

---

### Post by stream303 on 2008-06-29
Cursor down, and add this as the last line:

ide-core

The last three lines of that file should look like this:

```
# raid1
# sd_mod
ide-core
```

Note that you should NOT place a hashmark # before ide-core.

Now, CTRL-O to write out the file.  CTRL-X to exit the editor.

Now you will be at the terminal command prompt again.  Type:

```
sudo update-initramfs -u
```

Done!

---

### Post by jakem91 on 2008-06-29
Alright now when i went to restart after doing all of that it will not even load any more here is what it looks like...

[IMG]http://img390.imageshack.us/img390/430/compwg8.jpg[/IMG]

Then it just stops loading from there. What do I do!

---

### Post by stream303 on 2008-06-29
I've never seen that fail before after successfully being able to do it via busybox, unless somehow your newly-edit modules file is corrupt perhaps.

I'm hoping that you didn't remove the hashmarks # from the first two lines shown, and only left it removed from the last line.

I'm also hoping that you allowed the initramfs -u command to finish the job and return you to the shell prompt before you rebooted.  It can take a little while on slower machines.

I hate to say it, and I'm sorry it happened, but at this stage it might be best to just reinstall, and live with typing in the modprobe command at the busybox/initramfs prompt due to unforseen hardware quirks on your machine.

Gutsy is known for this issue, so you might also want to consider installing either Feisty 7.04, or perhaps the latest Hardy, which don't exhibit this problem.

---

### Post by jakem91 on 2008-06-29
I got it all fixed i just re installed everything

---

