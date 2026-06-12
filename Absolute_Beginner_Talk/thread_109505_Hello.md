---
title: "Hello"
date: 2005-12-28
forum: Absolute Beginner Talk
---

### Post by total numpty on 2005-12-28
Hello,

As posted many times on here before, but i'll say it again, i am an absolute novice/newbie/noob to this linux world. I have just installed UBUNTU on a spare PC after reading about it in a computer magazine, within a tutorial section. 
I have never strayed from windows before but have always been intrigued by linux and never really read a bad thing about it.
My install went well and the machine seems to work fine (as far as i can tell). It recognised all my hardware including a capture card, and, i can VNC into it from my XP machine which is a bonus. 

What made me take the step in the direction of linux was that i was curious of a single program i wanted to install and try out. This program is called 'zoneminder'. This program is found here [http://www.zoneminder.com/](http://www.zoneminder.com/) 

Its a cctv program for recording single and/or video images. 
I have read a number of posts on this forum and learnt a little about how ubuntu works however I am a bit lost when it comes down to installing anything. I followed the instructions with zone minder but it doesnt seem to work.

The instructions were :-

./configure
make
makefile 

(I think)

Can anyone point me in the right direction of what to do and if possible post any appropriate links that may help me, as there seems to be hundreds of pages on these forums and unfortunately cant understand most of them!

Thanks in advance.

---

### Post by Manny C on 2005-12-28
Hi TN
./configure
make
sudo make install 
(then type in your "root/administrator" password - preset in the install)

Does this spare machine have internet connection?

---

### Post by total numpty on 2005-12-29
Thx for the reply, will try that shortly.
Yes, this PC is connected to the internet, i amazed myself doing that bit as i installed a network card after installing UBUNTU and it seen it no problem. Then i found i had to activate the card, which i did. It was DHCP enabled so it picked up an IP address from my router and works like a dream :)

---

### Post by poofyhairguy on 2005-12-29
[QUOTE=total numpty]Thx for the reply, will try that shortly.
Yes, this PC is connected to the internet, i amazed myself doing that bit as i installed a network card after installing UBUNTU and it seen it no problem. Then i found i had to activate the card, which i did. It was DHCP enabled so it picked up an IP address from my router and works like a dream :)[/QUOTE]


You can install it with those directions in the terminal if you install somethings first. To install them, use this command:

> sudo apt-get install build-essential

that will let you compile programs.

---

### Post by total numptys mate on 2006-01-01
Hello all

As name suggests a total novice in the linux world! I am a windows user and have been from the "dos" days. I am starting to get that hang of ubuntu "sort of" but am very interested in this post about zoneminder.....has anyone set this up and if so any set-by-step instructions for the ubuntu noobs ;) 

Lets keep this post active until one of us sorts this out.....all in favour say I


Great forum and i am slowly starting to love ubuntu............it is a big leap from windows but i am trying.

Come on [COLOR="Red"]total numpty [/COLOR]let us know how far you have got?

Thanks

Mark.

---

### Post by total numpty on 2006-01-04
i have got no further, it requires SQL or something and when i tried using synaptic and installing it, it wont load any dependencies for SQL?


I

---

### Post by Lord Illidan on 2006-01-04
You have to add some repositories.
Take a look at this site. It will help you gain a better understanding of what to do. Take it slowly, enjoy the ride.

[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

---

### Post by phido on 2006-01-04
[quote=Manny C]Hi TN
./configure
make
sudo make install 
(then type in your "root/administrator" password - preset in the install)
[/quote]

Isn't dh_make, fakeroot debian/rules binary and then install with dpkg, not better?

---

### Post by deontaljard on 2006-01-10
Hi

Have you tried the Debian install in their docs page?
[http://www.zoneminder.com/documentation.html](http://www.zoneminder.com/documentation.html)
There is a how to written by someone called Koenzie

Cheers

---

### Post by total numpty on 2006-01-10
thanks

---

### Post by total numptys mate on 2006-02-24
Come on people can anyone help here !!!

I have been trying for ages to get zoneminder running on an ubuntu machine and i am close to breaking point - would one of you kind people please post a step by step idiots guide on how its done.......and i mean idiot!.....all the .\config..blar blar and such as i am totally new to linux....


First one to do so wins !..lol

---

### Post by BrownieMan on 2006-05-27
If anyone gets it working I would love to hear from you and then perhaps we could build a HowTo for this thing. You can IM me at anhourtofall or email at [email]wickednice@gmail.com[/email]

---

