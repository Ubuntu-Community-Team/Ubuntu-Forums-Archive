---
title: "Choosing hibernate or suspend to ram at logout."
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by Bastanteroma on 2006-08-19
Is it possible to choose at the logout screen between suspending to ram and suspending to disk?  I know that both work fine on my desktop.

Thanks

---

### Post by rowanparker on 2006-08-19
Yes, just select "Hibernate".

---

### Post by Bastanteroma on 2006-08-19
I realized my wording was unclear: I want to be able to either suspend or hibernate, as I choose.  Is that possible?

---

### Post by rowanparker on 2006-08-20
Do you mean this:
**Suspend:** Just go to sleep then wake up when mouse moves (Like on Windows).
**Hibernate:** Save current state then power off, when powers on it resumes previous state.

---

### Post by Bastanteroma on 2006-08-20
I think I mean suspend to ram and suspend to disk (hibernate).  In windows they are called standby and hibernate.  I installed fedora also, and instead of hibernating when I choose suspend, it goes to standby, from which I resume by pressing the power button.

---

### Post by rowanparker on 2006-08-20
Yeah I know what you mean.

I don't think it's possible to "standby". The nearest is lock screen. Unless there is an unorthodox way of doing it?

---

### Post by Bastanteroma on 2006-08-20
Thanks Rowanpaker, but I just confirmed that suspend works on my machine with Breezy, since it is an option in xfce.  If I can't choose at logout, I'd like at least to make suspend-to-ram the default.

---

### Post by rowanparker on 2006-08-21
Oh right, well it doesn't seem to work on Gnome.

On Breezy, it remembers the last chosen thing doesn't it?

---

### Post by Bastanteroma on 2006-08-21
Found the answer here: [http://www.ubuntuforums.org/showthread.php?t=198616&highlight=gnome+suspend+ram+disk](http://www.ubuntuforums.org/showthread.php?t=198616&highlight=gnome+suspend+ram+disk)

lex1 wrote:
Execute gconf-editor, and visit apps/gnome-powermanager and enable "can_suspend". You can enable/disable suspend and/or hibernation from there.

Did the trick, both options appear on logout menu.

---

### Post by rowanparker on 2006-08-21
It didn't appear in my logout screen on dapper?

---

