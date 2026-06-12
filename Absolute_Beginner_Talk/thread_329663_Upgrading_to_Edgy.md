---
title: "Upgrading to Edgy"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-01-02
Hey folks. I've decided to try Edgy, but I have some concerns . . .I have two physical hard drives. One is system-exclusive, and the other is media-exclusive. Dapper is on the system drive, and nothing on that drive is important to me . . .if I upgrade to Edgy, do I have to do anything to the second, mounted drive to protect it from being wiped or anything in the upgrade process?
Also, how do I upgrade? ~LOL~

---

### Post by h0ax on 2007-01-02
No - I don't think you should need to do anything in particular.  An upgrade shouldn't touch the 2nd drive.
here's how to update

follow the steps in this link:
[http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html](http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html)
I just did "Option 2" today, so I know it works=P
Make sure you backup /boot/grub/menu.lst if you are dual booting
good luck

---

### Post by CheshireMac on 2007-01-02
> **h0ax said:**
> No - I don't think you should need to do anything in particular.  An upgrade shouldn't touch the 2nd drive.
here's how to update

follow the steps in this link:
[http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html](http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html)
I just did "Option 2" today, so I know it works=P
Make sure you backup /boot/grub/menu.lst if you are dual booting
good luck

/boot/grub/menu.lst . . .what's that? Is it big? I don't have a lot of space left for backup right now, and I'm out of disks. ~LOL~

---

### Post by h0ax on 2007-01-02
nono small text-like file mines 5KB

---

### Post by CheshireMac on 2007-01-02
K, so how do I back it up so it's okay to upgrade?

---

### Post by h0ax on 2007-01-02
just create a copy of it - open a terminal then

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

easy as cake (:

---

### Post by CheshireMac on 2007-01-02
> **h0ax said:**
> just create a copy of it - open a terminal then

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

easy as cake (:

So do that, and then I can Apt=Get the upgrade, and there shouldn't be any concerns?

---

### Post by MkfIbK7a on 2007-01-02
yup no concerns since edgy isnt beta anymore you shjouldnt have any problems at all except for wireless issues

---

### Post by CheshireMac on 2007-01-02
Okay then . . .I'm going ahead with it . . .but now I've got an error . . .
mac@mac-desktop:~$ sudo sed -e ’s/\sdapper/ edgy/g’ -i /etc/apt/sources.list
Password:
sed: -e expression #1, char 1: unknown command: `
I'm taking the Apt-Get method in the link given above . . .I could use some help. ~LOL~ Thanks.

---

### Post by raul_ on 2007-01-02
```

sudo update-manager -c

```
And choose to upgrade

This is the official method

---

### Post by CheshireMac on 2007-01-02
Here we go . . .tell you how it works out tomorrow . . .I'm going to try and sleep, knowing that this is happening. ~LOL~ Might have nightmares . . .;)

---

### Post by mlissner on 2007-01-02
Hey, I just tried to follow the number two type directions above, and I screwed up the sed command and now I've lost a good copy of my sources.list file. Can somebody post theirs for me please?

Sorry for the idiocy...I thought I had sed down, but now I've confused myself...

---

### Post by Frak on 2007-01-02
> **wert613 said:**
> yup no concerns since edgy isnt beta anymore you shjouldnt have any problems at all except for wireless issues
sorry to go off subject, but why did the developers roll back drivers?  My card worked fine under Dapper, but isn't even recognized under Edgy? Maybe it'll work under Feisty?

---

