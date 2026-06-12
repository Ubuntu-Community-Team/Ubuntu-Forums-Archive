---
title: "login/password?"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by viplayday on 2007-10-29
I have installed Xubuntu n a machine and I have not been on it since. I guess I put a password on it. I know what the password would be but not the user name. Is there any way of getting around the login process? Thank you very much for taking the time to read this

---

### Post by Dr Small on 2007-10-29
You would have to bootup in recovery mode, from GRUB.

---

### Post by overdrank on 2007-10-29
> **viplayday said:**
> I have installed Xubuntu n a machine and I have not been on it since. I guess I put a password on it. I know what the password would be but not the user name. Is there any way of getting around the login process? Thank you very much for taking the time to read this

Hi and if you know the password then at the login screen in the bottom right corner is the user name. :KS

---

### Post by viplayday on 2007-10-29
Thank you  for the info!! off coarse  now I am going to ask how to start up in grub. I am new this OS. I have no disks I installed over windows. is there a key i strike as I am booting up?

---

### Post by taurus on 2007-10-29
When you first turn on your machine, you would see a GRUB menu asking you which OS you want to boot.  If you don't see that menu, then press Esc key to see it.  Then, use the down arrow key to move down to the Recovery Mode and boot from that.  Once it's up run

```
ls -la /home
```
to see what is your login name is.  Then, reboot.

```
shutdown -r now
```

---

### Post by Dr Small on 2007-10-29
If you do not see the GRUB menu (which apparently by your reaction, you don't), you press ESC (escape) to access the GRUB menu, at bootup (it should flash across your screen telling you to press ESC.)

But try Overdrank's recommendation. It may be easier.
By the way, Hi there Overdrank. Long time no see ;)

Dr Small

---

### Post by viplayday on 2007-10-29
Good call about the name that is my wireless routers name. I tried to login with the name listed on the bottom right hand side of the screen next to the time and date. it will not log me in with any of the passwords i would have used. I must try to boot up some other way.

---

### Post by Dr Small on 2007-10-29
Please go back up and read taurus' post.

---

### Post by viplayday on 2007-10-29
Thank you guys you all rock!!!! I appreciate all the help! I think this ill work I just found out that the fan is dead now I am out the door to get a fan for this one. Thanks again.

---

