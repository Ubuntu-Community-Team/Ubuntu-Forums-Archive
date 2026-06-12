---
title: "forgot user name.!!  pls help"
date: 2006-08-11
forum: Absolute Beginner Talk
---

### Post by mcnn on 2006-08-11
I know this is lame, but I just installed ubuntu 6.06 on a second drive (also just instaslled) and I remember my password.but can't remember my user name!  where can I find it.or what should I do? I have tried this dist from live cd and love it. Ican't wait to use it more.I guess I will have to become a geek now, but in the meantime...pls help.??:confused:

---

### Post by jordilin on 2006-08-11
Do 
```
cat /etc/passwd
```
and take a look at what you get!!
Your username should appear there

---

### Post by Dr. Nick on 2006-08-11
reboot and choose "recovery mode" or whatever recovery from the grub screen, once thier do 

cd /home

then

ls

cd /home will take you to the home directory, and ls will list the folders in the home dir. It should have the folder of your user name

---

### Post by mcnn on 2006-08-11
thanks guys for your quick replies. As you can see, I am also very new to forums as well. After my post I saw the exact same problem from yesterday.with solutions. 
My problem is .you both use the word "do".!!
I really don't know how you mean that. anyway, when I reboot in recovery mode and "do' "cd/home"..it says "no such file or directory"
and I have no idea where to "do" "Code:
cat/etc/passwd"
please be a litle more specific. I know you linux guys are a lot more savy than us casual users.(esp the ugh windows world)
please make believe I am as dumb as a computer.....give me every line of code (instructions)
assume I know nothing (almost true)
thanks again.I am eegerly looking forward to exploring ubuntu linux
sincerely,
mike

---

### Post by jordilin on 2006-08-11
> **mcnn said:**
> thanks guys for your quick replies. As you can see, I am also very new to forums as well. After my post I saw the exact same problem from yesterday.with solutions. 
My problem is .you both use the word "do".!!
I really don't know how you mean that. anyway, when I reboot in recovery mode and "do' "cd/home"..it says "no such file or directory"
and I have no idea where to "do" "Code:
cat/etc/passwd"
please be a litle more specific. I know you linux guys are a lot more savy than us casual users.(esp the ugh windows world)
please make believe I am as dumb as a computer.....give me every line of code (instructions)
assume I know nothing (almost true)
thanks again.I am eegerly looking forward to exploring ubuntu linux
sincerely,
mike
be aware, there's a blank space between cd and home, it's
```
cd /home
```
then 
```
ls -l
```
and you'll get your username
When I say do, I say write down the instructions in a terminal and press intro.

---

### Post by Ptero-4 on 2006-08-11
Once you enter the recovery console mode. What you need to type is this:
```
cd /home
```

This will switch from whichever folder the console puts you in to the folder called "home" in the root of the drive. Then type this:

```
ls
```

This will display the contents of the /home folder, the contents of that folder are the "home" folders of every user in your box. Since you probably have only one user (your username), just use the name of the folder you'll see in the contents listing to log in.

---

### Post by kinematic on 2006-08-11
](*,)  ](*,)  ](*,)

---

### Post by mcnn on 2006-08-11
ok, I finally got into the "home' directory
it says "home#" and flashing cursor
I entered "ls" (small 'l',small 's')
next line returns "oem"......in blue letters
and then "home#" again
then I entered "ls -l" as told (l,s,space,minus sign,l)
it returns:
"total 4"
"drwxr-xr-x 2 oem oem 4096 Aug 11 08:31 oem (oem in blue letters)

more confused than ever.

maybe I should just reinstall it all over again...and pay attention this time.!

whatta ya think.??
-mike

ps, thanks kinematic, my forhead IS getting a little sore... : )

---

### Post by jordilin on 2006-08-11
> **mcnn said:**
> ok, I finally got into the "home' directory
it says "home#" and flashing cursor
I entered "ls" (small 'l',small 's')
next line returns "oem"......in blue letters
and then "home#" again
then I entered "ls -l" as told (l,s,space,minus sign,l)
it returns:
"total 4"
"drwxr-xr-x 2 oem oem 4096 Aug 11 08:31 oem (oem in blue letters)

more confused than ever.

maybe I should just reinstall it all over again...and pay attention this time.!

whatta ya think.??
-mike

ps, thanks kinematic, my forhead IS getting a little sore... : )

Yes, perhaps you'll solve this quickly if you install the Ubuntu OS again. And write down your username and password, just in case :mrgreen:

---

### Post by msak007 on 2006-08-11
All folders in the home directory belong to a user - did you name your user "oem"?

---

