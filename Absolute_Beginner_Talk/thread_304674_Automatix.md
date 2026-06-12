---
title: "Automatix"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by captgadget on 2006-11-22
By mistake I installed Automatix for 6.1. Then I went back and installed Automatix for 6.06. Then I Synaptic I had to force downgrade 6.1 to 6.06 version. Now, it always gives me an automatic update to 6 .1. How  do I go about removing that so it doesn't always want to perform that software update?

---

### Post by steven8 on 2006-11-22
Mt first thought would be to remove it completely, then go back and get the one you wanted in the first place.

---

### Post by judgejudy on 2006-11-22
sudo apt-get remove automatix2 then

 echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main" | sudo tee -a /etc/apt/sources.list
 wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -  then

sudo apt-get update
sudo apt-get install automatix2

---

### Post by captgadget on 2006-11-23
It tells me it couldn't find package

---

### Post by Bachstelze on 2006-11-23
My advice is to remove Automatix completely before it breaks something.

---

### Post by judgejudy on 2006-11-23
> **HymnToLife said:**
> My advice is to remove Automatix completely before it breaks something.
now thats helpfull[-( 

did you try     
sudo apt-get remove automatix2    

in terminal ? if you did try,  

sudo apt-get remove automatix  

as you may have downloaded the old automatix. to use the terminal go to applications>accessories>terminal
hope this is helpfull
and hymntolife we know you dont like automatix but if your going to post plz try and help :p

---

### Post by Bachstelze on 2006-11-23
My first guess would have been to browse the repo to find out if the package actually is there and try to guess why apt-get won't find it but guess what ? 403 error my friend, first time I ever see a repo that won't let you browse the packages !

---

### Post by cantormath on 2006-11-23
search for automatix in synaptic,
right click and remove all

then add the automatix repo to your source.list
save
open terminal```


laptop:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
laptop:~$ gpg --import key.gpg.asc
laptop:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
laptop:~$ sudo apt-get update
laptop:~$ sudo apt-get install automatix2
```

---

