---
title: "Boot Up Display"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by monkey56657 on 2008-02-01
Hello all. 

When booting into ubuntu I get a second of short message "Kernal Ready" or something and then the screen goes off until the time I arrive at the login screen. 

Im on Ubuntu x64 7.10 and with Nvidia 8800GTS (its overclocked but I dont think this is the cause). 

Any suggestions on what I should try to get some display during boot ?

Thanks.

---

### Post by shad0w_walker on 2008-02-01
It sounds like the usplash has a iffy configuration.

Open up a terminal (Applications > Accessories > Terminal) and run this command:

```
cat /etc/usplash.conf
```

Post the output of that command here. It's most likely assumed a resolution that isn't supported by your monitor and will be a nice easy fix.

---

### Post by monkey56657 on 2008-02-01
# Usplash configuration file
xres=1280
yres=1024

Im using 1280*1024 now as well.

---

### Post by shad0w_walker on 2008-02-01
Ok, strange as it sounds its probably that resolution (Even though you are running in it now)

Try this.

Open up the run dialog (Alt + F2) and run this command: 

```
gksu gedit /etc/usplash.conf
```

It will prompt you to enter your password to get root access.
When the file opens change it to read:

```

# Usplash configuration file
xres=1024
yres=768

```

Then hit save, close gedit and try it out.

---

### Post by monkey56657 on 2008-02-01
I made the change (also tried 800*600) but to no effect.

---

### Post by shad0w_walker on 2008-02-01
Damn, normally that sorts things out. Afraid I don't have any more suggestions however I will post again and give you a bump in the hope someone else comes along with a suggestion.

Good luck.

---

