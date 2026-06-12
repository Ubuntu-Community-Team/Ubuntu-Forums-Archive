---
title: "Forgot Password"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by NeoGreen on 2006-08-05
Hello, I need help. I forgot my password on my Ubuntu machine.  I have a laptop running Ubuntu 5.10. I haven't turned it on in a while because I have been playing around with my new desktop (which I installed Dapper on).  How can I retrieve or reset my password?  Any advice will help.:confused:

---

### Post by moma on 2006-08-05
Do this:

0) Restart your computer so you can see the GRUB-boot menu.

1)  When in boot-menu, select the Ubuntu-line in question and press [COLOR="Navy"]'e'[/COLOR] to edit that line.
Choose the "kernel...." line and press [COLOR="Navy"]'e'[/COLOR] again to edit it.  
Add word "single" at the end of  the line as shown in this example. 

[COLOR="Sienna"]kernel    (hd0,6)/boot/vmlinuz-2.6.15-23-k7  root=/dev/sda7 ro quiet splash [/COLOR][COLOR="Red"]single [/COLOR]

Quit the edit mode by pressing [Enter] (i think) and press  [COLOR="Navy"]'b'[/COLOR] to boot.
-----------------------
Your Ubuntu will now boot up into single-user (maintenance) mode.  And it will show you a root-shell.  

2) Change the passord for your user.
# [COLOR="Green"]passwd username [/COLOR]
[COLOR="DimGray"]Enter new UNIX password: xxxxxxx[/COLOR]

3) [COLOR="Sienna"]^d[/COLOR] or [COLOR="Sienna"]exit[/COLOR] 
will continue the boot-process to runlevel 2 (which is the normal state of Ubuntu).

---

### Post by Barney on 2006-08-06
I didn't forget my password, but the one I use was "forgotten" by Dapper.  I tried the above solution - no success.

Any other ideas about how to get around this password problem and get booted up?

Barney

---

### Post by Jagot on 2006-08-06
Boot in the recovery mode (should be an option in your Grub), then when at the prompt, then you can reset your password by doing this:

```
passwd username
```

---

### Post by Barney on 2006-08-06
I tried the above and system appeared to accept the new password, but still can't get booted up.  From root, what command will boot into Dapper?

---

### Post by Jagot on 2006-08-06
After you run the command you have to reboot then you should be able to lohin with the new password.

---

### Post by Barney on 2006-08-07
Tried all of the above - nothing seemed to work; re-installed, back up okay.

---

