---
title: "problem logging in my gutsy"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by pranayjha on 2008-01-02
hi.....
please someone help me..... i cannt log in my ubuntu gutsy....
i am getting an error telling that " cannt lock /.ICEauthority "...
i tried changing the ownership.... but its not working....
i did it by running in recovery mode..... there i tried to change the ownership.... i also tried it on safe mode terminal....
please help me if u have a solution.........

---

### Post by PriceChild on 2008-01-02
This is caused by [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

I suggest booting up into single user mode (second option on grub) and removing that file via the command line
[FONT=monospace]```
[/FONT]rm /home/your_username/.ICEauthority
```

---

### Post by llamakc on 2008-01-02
```

chmod 600 /home/USERNAME/.ICEauthority

```should make it look like this:

```

-rw------- 1 USERNAME USERNAME 15K 2007-12-31 13:32 .ICEauthority

```...do this from the safe mode terminal.

SEE the 'rm' suggestion above.

---

