---
title: "Help to get Ubuntu back in Mandriva grub"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by wapfu on 2007-07-08
Hi,
Well I tried a triple boot system.
Ubuntu is still fine , but I can't get back to it.
Runs well after my 7th install - gets easier each time I install it.
Installed a free version of mandriva and now the grub doesn't have ubuntu.
Has Mandriva and Xp - no ubuntu.
I've managed to get the ubuntu titleblock, root, kernel etc and copied it to a word doc.
Now all I have to do is get to the mandriva grub and insert the lines at the end of the list.
So i'm led to beleive.
And I don't know how, don't know the konsole code to use.
HELP

Ta
Best Regards
Bill

---

### Post by pyros on 2007-07-08
if you know the entries to add, boot into mandriva, open a console, and type:
```

sudo nano /boot/grub/menu.lst

```

Then you can make your changes, and press control and o to save to disk, then control and x to close nano.

PS, the menu.lst entry for ubuntu should look something like this:
```

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=ecc610e5-b197-41cb-af6b-7c893608ca6f ro quiet splash acpi=force irqpoll
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

```

---

### Post by wapfu on 2007-07-08
Thanks
Best regards
Bill

---

### Post by wapfu on 2007-07-08
Hi Back again,
I can get the terminal to show the list.
Moving the arrow keys moves the cursor.
I can get the cursor to the last letter at the end of the list.
Hitting the reurn or enter key doesn't give me a new line.
How do i get a new line so that he two don't merge?
If I screw up how do I recover?
How do i delete if I screw up to get back to the start.
Really I found / find ubuntu easier to use and just want it back rather than have to reinstall if all else fails.
Best regards
Bill

---

### Post by pyros on 2007-07-08
> **wapfu said:**
> Hi Back again,
I can get the terminal to show the list.
Moving the arrow keys moves the cursor.
I can get the cursor to the last letter at the end of the list.
Hitting the reurn or enter key doesn't give me a new line.
How do i get a new line so that he two don't merge?
If I screw up how do I recover?
How do i delete if I screw up to get back to the start.
Really I found / find ubuntu easier to use and just want it back rather than have to reinstall if all else fails.
Best regards
Bill

OK, I might have taken the wrong approach. You have a regular desktop in mandriva right? If it's gnome, you can use gedit to open the file. first thing to do would be to make a copy of the original menu file. This way you can always delete your edited file and replace it with the copy. You have to open it with sudo though, so that you have permission to edit the file-- I think this may be why you can't get a newline. If things get so screwed up you can't even boot, just pop the live cd in there and that should let you get in to replace the edited file with the backup.

---

### Post by wapfu on 2007-07-08
Cheers,
Live CD - good tip.
Unfortunately the desktop is KDE - arrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrr.
Thats why I like ubuntu.
Best regards
Bill

---

### Post by pyros on 2007-07-08
> **wapfu said:**
> Cheers,
Live CD - good tip.
Unfortunately the desktop is KDE - arrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrrr.
Thats why I like ubuntu.
Best regards
Bill

thats OK, in kde you should have kate instead of gedit. I should have mentioned that.

---

### Post by wapfu on 2007-07-08
Thanks,
Best Regards
Bill

As another option is there a way of replacing the mandriva grub with the feisty grub again.
Is there a simple way to retreive it? Given that feisty was loaded first, mandriva second and only now the mandriva grub is shown. Can I restore the fiesty grub and overwrite the mandriva.

---

### Post by pyros on 2007-07-08
Take a look here. it's  a bit involved for a posting here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by wapfu on 2007-07-09
Thanks,
Best Regards
Bill

---

### Post by wapfu on 2007-07-20
I have got it to work.
Once I had the list I was able to use nano - had to install the package.
Using control + O then Y for yes I saved it.
On next boot Ubuntu was back in all its glory on the boot menu - Yeah!!!!!!!!!
Success.
Best regards
Bill

---

### Post by pyros on 2007-07-21
> **wapfu said:**
> I have got it to work.
Once I had the list I was able to use nano - had to install the package.
Using control + O then Y for yes I saved it.
On next boot Ubuntu was back in all its glory on the boot menu - Yeah!!!!!!!!!
Success.
Best regards
Bill

Glad it worked out for you, and thanks for posting that it was successful. Sorry to recommend an editor that wasn't on the system.

---

