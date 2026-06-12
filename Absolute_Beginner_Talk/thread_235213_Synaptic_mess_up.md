---
title: "Synaptic mess up"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by M+J on 2006-08-12
Being new to linux I try things that get me in trouble. I tryed to add wine in the sources list of synaptic (winhq.com) when I start synatic I get:
E: Malformed line 33 in source list /etc/apt/sources.list, soo I try in terminal: /etc/apt/sourecs.list and get bash:/etc/apt/sourecs.list permission denied. How do I correct this please.

---

### Post by Mac_D83 on 2006-08-12
The file /etc/apt/sources.list is owned by the administrator(root), so you need to open it with the right privileges. You can use the sudo command to temporarely get administrator priveleges. Use the command in conjunction with gedit to edit the file. First do a backup of the file by entering the following command in a console
```

$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.bakYearMonthHDay

```
Then edit the file with gedit
```

$ sudo gedit /etc/apt/sources.list

```
Now either correct line 33 or delete it. Save the file and you should be go to go.

Cheers
Michael Mc Donnell

---

### Post by M+J on 2006-08-13
Thank You Michael, It's working fine again.

---

