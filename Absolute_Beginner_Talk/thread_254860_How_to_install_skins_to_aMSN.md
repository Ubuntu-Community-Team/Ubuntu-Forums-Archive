---
title: "How to install skins to aMSN"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-09-10
Anyone know how to install new skins to aMSN for Ubuntu? I've already downloaded the ones I want. Please help.

---

### Post by shoot2kill on 2006-09-10
go to the dir,

/home/USER/.amsn/skins   (where user is ur usename)

extract the full folders here....

restart amsn, change skins..

hope this helps

---

### Post by Narcoleptic_Insomniac on 2006-09-10
> **shoot2kill said:**
> go to the dir,

/home/USER/.amsn/skins   (where user is ur usename)

extract the full folders here....

restart amsn, change skins..

hope this helps

That didn't work, it says "I do not have permission to write to this folder".
I went to properties of the folder and it said "I am not the owner so I do am unable to change these settings" under the permissions tab.

---

### Post by shoot2kill on 2006-09-10
ok... i use kubuntu, so im not sure of the correct command, but i use

```

kdesu konqueror

```

for ubuntu, use ```
gksu <file manager name>
```

sorry i couldnt help more... 

once this is done, go to ur amsn skins folder and try again

---

### Post by Narcoleptic_Insomniac on 2006-09-10
> **shoot2kill said:**
> ok... i use kubuntu, so im not sure of the correct command, but i use

```

kdesu konqueror

```

for ubuntu, use ```
gksu <file manager name>
```

sorry i couldnt help more... 

once this is done, go to ur amsn skins folder and try again

I get this in terminal "bash: syntax error near unexpected token `newline'
matt@ubuntu:~$"

---

### Post by shoot2kill on 2006-09-10
what did u try.. when i said "<file manager name>" i meant u to input the name of ur file manager...

---

### Post by Narcoleptic_Insomniac on 2006-09-10
> **shoot2kill said:**
> what did u try.. when i said "<file manager name>" i meant u to input the name of ur file manager...

I tried gksu <file manager> which didnt work then I tried gksu <archive manager> and it gives me the same thing.

---

### Post by shoot2kill on 2006-09-10
try..
```

sudo aptitude update
sudo aptitude install konqueror
gksu konqueror
```

then go to amsn skins dir, and try again..

---

### Post by Narcoleptic_Insomniac on 2006-09-10
> **shoot2kill said:**
> try..
```

sudo aptitude update
sudo aptitude install konqueror
gksu konqueror
```

then go to amsn skins dir, and try again..

It didn't do anything. It opened up some thing. Thats it. I went back to amsn skins dir and i still couldnt change permissions or put new skins in it.

---

### Post by shoot2kill on 2006-09-10
it opened up something.. was it a window, where u could click a button saying HOME... and go to amsn folder from there.. dont close this window

---

### Post by Narcoleptic_Insomniac on 2006-09-10
> **shoot2kill said:**
> it opened up something.. was it a window, where u could click a button saying HOME... and go to amsn folder from there.. dont close this window

Oops, I closed it, you never replied in time, and yea it was a window and I tried to look around in home folder and stuff but it wasnt anything I had seen on my computer before. I can open it up again by going to Applications/Internet/Konqueror

---

### Post by shoot2kill on 2006-09-10
nope... to do it again.. do

gksu konqueror in console.. this gives u permissions

---

### Post by Narcoleptic_Insomniac on 2006-09-10
Ok I got to the skins folder in Konqueror but I still can't change permissions. And It still won't let me put the skin in the skins folder.

---

### Post by Narcoleptic_Insomniac on 2006-09-10
> **shoot2kill said:**
> nope... to do it again.. do

gksu konqueror in console.. this gives u permissions

Ok, I'll do it over agina, forget that last post I made cause I opened it from apps.

---

### Post by shoot2kill on 2006-09-10
did u do it through console.. 

gksu konqueror

if not, do this.. no need to change permissions, just do the job u wanna do..

------------------------------
Never Mind...

---

### Post by Narcoleptic_Insomniac on 2006-09-10
Ok it let me in and I can use the permission tools and stuff now, and I'm changing the ownership and in the "User" feild, I'm putting in my user name, which is Matt, my name, what do I put in the group feild?

---

### Post by shoot2kill on 2006-09-10
there is no need to edit permissions, just extract the folders to that directory,

when u wdo not have permissions in future, remember 

gksu konqueror

i would not recomomend changing permissions

---

### Post by Narcoleptic_Insomniac on 2006-09-10
Ok, I got it all working, thanks a lot for the help man.

---

### Post by shoot2kill on 2006-09-10
np.. these forums are a great place for people new t linux (i am one myself)

hope i can help u again sometime.. 
:D

---

### Post by Jukey on 2006-09-10
Just a small note, I thought it was gksudo, and that has worked for me. since you've had success i guess gksu works too

---

