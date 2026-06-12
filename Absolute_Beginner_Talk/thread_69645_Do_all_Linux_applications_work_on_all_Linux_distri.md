---
title: "Do all Linux applications work on all Linux distributions?"
date: 2005-09-27
forum: Absolute Beginner Talk
---

### Post by commodore on 2005-09-27
Do all Linux applications work on all Linux distributions?
I don't mean totally *all*.
Or do I have to do something with compiling? 
Sorry if I sound dumb :D

---

### Post by odin on 2005-09-27
well I dont know how dumb that is but I also made myself the same question;-).The thing is that if you get the tarball and compile it succesfully with make and then install it with make install yes,the app will work on your system.Anyway whenever you need to install something look first in the repositories with either apt or synaptic.Those packages there are made for ubuntu so they are the ones that will work better for you.

---

### Post by KingBahamut on 2005-09-27
It depends entirely on how the developers package the programs they build. 

If your a beginning ubuntu -- and ultimately linux user -- stick to searching for application through the synaptic package manager , and -- if your using Breezy , the Add Applications program. 

If you have any questions about what you dont find in there and you need, then ask us, and we will direct you properly.

---

### Post by weasel fierce on 2005-09-27
Easiest step is always to use the repo's and synaptic.

Debian packages should work pretty well, on Ubuntu. 

RPM packages can be converted, but Im not sure how well it actually works.

Compiling from the source code is a good option (especially with checkinstall that makes it a debian file, so its easy to remove again), but can take a bit.

---

### Post by commodore on 2005-09-27
I don't understand most of the names you said :D but I get the idea. So learning compiling isn't necessary?

---

### Post by KingBahamut on 2005-09-27
Not really, unless you want something really specialized.

---

### Post by Perfect Storm on 2005-09-27
[QUOTE=commodore]I don't understand most of the names you said :D but I get the idea. So learning compiling isn't necessary?[/QUOTE]

No, it's not a necessary, but a good Idea. Perhaps when you get more familiar to linux. Or you could just jump right into it, very good way to gain experience (geesh, now it sounds like a RPG game :P )

---

### Post by brentoboy on 2005-09-27
The short answer here is "Yes" and "no."

If you grab an executable file from one Linux system and move it to another, it generally wont work unless the exact same kernel is in place.

If you have ever developed C for windows, it is easy to understand the problem. Imagine if the windows.h file was potentially incompatible with itself for each version of windows.  You would have to get the correct windows.h file for each target computer you wanted it to work on, and if you wanted your resulting program to work across them all, you would have to meld the windows.h file to magically have the same data structure sizes and things no matter what kernel it was running in.

Microsoft has a (slight) advantage in that they can control data structures in all versions of windows to be exactly the same size (theoretically) so in most cases an app that works on win2k will work on Xp etc,  but in Linux, because any distro can freely change the way the kernel works, and potentially add more stuff to the headers, there will always be inconsistencies.

The reason this is not as big a problem as it would otherwise be is that most Linux apps are available as source code, and it links to the kernel using the headers on your PC so you know you have a match, and any potential incompatibilities are caught by the compiler not at run time.

The beauty of Ubuntu is that the kernel is precompiled, and they go to great lengths to make their different architectures have similar headers, so that there is very little variance in the headers between processor types etc.  Then, they precompile the stuff to work on those kernels, so you can download prebuilt packages and not have to compile them to your kernel.

If you get something from anywhere other than Ubuntu, you should compile it from source or you may have serious issues - or you might not - depends.

Hope that answers your underlying question.

---

### Post by brentoboy on 2005-09-27
[QUOTE=Artificial Intelligence](geesh, now it sounds like a RPG game :P )[/QUOTE]

What are you talking about, Linux IS an RPG.

Its a strange first person world where you explore dungeons and search folders for interesting files - treasures and stuff.  You beef up your character (pc) until it has all the most powerful weapons, and tell your friends what enemies (driver problems) you have defeated.

Occationally, you even walk noobs through the early levels of the game so their character is good enough to stand on their own while they get used to game play.

If that isnt an RPG I dont know what is.

---

### Post by Perfect Storm on 2005-09-27
Hehehehe....if you look at it in that way :D

---

### Post by matthew on 2005-09-27
[QUOTE=brentoboy]What are you talking about, Linux IS an RPG.

Its a strange first person world where you explore dungeons and search folders for interesting files - treasures and stuff.  You beef up your character (pc) until it has all the most powerful weapons, and tell your friends what enemies (driver problems) you have defeated.

Occationally, you even walk noobs through the early levels of the game so their character is good enough to stand on their own while they get used to game play.

If that isnt an RPG I dont know what is.[/QUOTE]
LOL. Thanks, I needed the amusement today!

---

### Post by Ride Jib on 2005-09-27
[QUOTE=brentoboy]What are you talking about, Linux IS an RPG.

Its a strange first person world where you explore dungeons and search folders for interesting files - treasures and stuff.  You beef up your character (pc) until it has all the most powerful weapons, and tell your friends what enemies (driver problems) you have defeated.

Occationally, you even walk noobs through the early levels of the game so their character is good enough to stand on their own while they get used to game play.

If that isnt an RPG I dont know what is.[/QUOTE]

+1: Funny


oh poop. I forgot I'm not on slashdot, atm.


**Luke Luke your targeting computer is off.........Try to stay on topic, please. -- KB**

---

### Post by netwench on 2005-09-27
mod answers +1 Funny and +2 Insightful
.... but....

brentoboy said:
"The beauty of Ubuntu is that the kernel is precompiled, and they go to great lengths to make their different architectures have similar headers, so that there is very little variance in the headers between processor types etc. Then, they precompile the stuff to work on those kernels, so you can download prebuilt packages and not have to compile them to your kernel.

If you get something from anywhere other than Ubuntu, you should compile it from source or you may have serious issues - or you might not - depends"

that little "depends" part..what do i look for to know the depends?  the kernels must match? only 2.6 goes on 2.6, etc? ok, as a newbie,i'll stick with what i can get with synaptic, but if i want to experiement, what info do i need? how do i know what kernel something has been complied in, if that's what i need to know...etc..or only .deb extensions? or....?

thanks!!!

---

