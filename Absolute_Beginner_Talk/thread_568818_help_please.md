---
title: "help please"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by savasalim on 2007-10-06
Hello

This is my first post and am a newby to Linux

I have installed program from cd.... all looked well and saked to reboot

so i did...when its starting without the cd it comes up with this error

FAILED TO START X SERVER (your graphical Interfacee)
Yould you like to diagnose problem?


if i press YES or NO it coes to dos promp and asks me to enter user and password which i do then it goes to  ******@****-desktop: ~$

no matter hat i do cant get it to start

do i need to enter a comand to start program or is the instalation faulty?

Could anyone advise please

and sorry if this question has been asked as i could not find an answer


Savas

---

### Post by drinkpepsi on 2007-10-06
At the prompt type

```
dpkg-reconfigure xserver-xorg
```

Just FYI, I typed

failed to start x server

 in the search box and got many pages of posts with the same issue, so if the above doesn't work try typing it in the search and you'll come up with many pages of similar posts.

---

### Post by Sef on 2007-10-06
```
dpkg-reconfigure xserver-xorg
```

If that does not work, do this:

```
suho dpkg-reconfigure xserver-xorg
```

If that does not work, then post your specs including video card and version plus type of Ubuntu.

---

### Post by Vixis on 2007-10-06
> **Sef said:**
> 

```
suho dpkg-reconfigure xserver-xorg
```



must be:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Sbarton on 2007-10-06
Sef: did you mean 'sudo'and not 'suho'?
```
suho dpkg-reconfigure xserver-xorg
```
regards

---

### Post by om1 on 2007-10-06
Sef said it all
just to make it quicker and easier to receive help in the future ... post your specs and use a more descriptive title
and yes Sef mint sudo

---

### Post by PmDematagoda on 2007-10-06
> **Sbarton said:**
> Sef: did you mean 'sudo'and not 'suho'?
```
suho dpkg-reconfigure xserver-xorg
```
regards

Isn't that obvious? Unless ofcourse you make a shell of your own which uses the command suho:)

---

### Post by Sbarton on 2007-10-08
PmDematagoda,* Quote: Isn't that obvious?*. The OP 'savasalim' states their status as newbie to linux, so it may not be as 'obvious' as it is to others. :). Also though I have been using Ubuntu linux  for a while there are still an emormous amount of command words I have not yet come across, though sudo isn't one of them.
regards

---

### Post by PmDematagoda on 2007-10-08
> **Sbarton said:**
> PmDematagoda,* Quote: Isn't that obvious?*. The OP 'savasalim' states their status as newbie to linux, so it may not be as 'obvious' as it is to others. :). Also though I have been using Ubuntu linux  for a while there are still an emormous amount of command words I have not yet come across, though sudo isn't one of them.
regards

Point made:).

---

