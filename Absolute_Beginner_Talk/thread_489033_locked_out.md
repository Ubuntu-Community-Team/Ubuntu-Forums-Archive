---
title: "locked out"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by alanc on 2007-06-30
:p Hi.      I can not get into Ubuntu, i put in my username & password and it comes up: incorrect username &
            or password and it must be in the right case.  I know the username & password are correct and the
           letters are all in lower case. I have got into Ubuntu OK about 20 times or more, and now all of a 
            sudden its not working. Can someone please help me here, i was going so well with Ubuntu too.
                                                                     Regards    alanc:  :(

---

### Post by kvonb on 2007-06-30
Reboot, and at the GRUB menu screen select "Recovery Mode"  (I think it's called that, it is just below your normal selection).

You can then check your login name by looking in the /home folder, ie:

```
ls /home
```

If you don't see your username in there, then maybe you had your home partition on another drive/partition and that drive/partition is damaged or not mounted!

You can change your password byt typing:

```
passwd yourusername
```

Then reboot and see if it worked :)

---

### Post by alanc on 2007-06-30
:p  Hi.  I went in to recovery mode, but i could not find the home folder, and all i got at the end of all that
            writing was:  root@alan- desktop,so i don,t know where i went wrong, but could you give me a bit
            more help please.
                                                                  Regards    alanc:(

---

### Post by alanc on 2007-07-01
:p Hi.  I went into win.xp, and looked in my computer, and the second HDD  D: that i had Ubuntu installed on,
         is not showing up, could this have something to do with why i cannot log into Ubuntu.  I tried doing what
       you instucted me to do, but i got the same thing again.
                                                                        Regards    alanc  :(

---

### Post by kvonb on 2007-07-01
It won't show up under Windows as Windows refuses to acknowledge that anything but Windows exists!

Boot from your Ubuntu CD, then open a terminal and type:

```
sudo fdisk -l
```

Post the output on here please :)

---

### Post by alanc on 2007-07-01
:p Hi.   I booted up from my cd, and looked in everything i could find, i typed in what you said but
       could not get anything. What exactly is a terminal, i am a real beginner at this.
                                                    Regards     alanc:(

---

### Post by gothelin on 2007-07-01
Okay.  You know the command prompt in Windows?  You can basically think of the terminal in Ubuntu in the same way.  It lets you directly type commands into the system.  :)

---

### Post by alanc on 2007-07-03
:(  Thank-you,i will try that when i get my PC going again. It crashed,the hard drive i had ubuntu on,has
    completely had it,and the pc just keeps turning on & off.I,ve put it in the sick bay to get repaired, i don,t
   know how long that will take.
                                                       Regards   alanc:(

---

