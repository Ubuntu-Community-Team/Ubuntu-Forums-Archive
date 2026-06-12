---
title: "login error (gnome crashed)"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by usater on 2008-01-29
Hai, friends

i' using ubuntu 7.10:guitar:

i've installed wine and winrar via wine:popcorn:

then i tried to unrar a 700mb file twice:) 

after that i got a message that no free disk space.:(

then when i restarted the system......Opps :( the Gui is not loading

and got some error related to .ICEauthority.

Crash report said cannot login as there is no disk  space,but terminal login is possible

then i removed wine and it's folder(~\.wine)

then i successfuly get gui login.

i tried one more wine installtion in gui:cry:

after reboot the same message repeat n stopping me from gui login:confused:

after that on gui login the same error begin to come

i removed wine n tried but i cann't login via gui    :mad:

my" / " is done on a 5.9gb partition and /home is done on a 4.7gb partition

when the problem starts there was 1.7gb free on /home n2.5gb free on " / " 

:why the message came that the disk do not posses free space anymore


please help me

thanks in advance

---

### Post by XplOzIOn on 2008-01-29
Hi there, why would you need winrar?

Maybe there something wrong with winrar and wine. i have never tried that

Just install rar and unrar from repositories

```
gksudo apt-get install rar unrar
```

Remember to have backports and extra repos active ;)

//Hope it helps

---

### Post by usater on 2008-01-29
ya i do have Unrar with me but it take much more time 

it is not detecting CRC error

one Rar file i've dnlded was contained a CRC error the linux archiver continuously asked for passwd

but archive was not locked when i tried the winrar i got the correct problem

---

