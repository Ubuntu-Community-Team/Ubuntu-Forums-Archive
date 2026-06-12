---
title: "must be loggged in as root"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by GQed76 on 2005-12-15
i tried to install a driver in ndiswrapper and i told me i must be in root

does that mean in a root directory or logged in AS root.

I just have the login ID i created on the setup. i cant login as root.  no password?

---

### Post by 23meg on 2005-12-15
You don't need to log in as root, use "sudo" as a prefix to the commands you use to make changes that require root privilege, and when asked, enter your user pass.

---

### Post by earobinson on 2005-12-15
i assume you are using the terminal for this

sudo <command> then user password will do the trick for more info see this: [https://wiki.ubuntu.com//RootSudo](https://wiki.ubuntu.com//RootSudo)

EDIT: dam 23meg you are fast

---

### Post by GQed76 on 2005-12-15
sudo or $sudo?

whats the difference.

---

### Post by earobinson on 2005-12-15
$sudo is not a command some people use the $ sign to represent the start of user input..... sudo is all you need

EDIT: where did u get $sudo from btw?

---

### Post by 23meg on 2005-12-15
$ is the default prompt end character; just enter "sudo".

(edit: damn earobinson you're fast)

---

### Post by GQed76 on 2005-12-15
ahh directions on this site for how to install a wireless card.

Im trying to get my driver loaded.  I got ndiswrapper installed, got the driver on the desktop
now i want to install it

---

### Post by 23meg on 2005-12-15
Do a search for ndiswrapper on the forums and elsewhere (see my sig), and if you're having problems, start a new thread with a detailed description of the problem along with the errors you get.

---

### Post by GQed76 on 2005-12-15
i got it to work, but then before i installed the driver i realized all of netgears drivers were for 32 bit.  Im running ubuntu64

---

