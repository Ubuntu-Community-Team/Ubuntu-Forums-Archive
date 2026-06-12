---
title: "X server failure"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by Romin-1 on 2007-04-26
This morning when I fired-up the PC Dapper Drake started loading then I got this message:

> "Failed to Start X server. It is likely not set up correctly. Would you like to view the report?".

I clicked "Yes" and didn't know what I was looking at. Clicked on the "NO" button and got this:

> " The X server is now disbled. Restart GDM when it's configured correctly".

Under this is my login Jon@MMI:~$ with a blinking cursor. I have no idea what to enter there to fix this situation as I'm Ubuntu challenged.

Any help will put you at the top of my Xmas card list,

Jon

---

### Post by taurus on 2007-04-26
You probably need to reconfigure your X again.

```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by Romin-1 on 2007-04-26
Thanks for the hasty reply, taurus,

I tried you suggestion but it returned this reply:
> 
"X package is not installed".

I have the live CD if needed. Just don't know which way to go with this.

Jon

---

### Post by Seisen on 2007-04-26
You need to reinstall the X by doing this.

```
sudo apt-get install x-window-system-core
``` if you can access the internet you can download it from the repo's.

---

### Post by Romin-1 on 2007-04-26
I have no problem accessing the internet with windoze. It's when I try to boot Ubuntu that I have the problem.

I get the splash screen then it starts just about everything until it gets to the X server which, as I read it, is the desktop or GUI. I do get "OK"s for everything prior to the problem area.

Can I re-install Ubuntu from the disc over the existing one or would that screw it up even more?

I have no idea where to look for what you suggested or how to get it from windows into Ubuntu.

Jon

---

