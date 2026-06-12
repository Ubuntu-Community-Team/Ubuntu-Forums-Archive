---
title: "apt-get"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by jayser on 2007-01-10
Hello, 

I just download the new version of the server. I booted off the cd, then while it was live I did the install.

I am trying to install vsftpd and ssh server but when I do a sudo apt-get install vsftp

I get coudn't find package, I also get the same when trying to install the ssh server.

any clues?

Thanks,
Jayser

---

### Post by jpeddicord on 2007-01-10
You needed to add a D to vsftp:```
sudo apt-get install vsftpd
```and SSH, while it can be installed by the name of 'ssh,' it is recommended to use this package instead: ```
sudo apt-get install openssh-server
```

Quick tip: To search for a package, use the command `apt-cache search <paramaters>`

Jacob

---

### Post by jayser on 2007-01-10
Sorry about that, I didn't type it correctly in the post. I did type it in correctly and got the those errors.

These packages should be on the Server's cd, right?

Thanks again,

Jayser

---

### Post by misterpms on 2007-01-10
I'm new to Ubuntu and I don't know anything about the programs that you are trying to install but you can try the following:

See if you already have the package
```
dpkg -l vsftpd
```

If not then
```
sudo apt-get update;
apt-cache search vsftpd; If you see it then
apt-get install -y vsftpd
```

If this doesn't work then I'm also interested in finding out why.

Edit: jacobmp92 already mentioned the apt-cache search

---

### Post by meng on 2007-01-10
Is your machine connected to the internet? I can't confirm whether those packages are on the install CD.

---

### Post by Modernity on 2007-01-10
Is it giving you an error of some type? Post your results of what comes up.

---

### Post by jayser on 2007-01-10
Thanks for all the responses!!! Yup it wasn't connected to the internet, I thought it would just install the packages off the cd.  Anyhow once I connected to the internet and ran the update command, those packages installed nicely.

Thanks again!
Jayser

---

