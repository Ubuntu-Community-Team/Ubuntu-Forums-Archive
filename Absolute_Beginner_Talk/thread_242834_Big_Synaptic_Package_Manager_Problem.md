---
title: "Big Synaptic Package Manager Problem"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by ShadyTails on 2006-08-24
E: Type 'http://wine.budgetdedicated.com/apt' is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

I didnt know what it meant by respitory dialog so I tried going to the sources.list and editing it and I tried saving it and it said to check the permissions, so then i set it to root and it still says to check the permissions and wont let me save it. I was following what Wines website said too to install it!

---

### Post by Klaidas on 2006-08-24
The line in sources list is incorrect. Correct it, or remove it.
> sudo gedit /etc/apt/sources.list

---

### Post by ShadyTails on 2006-08-24
Ahhh Thankyou very much =D

---

### Post by goatflyer on 2006-08-24
First, you need to edit the file with super-user priviledge.

Open a terminal window and type
```

sudo gedit /etc/apt/sources.list

```

Next, scroll down to the part where you want to add the wine repository and make sure it looks like this:

```


## wine
deb http://wine.budgetdedicated.com/apt dapper main


```

Make sure the deb is there, and the spaces between apt and dapper and main.

Then exit the editor (yes save the file), and exit the terminal.

Now open System>Administration>Synaptic Package Manager and click Reload.  You should see no more warning messages.


For future reference, you can get to the repository dialog by selecting Settings>Repositories inside Synaptic.

---

### Post by ShadyTails on 2006-08-24
thankyou goatflyer, it was trying to download them but 2 of the 4 respitories for Wine wouldnt download. So maybe their network is having problems rightnow.

---

