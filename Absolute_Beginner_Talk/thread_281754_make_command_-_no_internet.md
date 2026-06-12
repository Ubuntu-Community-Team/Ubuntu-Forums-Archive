---
title: "make command - no internet"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by JanCoonen on 2006-10-21
Hey everybody,

In order to get my modem (USB speedtouch 330 Alcatel green) up and ready in Ubuntu, I've already tried some how-to's. None of them seem to work because I'm not able to use the "make"-command.

"sudo make" results in command not found.
"sudo apt-get install make", "sudo apt-get install build-essentials", ... tells me the packages can't be found. It seems I wants to look for the packages on the internet. This is not possible because there isn't a connection ....

What am I doing wrong? Any suggestions? Remember I'm a total Ubuntu newbie...

Cheers,
Jan.

---

### Post by IYY on 2006-10-21
Is your Ubuntu CD in the drive? The build-essential package is on the CD as well.

---

### Post by sumguy231 on 2006-10-21
If you still have the cd, build-essentials should be on it. Do:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essentials
```
Then you will have make.

---

### Post by taurus on 2006-10-21
> **sumguy231 said:**
> If you still have the cd, build-essentials should be on it. Do:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essentials
```
Then you will have make.

It's "build-essential" not "build-essentials"...

---

### Post by JanCoonen on 2006-10-21
Hey Guys,

Thanks for helping me out. Make works fine, did find it on the CD. Still got problems with getting the modem up and running ...

Gives a lot of errors when I compile ..

1. Is it necessary to change the firmware to get a modem running in Linux?
2. Which Linux books/tutorials/sites do you suggest to newbies? In my case it should be written very simple. 

Thanks,
Jan.

---

### Post by sumguy231 on 2006-10-21
> It's "build-essential" not "build-essentials"...
My mistake, I know the correct name, but I never actually *type* the correct name. :oops: I need to be more careful.

---

