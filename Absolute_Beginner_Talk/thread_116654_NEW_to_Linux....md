---
title: "NEW to Linux..."
date: 2006-01-13
forum: Absolute Beginner Talk
---

### Post by madu on 2006-01-13
Hi guys..

At last I migrated to Linux.. Ubuntu.. feels great to be here...
I am an absolute noobie.. so please help me out here guys..
First things.. I want to hang in here and dont want to get back to Windows to keep in contact with my contacts..
I want to install SKYPE guys.. but having a bad luck..
Seems I cant install the .deb package.. Says not found in Archive.. How can I install this guys..?
Also, I have a wireless keyboard.. and it doesnt work to chose in the grub bootlaoder.. do you guys have any idea how i can use it.. or I cant?

Thanks a lot guys.. Once I get those two things done, I will have lot of time to hang around here and learn Linux..
Thanks a lot guys..!

Cheers..!

---

### Post by 23meg on 2006-01-13
Welcome. For Skype see this: [https://wiki.ubuntu.com/SkypeHowto](https://wiki.ubuntu.com/SkypeHowto). For your other problem, start by doing a search in the forums and wikis; see my signature.

---

### Post by jorn on 2006-01-13
You can install skype by using Automatix:
[http://www.ubuntuforums.org/showthread.php?t=114251](http://www.ubuntuforums.org/showthread.php?t=114251)
Jorn

---

### Post by madu on 2006-01-13
Hi guys..
Thaks for the replies...
Yes.. i did look into them.. and i saw that i have to get the .rpm and convert it..
but the problem is "alien" command is not found..
then I downloaded ALIEN.. and for it to install, I have to "make" it,, but surprisingly, it says "make" not found!!!
Whas the problem guys.. how can I do it? To install ALIEN, I first enters the Perl.Pl something command.. and it worked.. the second command is "make".. and its not working...
Please help me guys...!

---

### Post by 23meg on 2006-01-13
```
sudo apt-get install alien
```will install alien. 

Here's an easier (unofficial) method for installing it in Breezy: [http://www.ubuntuforums.org/showthread.php?t=81831](http://www.ubuntuforums.org/showthread.php?t=81831)

---

### Post by Gustav on 2006-01-13
for make to work install build-essential
```
sudo apt-get install build-essential
```

---

### Post by M3lted on 2006-01-13
well im quite new to , but i recommend useing automatrix,becouse of the following reason's
first off it just very fast to install most things u need and get u settled in your new enviroment very fast.
Its very user friendly,and it install's skype ,so after u got what u want u can get your time to figure out other stuff :P

---

### Post by madu on 2006-01-13
Hi guys,,,

Oh.. phew.. this is soo hard.. but i;m learning a lot..
First of all thank you very much guys..
I used the sudo install commmand and installed ALIEN.. and now when i try to convert the rpm to deb with alien, it runs and gives error.. and in I could see it says gcc not found? alos I donthave the make command..
Isnt it like a standard command..?
Anyway guys.. how do i install gcc..? I tried synaptic, but I dontknow how o get the gcc..
Please help me out here guys..once I get my skype working, i can hang around here and explore slowly and learn..
also I tried that ther easier link for skype.. i downloaded it and tried to sudo install, but unfortunately, it says package not found.. HEres what it says..:

maduranga@Maduranga:~/Desktop$ sudo apt-get install skype_1.2.0.18-1_i386.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package skype_1.2.0.18-1_i386.deb

hmmmm... please help guys..!! thank you very much...!

---

### Post by M3lted on 2006-01-13
i just looked and u can get skype via synaptic 
but i do thing u need to enable some extra repositories
here a link how to do that 
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse)
and then just press the search button and type skype u will find a packet for it :)
check the packet u want and aplie

---

### Post by madu on 2006-01-13
Thanks you very much guys...
I opened the sypnatic and enabled those settings and searched to skype but no success...
So i'm going to try automatrix..
If anybody have a link or guide to this pleeease post.. i am an absolute noobie.. please tolerate me few times :confused: 
i'm going to search for automatrix now.. wish me good luck..!!

again.. thanks a lot guys!!

---

### Post by 23meg on 2006-01-13
I already pointed you to a guide: [http://www.ubuntuforums.org/showthread.php?t=81831](http://www.ubuntuforums.org/showthread.php?t=81831)

Download this file: [http://rapidshare.de/files/6743630/skype_1.2.0.18-1_i386.deb.html](http://rapidshare.de/files/6743630/skype_1.2.0.18-1_i386.deb.html)

Install it with ```
sudo dpkg -i FILENAME
```

---

### Post by madu on 2006-01-13
I cant install Automatrix.. gives a error..
I think its because i'm using the and64 version.. hmmm... looks like i;m stuck...
Any idea guys..?
I tried everything.. i cant seem to get anything installed...
anyway.. I was doing something and something worked..!!
now i have a folder skype-1.2.0.18
In that I have 3 folders.. : DEBIAN ETC USR
Can I get any help with this guys..?
Sorry for the trouble guys..

---

