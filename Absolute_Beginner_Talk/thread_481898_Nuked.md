---
title: "Nuked"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Gigzaholic on 2007-06-23
So I think I have nuked my installation. So, since I installed thunderbird, I thought that i should delete evolution. I went into synaptic and CTRL+F'd evolution. I accidentally selected all the search results for installation. Later, I decided to remove them and everything that had a reference to evolution in both the file name and description.

Apparently, I had removed gnome-terminal. I have however managed to reinstall it. My problem now is that whenever I click on the trash bin it doesn't open. I think I have messed up gnome :( How do I fix this? thanks.

---

### Post by maddot on 2007-06-23
would it be possible to just reinstall ubuntu?

---

### Post by irish_flu on 2007-06-23
You might try a reinstall of the package called "ubuntu-desktop".

That package "depends on" all the other necessary packages, and should offer to install them as well.

---

### Post by Gigzaholic on 2007-06-23
I don't have access to my computer right now but tomorrow I will definitely try your suggestions.

Also, if you guys have more suggestions please post them. Thanks.

---

### Post by swoll1980 on 2007-06-23
go to / see if there is a file called /trash if not just replace it

---

### Post by Malta paul on 2007-06-23
Hi, you could take a look at: System>administration>synaptic package manager,  'sections'
go to 'GNOME desktop environment', then 'mark for installation'
evolution-common
evolution-data server
evolution-data server-common
evolution-exchange
evolution-plugins
evolution-webcal
Hope this is of help to you :)

---

### Post by Inxsible on 2007-06-23
Removing Evolution does remove ubuntu-desktop, but it does not remove the terminal. I know because i removed evolution (along with a host of other pre-installed apps that i dont use)


You just have to read carefully as to what packages it suggests that it will remove and make the appropriate choices.

---

### Post by Gigzaholic on 2007-06-23
> **irish_flu said:**
> You might try a reinstall of the package called "ubuntu-desktop".

That package "depends on" all the other necessary packages, and should offer to install them as well.

I actually tried what you said and what malta paul said. Thank God, my system is working fine now... even the trash bin lol. 

Thanks again fellas.

---

