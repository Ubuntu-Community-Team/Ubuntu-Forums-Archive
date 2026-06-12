---
title: "Lost Account/Root Password"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by rmx.dave on 2007-06-18
Hello,

I just installed Ubuntu Feisty and somehow the password for my account is not the same. Also, the root password is not working. I know what the password should be, my only thought is that I must have mistyped it twice while setting it up. Anyway, I tried logging in as root, but it asked me for the root password to continue. No luck there, I tried entering passwd <username> in a terminal but it wants my old password. Is there any way (short of reinstalling this) to reset both passwords to something I know?

Thanks,
rmx.dave

---

### Post by Bachstelze on 2007-06-18
Boot in recovery mode, it will give you a root prompt without asking for any password, and will let you set a new password for your normal account.

And despite what others might tell you, creating a root password is neither necessary, nor useful, nor recommended.

---

### Post by dfreer on 2007-06-18
Well, ubuntu ships with no root password enabled by default, that might be part of your problem.

Reboot and when the GRUB menu appears, enter the recovery mode. After loading essential files you'll be given a shell with root permissions. To set the root password (not recommended but you can if you want to), type:
```
passwd root
```
And then enter your root password. for your user account to reset the password:
```
passwd *your_username*
```

---

### Post by Bachstelze on 2007-06-18
I repeat, creating a root password *is not* necessary !!

---

### Post by dfreer on 2007-06-18
> **HymnToLife said:**
> I repeat, creating a root password *is not* necessary !!

Just letting OP know how to do it, I recommended against it as well ;)

---

### Post by rmx.dave on 2007-06-18
That would work great, but when I reboot into recovery mode, it loads all of the essentials, and then asks me for my password (or hit CTRL+D to load GDM). On my other computer I am able to get into the root command line no prob, but here it's asking for a pass. And I don't want a password on my root account, I don't need one, like you said, its not needed...but somehow one was set. Is there any other way to reset my passwords?

---

### Post by Bachstelze on 2007-06-18
If it asks you for a password in recovery mode, that means you *did* set one. And now, you're toast, your only option is to reinstall.

---

### Post by dfreer on 2007-06-18
not quite true.. you can load a live CD and edit your /etc/passwd or /etc/shadow file, and delete the password hash in there for root. give me a few secs and I can give you a how to, but it should be fairly straightfoward. that should work.

Here's an example of what it should look like.
[http://ubuntuforums.org/showthread.php?t=3575](http://ubuntuforums.org/showthread.php?t=3575)

The solution is on the second page ;)

---

### Post by rmx.dave on 2007-06-18
That'd be great, thank you!

---

### Post by bizmeds on 2008-02-02
[COLOR="RoyalBlue"]Reboot and when the GRUB menu appears, enter the recovery mode[/COLOR].

Okay, I have rebooted when the GRUB menu appears I press F8, ( tried F12 as well) instead of going to recovery mode I am taken to the login page which I don't have a password that i can remember. I know don't use a root password. I did , lesson learned...

---

### Post by mcduck on 2008-02-02
> **bizmeds said:**
> [COLOR="RoyalBlue"]Reboot and when the GRUB menu appears, enter the recovery mode[/COLOR].

Okay, I have rebooted when the GRUB menu appears I press F8, ( tried F12 as well) instead of going to recovery mode I am taken to the login page which I don't have a password that i can remember. I know don't use a root password. I did , lesson learned...
F8 won't take you to the recovery mode, that's for Windows only. ;)

You have to select the recovery mode from the Grub menu (with arrow keys) and then press enter. That should take you to command line as root. Then run "passwd USERNAME" (replace with your actual user name) and you should be able to set the new password for your user. After that run "reboot" to restart the machine.

---

### Post by bizmeds on 2008-02-03
thanks for your reply!

Once i stopped thinking in win and started thinking in linux I was able to access recovery mode. navigate around the GRUB.using the arrow keys. entering a new passwd and viola problem solved,

---

