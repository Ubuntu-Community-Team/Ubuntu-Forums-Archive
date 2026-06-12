---
title: "[SOLVED] config. Deluge ok"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-21
ok so i have deluge set up and when i download stuff it is really slow like on .5 kib/ sec and b4 when i use to download on windows i had like 300+/sec i dont know what the prob is the port that deluge is using is 

6881-6889

so on my router i have port forwarding to 6881 on TCP and UDP

here a screen shot [http://tinypic.com/view.php?pic=29m108n&s=3](http://tinypic.com/view.php?pic=29m108n&s=3)

is there anything i need to do or tips in deluge i should clcik

---

### Post by freelinuxhelp on 2008-02-21
Do you have the entire range forwarded, or just 6881? 
If just 6881, try forwarding the  entire range.

---

### Post by sisco311 on 2008-02-21
test your port forwarding:

go to Deluge -> Preferences -> Network and press Test Active Port button

---

### Post by articwolf939 on 2008-02-21
i forwarded all port and did test it and it wasnt able to go through

---

### Post by sisco311 on 2008-02-21
try again the port forwarding setup:

Name: deluge
TCP: 6881-6889
Schedule: Always

IP Address: <your ip address>
UDP: 6881-6889
Inbound Filter: Allow All

save the settings
test it again. if don't work try to restart your rooter.

to get your ip address open a terminal and type:
```
ifconfig eth0
```

---

### Post by articwolf939 on 2008-02-22
well ive tried everything they gave all said it still dosent work my upload speed is good lik 20k/sec but download is still .6k/sec any1 else have ideas?

---

### Post by articwolf939 on 2008-02-22
ok wow i figgred it out i feel VERY dumb i put the max upload at 1.0k/sec and didnt realize it DUH me

---

