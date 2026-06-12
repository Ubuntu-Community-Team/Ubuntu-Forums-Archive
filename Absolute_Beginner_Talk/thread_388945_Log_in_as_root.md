---
title: "Log in as root"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by wehttamb on 2007-03-20
Hi

How can i enable loging into the root user. I know it is dangerous and stuff but i really need to log into it. I am trying to install a cross compiler but even when i run the comand as sudo i still get a permision denied error. I have installed it on other distrobutions of linux when i was actually logged in as root. 

Thanks

wehttamb

---

### Post by Bachstelze on 2007-03-20
*sudo -i* will simulate an initial root login (i.e. ive you a root shell).

---

### Post by Kateikyoushi on 2007-03-20
Try sudo su, does that work ? Or you can try in recovery mode.

---

### Post by justleen on 2007-03-20
```
sudo passwd root

``` will enable you to set a passwd for root..

---

### Post by Bachstelze on 2007-03-20
Don't do that.

---

### Post by wehttamb on 2007-03-20
I still get the same error. I am trying to install arm-uclinux-elf-tools but it just wont let me!!!

HELP!

---

### Post by wehttamb on 2007-03-20
why not

---

### Post by Bachstelze on 2007-03-20
That doesn't help us much... What is the command you type and what error do you het ?


Because you don't need it so it's increasing security risk uselessly.

---

### Post by wehttamb on 2007-03-20
```
wehttamb@wehttamb-desktop:~/Desktop/iPod_Linux$ sudo su
root@wehttamb-desktop:/home/wehttamb/Desktop/iPod_Linux# ./arm-uclinux-elf-tools-base-gcc3.4.3-20050722.sh
bash: ./arm-uclinux-elf-tools-base-gcc3.4.3-20050722.sh: Permission denied
root@wehttamb-desktop:/home/wehttamb/Desktop/iPod_Linux# 

```

i tried the other thing and when it tried to log in at root it said "system administrator is not allowed to log in from this screen"

---

### Post by Bachstelze on 2007-03-20
Is the file executable ?

```
ls -l arm-uclinux-elf-tools-base-gcc3.4.3-20050722.sh
```

---

### Post by wehttamb on 2007-03-20
```
root@wehttamb-desktop:/home/wehttamb/Desktop/iPod_Linux# ls -l arm-uclinux-elf-tools-base-gcc3.4.3-20050722.sh
-rw-r--r-- 1 wehttamb wehttamb 30762799 2007-03-14 07:28 arm-uclinux-elf-tools-base-gcc3.4.3-20050722.sh
root@wehttamb-desktop:/home/wehttamb/Desktop/iPod_Linux# 

```

---

### Post by wehttamb on 2007-03-20
I found that it wasnt executable!!!!!

It is now installing 

Thanks:popcorn:

---

### Post by wehttamb on 2007-03-20
Ok i installed the program ok 
but now it isnt there. when i ran the makefile that uses it it just came up with an error saying
```
wehttamb@wehttamb-desktop:~/tools/hotdog$ make IPOD=1
mkdir ipod
arm-uclinux-elf-gcc  -DIPOD -I./libs/libpng -I./libs/libjpeg -I./libs/zlib -O3 -funroll-loops -Wall -c -o ipod/hotdog.o hotdog.c
make: arm-uclinux-elf-gcc: Command not found
make: *** [ipod/hotdog.o] Error 127

```

why is this 
when i used it in pclinuxos (when i instaled through root) it just worked what is wrong now?

---

