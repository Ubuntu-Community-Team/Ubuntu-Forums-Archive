---
title: "I can't login anymore"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by drmoore1 on 2008-04-07
Ubuntu had been working all day but when it wouldn't let me edit the users I restarted and found this great message:

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the fail safe sessions to see if you can fix this problem.

details:

```

/etc/gdm/Xsession: Beginning session setup...
Setting Im through in-switch for locale:en_us
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default/mkdtemp: private socket dir: Permission denied
```

What can I do to fix this? I know I cant use GNOME safe mode, I tried and it wouldnt work.

---

### Post by riven0 on 2008-04-07
Can you log into the Failsafe Terminal? And if so, try installing XDM, (sudo apt-get install xdm) and choose that as your login manager when it asks. Now reboot the computer and see if you can log in.

---

### Post by drmoore1 on 2008-04-07
I can run Failsafe Terminal however when I tried to do as you said I recieved an error saying that /etc sudoer are in mode 0460 and that I was in mode 0440. So I am still stuck

---

### Post by mali2297 on 2008-04-07
> **drmoore1 said:**
> Ubuntu had been working all day but when it wouldn't let me edit the users I restarted and found this great message:


Do you mean that you tried to edit the /etc/sudoers file?

If so, boot in recovery mode and open the file again:
```

visudo

```
Undo  anything that you edited previously. Save (Ctrl+o), quit (Ctrl+x) and restart:
```

reboot

```

---

### Post by drmoore1 on 2008-04-08
It just told me permission denied. I guess I will try installing again for the third time but iinstalling XDM this time.

---

### Post by mali2297 on 2008-04-08
> **drmoore1 said:**
> It just told me permission denied. I guess I will try installing again for the third time but iinstalling XDM this time.

Did you actually boot in recovery mode?

You could also try opening /etc/sudoers directly with
```

nano /etc/sudoers

```

---

