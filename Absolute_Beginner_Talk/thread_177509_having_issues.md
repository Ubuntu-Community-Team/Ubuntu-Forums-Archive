---
title: "having issues"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by kkm64 on 2006-05-16
am new to ubuntu and am frustrating my husband to no end with questions. Does anyone have a few moments? How can I install gnome as the default desktop? Why can't I get kmymoney to save files? ](*,)

---

### Post by meng on 2006-05-16
Erm, GNOME should already be the default desktop for Ubuntu. Have you installed Kubuntu or Xubuntu? What is your default desktop now, if not GNOME?

Oh, btw, thanks for frustrating us with your problems instead. :p Just kidding. I'm sure that coming here will be better for marital harmony. :o

---

### Post by nalmeth on 2006-05-16
No problem. Did he refer you here in response to frustration? Good then, you'll get a lot more help I'm sure.

Was ubuntu installed with KDE as the default? Kubuntu rather? Or is gnome actually installed already? You can select it in the Display Manager, and choose it as default for your user.

If it's not, open up a terminal
Kmenu / System / Konsole

and type 
sudo apt-get install ubuntu-desktop

then log into gnome from Display Manager.

Can you be more specific with kmymoney problem?

---

### Post by Dr. Nick on 2006-05-16
[quote=kkm64]am new to ubuntu and am frustrating my husband to no end with questions. Does anyone have a few moments? How can I install gnome as the default desktop? Why can't I get kmymoney to save files? ](*,)[/quote]

If you have gnome ntalled and kde then just change our session type to gnome on the login screen and it should ask if you want it default. If you have just kde and want gnome installed then the easiest way would be to run

sudo apt-get install ubuntu-desktop

---

