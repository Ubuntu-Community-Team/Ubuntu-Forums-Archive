---
title: "cddb error in k3b"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by crispy_420 on 2006-10-06
Does anyone know how to fix an error I get in k3b when I try to get cddb.

It happens when I try to "Querry CDDB" and comes up as a communication error. I think it is that I have my source (my freedb.org?) messed up but how do I fix it?

---

### Post by crispy_420 on 2006-12-14
I posted this quite a bit ago just trying again to see if anyone can help.

I just want to be able to have the text for artist/song added to backup CDs so they are displayed in my car. I know it works and is possible cause Nero/Windows does it.

Do I just need to do a simple adjustment in preferences or what?

Anyone?

---

### Post by Sef on 2006-12-14
Have you checked or asked about your problem in the [freecddb forums]("http://www.freedb.org/en/forum/list.php?1")?

---

### Post by stmiller on 2006-12-16
Remove the freedb entry in the K3B prefs and put in this one:

freedb.freedb.org

---

### Post by jeremy on 2007-01-07
> **stmiller said:**
> Remove the freedb entry in the K3B prefs and put in this one:

freedb.freedb.org

No, doesn't work.

---

### Post by jeremy on 2007-01-07
I have found it:

Remove the freedb entry in the K3B prefs and put in:
freedb2.org
(http, port 80)

---

### Post by crispy_420 on 2007-01-08
Thanks for the response, I'll try it out when I get some other issues resolved.

---

### Post by mslonik on 2007-01-20
jeremy: Thanks, now k3b lookup for cddb works fine again! Your suggestion to add freedb2.org works!

Kind regards,
Maciej (mslonik)

---

