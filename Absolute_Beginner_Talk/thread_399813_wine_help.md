---
title: "wine help"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Vitaminc23456 on 2007-04-02
well, ive been trying to get wine to work on my computer, and ive done everything the website has told me to do, it told me how to install it and i thought i had done it the right way, but it doesnt show up anywhere, i figure im doing something wrong, so im asking for help on how to get this thing to work.

---

### Post by ajmorris on 2007-04-02
> **Vitaminc23456 said:**
> well, ive been trying to get wine to work on my computer, and ive done everything the website has told me to do, it told me how to install it and i thought i had done it the right way, but it doesnt show up anywhere, i figure im doing something wrong, so im asking for help on how to get this thing to work.

Did you use the repositories method, whereby you add the repositories to you /etc/apt/sources.list file and then download through apt-get, aptitude or synaptic (or another package manager)?

---

### Post by Vitaminc23456 on 2007-04-02
i believe so, thats the one where you have to allow it and then you have to put something in the terminal right? if so i did that

---

### Post by JNowka on 2007-04-02
First discover what version of Ubuntu you have.  Dapper or Edgy.  

If you have Dapper use the following:
> 
[I]wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
[/I][I]
sudo apt-key add 387EE263.gpg
[/I][I]
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list](http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list) -O /etc/apt/sources.list.d/winehq.list[/I]


If you have Edgy:
> 
[I]wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg)
[/I][I]
sudo apt-key add 387EE263.gpg
[/I]*sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list](http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/winehq.list* 


This should enable wine in your repositories.  Next you install wine.

To Install:
> 
sudo aptitude install wine


Hope this helps

---

### Post by Maestro23 on 2007-04-02
Wine wiki: [https://help.ubuntu.com/community/Wine?highlight=%28wine%29](https://help.ubuntu.com/community/Wine?highlight=%28wine%29)

---

### Post by david_kt on 2007-04-02
> **Vitaminc23456 said:**
>  but it doesnt show up anywhere.

What do you mean by "show up"? You will not see wine anywhere, just open terminal, and type wine.

DK

---

