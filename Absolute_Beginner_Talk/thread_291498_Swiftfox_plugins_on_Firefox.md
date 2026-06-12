---
title: "Swiftfox plugins on Firefox"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by fasoulas on 2006-11-02
I have firefox 2 on my Ubuntu 6.06 istallation i tried to put plugins but i mothing happend 

I downloaded swiftfox from automatix and all it's plugins but it is based on firefox and it is version 1.5.7 
Swiftfox work with all the plugins,it also has all the extensions that i have on firefox 

But when i open swift fox close it and after open firefox it does something like update and checks the extensions for availability(it does what it does like when you install it for the first time).and the opppsite with swiftfox

Can someone help me on this ?????

I heard that swiftfox is faster than regular firefox

Can i copy paste swiftfox plugins in the firefox plugins folder?Is that goin to make the firefox work with the plugins?

---

### Post by raul_ on 2006-11-02
Yes

---

### Post by fasoulas on 2006-11-02
When i try to copy paste it says i can't because am not the owner 

i am loged with the accound that i had to create when i installed ubuntu 

Do i have to make another accound to log on as root?

---

### Post by joeshmo on 2006-11-02
>  	When i try to copy paste it says i can't because am not the owner

i am loged with the accound that i had to create when i installed ubuntu

Do i have to make another accound to log on as root?

No, you don't. Go into terminal and type:

sudo nautilus

Then navigate to the place you want to modify, assuming it isn't a ntfs partition, modify as needed.

---

### Post by fasoulas on 2006-11-02
> **joeshmo said:**
> No, you don't. Go into terminal and type:

sudo nautilus

Then navigate to the place you want to modify, assuming it isn't a ntfs partition, modify as needed.

what's the difference between that and goig normally from the menu???

---

### Post by zekopeko on 2006-11-02
you can modify/copy/cut/delete files only within your home directory.
the rest of the system has mostly root permissions so that you don't brake something by accident.

sudo means Super User DO and basicly gives you root/administrator rights.

sudo nautilus opens the file browser with root rights so you can go anywhere and copy/delete stuff (even system files).

once you get the hang of sudo and the terminal you'll see that it is very powerful and nothing to be afraid of (if you are :))

read this for more info [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by fasoulas on 2006-11-02
OK thnx for the information

---

