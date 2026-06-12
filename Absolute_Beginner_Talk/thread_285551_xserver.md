---
title: "xserver"
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by big_bad_brad on 2006-10-26
I reconfigured the xserver in a bad way and now I can't start ubuntu nor can I rerun xserver. It won't take my password.  Am I out of luck.

---

### Post by DSn0wMan on 2006-10-27
Please post specific errors. In most cases xserver shouldn't stop you from being able to log in.

If your xserver has become hosed you should still be able to log in via a terminal

Try hitting ctrl+alt+F2

---

### Post by big_bad_brad on 2006-10-27
You helped me get out of my 640x480 graphics mode and I appreciate that.  Then I wanted more resolution (which my monitor has the capability of) so I went back to xserver. Now When I start in ubuntu it appears normal then goes to a text screen and says "failed to start xserver"  and something like it probably wasn't set up correctly... Ctrl-Alt-F2 gives me the same thing I was getting which is brad-desktop login.  Asks me for password which it won't accept.  I'm at a loss.

---

### Post by DSn0wMan on 2006-10-27
It should be asking you for a username first, and then a password. 

brad-desktop login: <username then enter>
Password: xxxxxxxx

Sorry if that sounds lame, just covering the bases.

There shouldn't be anything with xserver that messesup your login.

You might try finding answers on how to reset your password. I am sure there is a way to do this in recovery, or single user mode.

---

### Post by CatKiller on 2006-10-27
> **big_bad_brad said:**
> It won't take my password.

Do you mean that you type in the password and nothing appears? That is supposed to happen.

---

### Post by big_bad_brad on 2006-10-27
Alright, somehow I was an idiot with the login(I swear it wasn't taking my password).  Anyway I tried to run xserver by typing what you had told me before 'sudo dpkg -reconfigure xserver-xorg' but it won't start.  I guess I'm probably doing something stupid again.
Any help? Thanks.

---

### Post by CatKiller on 2006-10-27
dpkg-reconfigure is one word.

---

### Post by big_bad_brad on 2006-10-27
Ok I am a complete idiot and have xserver reconfigured.  But one more question: My monitor has a capable resolution of 1280x1024 but if I choose that resolution it doesn't offer me that in the system preferences under screen resolution, Any ideas?
Thanks again

---

### Post by CatKiller on 2006-10-27
Check the refresh rate ranges of your monitor.

---

