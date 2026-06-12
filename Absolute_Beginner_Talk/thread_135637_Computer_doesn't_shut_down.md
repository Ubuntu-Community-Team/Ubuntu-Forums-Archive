---
title: "Computer doesn't shut down"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2006-02-24
My computer doesn't like to shut down.  It will hang up at the end on powering down.

---

### Post by pbaehr on 2006-02-24
Can you be more specific?

What is the last thing it displays before it hangs?

Or is it just not shutting the power off on the computer (in which case it is an APM (advanced power management) issue).

---

### Post by inovermyheadd on 2006-02-25
everything is sent a terminate...then it says...

"power down computer"

then it just doesn't turn off...I guess this is an APM like you said.  Is this fixable?

thanks for the reply btw.

---

### Post by az on 2006-02-25
In your bios, what power management setting do you have (none, apm, acpi, both) and what is it set to?

---

### Post by fuscia on 2006-02-25
have you tried *sudo shutdown -h now*?

---

### Post by inovermyheadd on 2006-02-25
hey, I have no clue how to find out my bios...

but sudo shutdown -h now worked perfectly...

thanks a lot to both of you!:)

---

### Post by thomashauk on 2006-02-25
Its normally the first thing you see when starting the computer. Press normally you F2 or Del (or some other random button) to veiw and change settings.

---

