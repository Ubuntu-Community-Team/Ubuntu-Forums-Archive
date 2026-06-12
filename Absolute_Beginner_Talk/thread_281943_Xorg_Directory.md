---
title: "Xorg Directory"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by rlozano on 2006-10-21
anyone have an idea why i dont have a X11R6 directory which is being used by xorg?

this is the reason why i can't seem to make my DRI active. ](*,) 

would appreciate for any feedback.

thanks so much in advance.

---

### Post by wieman01 on 2006-10-21
Ubuntu does not use X11R6 but X11 (long story)... So you find "xorg.conf" here:
> sudo gedit /etc/X11/xorg.conf

---

### Post by rlozano on 2006-10-21
dang! hpow come i did not realize this... ](*,) 

thanks for the info wieman. 

so this would mean i cannot make my DRI active and it will always be missing, coz the DRI package is actually looking for that directory.

i'm using ibmr51e and it graphics card is mobility radeon. been a pain really to make its rendering active and make that DRI working....

any idea?

thanks...

---

### Post by podunk on 2006-10-21
If you read this page:
[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

and your graphic adapter is listed then you can use this page to install the drive for Ubuntu:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

If it's an older ATI card you'll need to use method 1

---

### Post by po0f on 2006-10-22
rlozano,

What happens when you symlink /usr to /usr/X11R6?
```
$ sudo ln -s /usr /usr/X11R6
```

---

### Post by rlozano on 2006-10-22
here's what happened...

[HTML]randall@ibmr51e-ubuntu:~$ $ sudo ln -s /usr /usr/X11R6
bash: $: command not found
randall@ibmr51e-ubuntu:~$
[/HTML]

---

### Post by po0f on 2006-10-22
rlozano,

The $ was just meant for a placeholder for your terminal prompt, try it without the $:
```
ln -s /usr /usr/X11R6
```

---

### Post by rlozano on 2006-10-22
oh sorry...

i did it... and the prompt went back. no message of whatever. am i suppose to see something?

thanks so much for the help...

---

### Post by po0f on 2006-10-22
rlozano,

Now try to finish what you were trying to do in your original post.

---

