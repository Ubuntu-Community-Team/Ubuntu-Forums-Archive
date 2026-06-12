---
title: "Cannot use sudo and no su password"
date: 2012-06-14
forum: Any Other OS
---

### Post by yeehi on 2012-06-14
I edited sudoers and saved it with a parsing error. (I tried to use visudo to edit the sudoers file but couldn't get the right command.)

Anyway, I now do not have a valid sudoers file, so I cannot use sudo. I need sudo to edit the sudoers file in /etc

I try to login as su but it doesn't accept the password I use for sudo. I have never set a password for su. I guess it must be the default. What is the default password for su ?

Thank you!

---

### Post by Cheesemill on 2012-06-14
There isn't a password that will work with su, the root account is disabled in Ubuntu.

You can boot into recovery mode and edit the sudoers file that way instead:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

PS - This is why you should always use visudo to edit the sudoers file :)

---

### Post by yeehi on 2012-06-14
Thanks for that great link, Cheesemill!

I have to use the down arrow key. There is one on my keyboard on the number pad. It shares the number 2 button. It looks exactly like an arrow pointing down. I try to select this down arrow but nothing appears. I have tried using the shift+2, alt+2, ctrl+2 but they don't do the trick. 

There is another place with up and down arrows, too. The down arrow shares a key with Pg Dn. It is an inverted triangle. Page down is in blue - i think I need to use the blue function key for page down to work.  Anyway, I can't get this down arrow key to produce anything on the command line either.

Any suggestions on how to get the down arrow working?

Thank you!

---

### Post by Cheesemill on 2012-06-15
If you press the num lock button first the arrows on your number pad will work.

---

### Post by yeehi on 2012-06-15
I tried num-lock first. I got it to toggle between entering a number and entering something else. Unfortunately, when I try to get it to enter something else, like a down arrow, nothing appears. The cursor remains in the same place and no character is produced. :(

This is frustrating!

Edit:

Ah! The down arrow key was working, after all. The problem was that I thought down arrow was an actual command on the command line. Instead, it was referring to moving down through a menu in instructions I was following. I don't actually have that menu, so I can't navigate through it. 

I still need to somehow drop to the root shell prompt from the command line though. I don't know how to do that.

---

### Post by mastablasta on 2012-06-15
here is how to use sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by yeehi on 2012-06-15
```
sudo -i
sudo passwd root
```

I can't do the above, as when I try I get a parsing error in sudoers error message. There is no valid sudoers file.

I am using Trisquel, a fully free, linux-libre distro based on Ubuntu. There is no menu option for getting root in the recovery console that I can see.

I wonder whether I will ever be able to get sudo back again on this installation... I might have to try booting with a live CD and editing the file from there somehow.

---

### Post by Cheesemill on 2012-06-15
> **yeehi said:**
> [CODE] I might have to try booting with a live CD and editing the file from there somehow.
This will work as well. Just boot from a Live CD, mount the root partition belonging to your problem installation and edit the sudoers file.


If you are having problems getting to the GRUB menu to try the fix that I mentioned previously then just keep hitting SHIFT when the computer is booting. This should bring up the GRUB menu.

---

### Post by yeehi on 2012-06-15
I tried that sudo mount /dev/sda1 /mnt and got an error message:

deleted i-node reference

By the way, for some reason when I tried booting from a live CD on a usb stick, I only reached a command prompt interface. There was no GUI. Previously, when I tried out Trisquel this way on the USB stick, prior to actually installing Trisquel, I got the usual GUI.

---

### Post by oldos2er on 2012-06-15
Moved to Other OS/Distro Talk.

---

