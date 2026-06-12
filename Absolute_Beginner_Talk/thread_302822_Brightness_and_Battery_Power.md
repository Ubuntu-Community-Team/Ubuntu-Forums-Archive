---
title: "Brightness and Battery Power"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by cytutchi on 2006-11-19
Hi there people...
i m trying to find out some problems that i have with my dapper kubuntu!

1. Firstly i cant seem to manipulate the Brightness of my laptop and is driving me blind! :)
i have a Sony vaio with nvdia card!
I have installed the drivers for the nvdia but the smartdimmer still does not work!!!

2. Second of all the battery lasts only 5 minutes with linux...why doesn't it last longer?

Thenx a lot to everybody that would take the time to help me a bit! ;)

chiers

---

### Post by ahaslam on 2006-11-19
Hi, I'm not sure about your brightness problem, I'm on Dapper & the keyboard shortcuts work for that.
However regarding battery life in general, you may want to enable laptop-mode. To do this you'll need to edit a config file, so:
**sudo nano /etc/default/acpi-support**
and add/change: ENABLE_LAPTOP_MODE = **true**
Then you'll want to set it up for better battery life:
**/etc/laptop-mode/laptop-mode.conf**
and set it up something like this: **[ATTACH]19619[/ATTACH]**
Doing this gave me a 10% increase in battery life, let's hope it does more for you ;)
Please note that this is assuming the required components are installed on Edgy by default. If you have problems, I'll list what power related stuff I have installed.

Good luck,

Tony.

---

### Post by obavjestenja on 2006-11-19
im changing brightness  on my LG laptop FN+CTRL+HOME or FN+CTRL+eEND

---

### Post by cytutchi on 2006-11-20
Firstly thenx for the replies guys...

>>>>>Please note that this is assuming the required components are installed on Edgy by default.<<<<<

Edgy...but we are talking for Dapper! did you mean Dapper or really you ment Edgy? Anyway i'll have a look about that...but could you plz tell me if you did all these with KUBUNTU DAPPER?

as for the Ctrl+Fn+HOME or END ...i wish it worked!!it didnt!

i ve'read in some forums something about the smartdimmer that i had to enable it but it was a 4 pages thing and i was getting lost in it...maybe anoybody else any sugestion?...

---

### Post by xyz on 2006-11-20
[Adjust brightness on Sony Vaio]("http://ubuntuforums.org/showthread.php?t=88611")
I'll post this one just in case someone consulting this thread has a Toshiba laptop, run as root:
```
echo "brightness: 7" > /proc/acpi/toshiba/lcd
```
where "7" is the number you may want to change.

Did this disappear in Edgy?
System > Preferences > Power Management

---

### Post by ahaslam on 2006-11-20
> **cytutchi said:**
> Edgy...but we are talking for Dapper! did you mean Dapper or really you ment Edgy? Anyway i'll have a look about that...but could you plz tell me if you did all these with KUBUNTU DAPPER?

What I said is what I meant. I obviously didn't read your post properly though, I went by your profile '*6.10 Edgy User*'.

To clarify, I did this with Dapper ;)

Tony.

---

### Post by cytutchi on 2006-11-21
well...you were right Antony...
my profile says edgy but i went back to dapper again cause i think they are more stable..just cahnged the prof. again!
As for your advice i did what you said to enable_laptop=true but nop..it didnt work for me...
also i tried comparin the file you sent me and it is the same so i didnt had to change smthing...

do you have nvdia?if yes apart from installing the drivers did you have to do as well anything else like activating smthing or ...installing another packet???

from another forum the answer was smartdimmer but...the number changes but not the actuall brightness!

Thenx again...community! ;)

---

