---
title: "exporting firefox extensions and setting from root to a user"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by helvete on 2006-08-17
i think the subject line explains my situation, i created a root user but i want to have the same setting for all my users with out having to d/l every extension again, any ideas or tips or how to's, i searched but could not find...

---

### Post by aysiu on 2006-08-17
```
sudo cp -R /root/.mozilla /home/helvete/.mozilla
sudo chown -R helvete:helvete /home/helvete/.mozilla
```

---

### Post by helvete on 2006-08-17
i tried this but nothing happens, i'm using ff2 beta if that helps

---

### Post by mlind on 2006-08-17
You want to install extensions & set preferences globally ?

I guess proper way to do this is to use /etc/firefox/firefoxrc and /etc/firefox/profile. I haven't tried it myself, but extensions which work on read-only directory, should work just by copying these to /etc/firefox/profile/extensions.

I think you should test this on a sandboxed environment first..

---

### Post by aysiu on 2006-08-17
> **helvete said:**
> i tried this but nothing happens, i'm using ff2 beta if that helps
It's possible you might have an existing profile that's marked as the default.

Try this, then: ```
rm -rf /home/helvete/.mozilla
sudo cp -R /root/.mozilla /home/helvete/.mozilla
sudo chown -R helvete:helvete /home/helvete/.mozilla
``` Be **very** careful with that first command (copy and paste is good--instead of retyping). If you hit Enter too soon, you might delete everything in your /home directory.

---

### Post by helvete on 2006-08-17
yeah thats what i want to do saves having to go to each users accpunt and doing it loads of times, but i would need the code for terminal coz i'm still a newbie and not used to it but i'm getting there

---

### Post by aysiu on 2006-08-17
> **helvete said:**
> yeah thats what i want to do saves having to go to each users accpunt and doing it loads of times, but i would need the code for terminal coz i'm still a newbie and not used to it but i'm getting there
I just gave you the code. You just need to change *helvete* to whatever the real username is.

---

### Post by helvete on 2006-08-17
> **aysiu said:**
> It's possible you might have an existing profile that's marked as the default.

Try this, then: ```
rm -rf /home/helvete/.mozilla
sudo cp -R /root/.mozilla /home/helvete/.mozilla
sudo chown -R helvete:helvete /home/helvete/.mozilla
``` Be **very** careful with that first command (copy and paste is good--instead of retyping). If you hit Enter too soon, you might delete everything in your /home directory.

the first line of code is permission denied, i'm currently on a user profile should i change to root

---

### Post by aysiu on 2006-08-17
If you're trying to delete it from *another* users' directory, you'll need *sudo*, but you'll need to be even more careful about that first command. If you hit return too soon, you could delete your entire Ubuntu installation.

```
sudo rm -rf /home/username/.mozilla
sudo cp -R /root/.mozilla /home/username/.mozilla
sudo chown -R username:username /home/username/.mozilla
```

---

### Post by helvete on 2006-08-18
its not that i want to delete it, but it looks like there is no easy way to do it so i'll do it manually

---

### Post by mlind on 2006-08-18
> **helvete said:**
> its not that i want to delete it, but it looks like there is no easy way to do it so i'll do it manually

Did you try storing user preferences to /etc/firefox/profile ?

---

### Post by helvete on 2006-08-20
i've done a re-install so its sorted now thanx anyway

---

