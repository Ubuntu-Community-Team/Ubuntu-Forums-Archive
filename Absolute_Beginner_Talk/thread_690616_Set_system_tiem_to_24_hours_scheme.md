---
title: "Set system tiem to 24 hours scheme"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by D0Z on 2008-02-07
I like my Ubuntu in English although i am from Europe, where we use the 24 hours scheme. I could set this up for the clock in the panel, but other programs and the time displayed at the login screen still use the AM-PM scheme. How do i get this right for me?

---

### Post by D0Z on 2008-02-07
Someone?

---

### Post by seventhc on 2008-02-07
Please be more specific..as in what other programs?:)

---

### Post by G. Cotgreave on 2008-02-07
you can try to set 24 hour scheme while you are logged on as root but i am not sure it will work...

---

### Post by jw5801 on 2008-02-07
To change it at the login screen you can have a look in ```
gksu gdmsetup
``` I think there should be an option in there. As for the other programs, it depends how they access the time. System time is the time as set in your bios, it's always in 24-hour time there, it's just a matter of how different applications choose to show it.

---

### Post by D0Z on 2008-02-07
Login screen is already fixed, but it keeps returning in Pidgin and Evolution. And how can i do that G. Cotgreave?

---

### Post by D0Z on 2008-02-08
Anyone?

---

### Post by forestpixie on 2008-02-08
setting the calendar time to 24 hr in evolution might work for that - edit>preferences>calendar and tasks

not sure about pidgin - don't do that whole thing :)

---

### Post by jw5801 on 2008-02-08
Whereabouts in Pidgin is the time displayed incorrectly?

---

### Post by D0Z on 2008-02-09
Evolution is already set to 24 hours, but still displaying time in AM PM style.  In pidgin i mean the time displayed in chat screens, before the line you typed or recieved. Like this:

(04:44:18 PM) Borat: he
(04:44:19 PM) Pamela Andersons: he

---

### Post by jw5801 on 2008-02-09
For pidgin, there's a plugin (tools > plugins) called "Message Timestamp Formats" which allows you to force 24hour time on your timestamps.

---

### Post by D0Z on 2008-02-09
Ok that is working, now the same for Evolution..

---

### Post by D0Z on 2008-02-11
Anyone?

---

