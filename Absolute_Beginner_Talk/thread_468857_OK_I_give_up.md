---
title: "OK I give up"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Mechmechie on 2007-06-09
I give up,
I have tried to install ubuntu feisty fawn. 
That all goes ok but I am unable to get wireless networking to work.
I have googled and found loads of stuff on ndiswrapper etc, but I get stuck with the basics, like when I get told to Make file etc, or told the dependancies are not met... Huh ftw?
My network card gets detected but I am unable to intstall the drivers, as I cant figure out the ndiswrapper stuff.
I am at the point of scrapping linux all together as i cant see what the point is , if a person has to battle just to get the basics going.

I have the network card drivers on disk I have ndis wrapper etc.
Any one able /willing to help:mad:
Thanks

---

### Post by Kobalt on 2007-06-09
All right first of all : calm down. As far as I can see, this is your first post on these forums. Searching for yourself how to do this is a good thing, but you should post here your questions if you don't understand.
Then we must identify your wireless card : which model is it, chipset ?
To find it out, go into Applications > Accessories > Terminal. Enter ```
lspci
```In this list of hardware you will find your wireless card : please post here the info you will get. We'll see afterwards if you do need to use ndiswrapper of if you can use some other open source drivers.

---

### Post by Mechmechie on 2007-06-09
Hi,
The card is a belkin 7001

But right now my life is looking bleak...I followed instructions on removing Ubuntu from the pc using the fdisk /mbr method and now i get no booting ( this is /was the wifes pc....):(

Thanks for the response, let me get back to square one first

---

### Post by p_quarles on 2007-06-09
Getting back to the beginning shouldn't be difficult: just reinstall Ubuntu from the CD. 

Also, the easiest way to remove it (in the eventuality that you decide to do that) would be to install another OS over it.

---

