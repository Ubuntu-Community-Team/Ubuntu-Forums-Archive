---
title: "[ask]Does this command should work in crontab ?"
date: 2008-04-13
forum: Absolute Beginner Talk
---

### Post by jualansandal on 2008-04-13
the command is:
```

gnome-terminal -x bash /home/hqpos/Kettle-3.0.2/kitchen.sh -rep="hqpos rep" -user=user -pass=pass -job="Kettle Job"      

```
I just want the script(kitchen.sh) to be executed in console so I could see the process log.

thanks

---

### Post by Oldsoldier2003 on 2008-04-13
> **jualansandal said:**
> the command is:
```

gnome-terminal -x bash /home/hqpos/Kettle-3.0.2/kitchen.sh -rep="SION hqpos" -user=user -pass=pass -job="Kettle Job"      

```
thanks

you shouldn't need  " gnome-terminal -x bash"

---

### Post by jualansandal on 2008-04-13
ok, it runs well without the " gnome-terminal -x bash"
but the terminal is not showing up, and I would like to see the job(process)'s logs.

thanks

---

### Post by scxtt on 2008-04-13
try redirecting the output to a file ...

bash /home/hqpos/Kettle-3.0.2/kitchen.sh -rep="SION hqpos" -user=user -pass=pass -job="Kettle Job" [color=green]**2>&1 >> /home/hqpos/Kettle-3.0.2/kitchen.sh_out**[/color]

then view the home/hqpos/Kettle-3.0.2/kitchen.sh_out file.

---

### Post by jualansandal on 2008-04-13
> **scxtt said:**
> try redirecting the output to a file ...

bash /home/hqpos/Kettle-3.0.2/kitchen.sh -rep="SION hqpos" -user=user -pass=pass -job="Kettle Job" [color=green]**2>&1 >> /home/hqpos/Kettle-3.0.2/kitchen.sh_out**[/color]

then view the home/hqpos/Kettle-3.0.2/kitchen.sh_out file.

ok, this works. But could we add the file with the date(when it is created) ?
thanks

---

### Post by Oldsoldier2003 on 2008-04-13
> **jualansandal said:**
> ok, this works. But could we add the file with the date(when it is created) ?
thanks

```
bash /home/hqpos/Kettle-3.0.2/kitchen.sh -rep="SION hqpos" -user=user -pass=pass -job="Kettle Job" 2>&1 >> /home/hqpos/Kettle-3.0.2/kitchen`date +%Y%m%d%H%M%S`.sh_out
``` should insert the date and time into the filename

---

### Post by jualansandal on 2008-04-13
is it ** '**  or ** ` **

but can't I show the console in cronjob, maybe it is better to look the log at that time. thanks

---

### Post by jualansandal on 2008-04-14
> **Oldsoldier2003 said:**
> ```
bash /home/hqpos/Kettle-3.0.2/kitchen.sh -rep="SION hqpos" -user=user -pass=pass -job="Kettle Job" 2>&1 >> /home/hqpos/Kettle-3.0.2/kitchen`date +%Y%m%d%H%M%S`.sh_out
``` should insert the date and time into the filename

It does not work.
anything wrong ?

---

### Post by jualansandal on 2008-04-14
anyone knows ?

---

