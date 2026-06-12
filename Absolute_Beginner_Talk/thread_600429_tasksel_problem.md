---
title: "tasksel problem"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Circus-Killer on 2007-11-02
hey there.

okay, i used tasksel to install a lamp server, which ran almost perfectly. the only problem is that the installation halted at the end, and i had to manually kill off the tasksel processes.

after that, everything regarding the lamp server and the rest of my system works perfectly.

the only problem i am having, is that whenever i now try use tasksel to install ubuntustudio-audio, i get an error "aptitude: error 100" or something to that effect.

i was wondering if anyone knows the problem to this solution? am i required to first install ubuntustudio-desktop first? please help.
the reason why i am only trying to install ubuntustudio-audio is that i only want the audio applications, with no real need for the rest.

i dont know, any suggestions? (before i lose my mind and try install the whole of ubuntustudio)
thanks in advance.

---

### Post by Circus-Killer on 2007-11-02
*bump*

---

### Post by louieb on 2007-11-02
```
sudo dpkg --configure -a
```

From this thread [http://ubuntuforums.org/showthread.php?t=565837](http://ubuntuforums.org/showthread.php?t=565837)

---

### Post by Circus-Killer on 2007-11-05
thanks for the suggestion.
unfortunetaly, i am at work at the moment, so i will have to try out the suggestion when i get home tonight.
will report back once i've tried it out.

---

