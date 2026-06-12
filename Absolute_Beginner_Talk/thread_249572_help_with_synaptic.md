---
title: "help with synaptic"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by knutsack on 2006-09-02
Okay I am completely stupid when it comes to linux and Ubuntu, but I am slowly learning. I was attempting to play around with WINE for Ubuntu, and well it didn't work (thats not what my problem is). Now I am assuming I did something stupid and I am getting a message in synaptic 
"E: Type 'http://wine.budgetdedicated.com/apt' is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem."

does anyone know what this is?
Please help if you can.

thanks

---

### Post by knutsack on 2006-09-02
Okay... the porblem will not let me use the add/delete programs either...

Please help if you can...

---

### Post by bulldog on 2006-09-02
There is a line in your sources.list that not should be there.
Do:
gksudo gedit /etc/apt/sources.list

and go to the line ''http://wine.budgetdedicated.com/apt" and comment it out
[that is put ## in front of it]
If there are more errors do the same untill your sources.list is correct again.

---

### Post by knutsack on 2006-09-02
Thank you

that worked...

---

### Post by bulldog on 2006-09-02
You could erase the line(s) that are wrong if you prefer.
But as long as you have them commented out they will not be used by aptitude.

Glad to be of some help to you.

---

