---
title: "Evms Accidental Install"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by itsvan on 2008-02-20
HELLO EVERYONE, I WILL OPEN UP BY SAYING IM RATHER NEW AT UBUNTU (NOOB)
FOR SOME GOD AWFUL REASON I ACCIDENTALY INSTALLED EVMS,(thinking it was something else)
AND AFTER THE REBOOT IT WILL NOT LET ME LOGIN INTO ANYTHING,NOR ANY FAIL SAFE SESSION,,,WHAT CAN I DO TO UNINSTALL EVMS? AND GO BACK TO UBUNTU,,WHAT REALLY INTERESTS ME IS IN NOT LOSING ALL OF MY DATA....PLEASE SOMEONE HELP ME......thank you very much

---

### Post by jan quark on 2008-02-20
hmm ...

Try to select recovery mode during the booting session.

I think you must press escape during the grub loader loads.

Then you should boot into a text mode session.

Try to run this command:

```

sudo apt-get remove --purge evms libevms-2.5
```

---

### Post by mkoehler on 2008-02-20
Even if you boot into the standard mode, you can still hit CTRL+ALT+F1 to bring up your tty1 prompt.  From there, you can log in and carry out the same commands that jan quark suggested.

---

### Post by itsvan on 2008-02-21
thanks for the reply,,,one thing when i go into the recovery mode,,a ridiculously long numbering list starts going off,,and i don't know if thats normal,,or if its searching over and over for something thats not there...what could it be?

---

### Post by itsvan on 2008-02-21
YOO THANKS ALOT GUYS,,,IT WORKED ,,,,i appreciate it greatly that u took the time to help,,,UBUNTU IS THE ****......A BILLION THANKS...PEACE OUT!!!!!!!!!!!!:guitar:

---

