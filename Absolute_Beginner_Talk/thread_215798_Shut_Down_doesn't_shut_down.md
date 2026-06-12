---
title: "Shut Down doesn't shut down?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by Uncle Spellbinder on 2006-07-14
When I click *Quit > Shut Down*, Dapper stops, the monitor shuts off but the computer remains on and I must shut it off manually. am I missing something?

---

### Post by wildseven on 2006-07-14
im new too, but i had this problem before. I fixed the shutdown, but the reboot hangs...ehhh lol, I can live with only shutdown for now. Any-who
What I did was...
```
$: sudo gedit /etc/gdm/gdm.conf 
```

I searched the line that said:
```
 AlwaysRestartServer=false 
```
Then I un-hashed it and made it:
```
 AlwaysRestartServer=true 
```

hopefully that works for you too^^

---

