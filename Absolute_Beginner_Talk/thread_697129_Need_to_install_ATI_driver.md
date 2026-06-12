---
title: "Need to install ATI driver"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Stone9 on 2008-02-14
Hi guys,

I downloaded the  ati-driver-installer-8-02-x86.x86_64.run driver installer from the ATI website:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

The installer instructions say to:

1) Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux driver download.
2) Enter the command ati-driver-installer-8-02-x86.x86_64.run to launch the ATI Proprietary Linux driver installer. The ATI Proprietary Linux Driver Setup dialog box is displayed.

However, when i navigate to my desktop in the terminal and enter that command, I receive this error:

bash: ati-driver-installer-8-02-x86.x86_64.run: command not found

The instructions are here:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat82-inst.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat82-inst.html)

Does anyone know what I'm doing wrong by chance?

Thanks in advance!

- Stone9

---

### Post by spiderbatdad on 2008-02-14
Just a thought ```
sudo chmod a+x name of installer.run
```

If it stiil won't run, you may need additional libraries to run the program. Try installing build-essential.

---

### Post by mrsteveman1 on 2008-02-14
you have to run it as ./ati-driver-installer-8-02-x86.x86_64.run

Most linux systems don't look in the current directory for the program you are trying to run, so you have to explicitly run it like that. If you had stuck the file in /usr/bin it would run normally from anywhere but you don't have to do that.

---

### Post by terklotron on 2008-02-15
> **mrsteveman1 said:**
> you have to run it as ./ati-driver-installer-8-02-x86.x86_64.run

Most linux systems don't look in the current directory for the program you are trying to run, so you have to explicitly run it like that. If you had stuck the file in /usr/bin it would run normally from anywhere but you don't have to do that.

I've got the same problem. Tried to run in terminal as ./,
Got 
```
./ati-driver-installer-8-02-x86.x86_64.run
bash: ./ati-driver-installer-8-02-x86.x86_64.run: Permission denied

```
Then I sudo'ed it and got
```
sudo ./ati-driver-installer-8-02-x86.x86_64.run
sudo: ./ati-driver-installer-8-02-x86.x86_64.run: command not found

```

Any clue??
I'm a beginner, so if anybody could explain to me, why this does not work.
If it denies me permission, then Super User should do the job no???

thanx:guitar:

---

### Post by spiderbatdad on 2008-02-15
As I said above: you need to have the correct permissions.  ie, chomd a+x, you also should install the package build-essential from synaptic. It contain libraries necessary for running some programs written in C.

---

### Post by Nikos.Alexandris on 2008-02-15
Why not just:

sudo sh ./ati-driver-installer-8-02-x86.x86_64.run

Cheers,

Nikos

---

### Post by terklotron on 2008-02-21
spiderbatdad=> Thanks man. I tried to use the chmod command you provided.

> **Nikos.Alexandris said:**
> Why not just:

sudo sh ./ati-driver-installer-8-02-x86.x86_64.run

Cheers,

Nikos

Thanks Nikos, That did the trick. I assume spiderbatdad's chmod also helped :-)
Only problem now is it's even slower...
I have no idea what's going ion and why.

Posted a new thread. Plz help
[http://ubuntuforums.org/showthread.php?p=4372126#post4372126](http://ubuntuforums.org/showthread.php?p=4372126#post4372126)

Peace

---

