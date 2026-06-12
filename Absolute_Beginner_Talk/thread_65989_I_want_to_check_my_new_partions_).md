---
title: "I want to check my new partions :)"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by cyclister on 2005-09-15
I want to know how to check if my partitions runs as them should?
What commands or wich programm can I use?
I did test cfdisk with no luck

My whole hdd is about 40 gb big
And I want to know about where I can see a proper list how the partitions should look like and how big them should be.
My first is home about 20 gb big
My root is quite big 15 gb (heard it should be like 8 gb)
And a swap big as half my memory size, only time I have seen that one moving is when I updated my system :(
And when I looked in the installation program is saw many things I could form a particullar partition into.
I want to know more about this options and what they stand for?
I cant remeber them all just for now Im afraid

I checking in my systemoverviewer and do not see any sign that my swap is in use 0,0 % is that all right?
I just surfing around and not having any major programms running

---

### Post by mlomker on 2005-09-15
I go with 6 gigs on /.  1.5x memory for /swp.  The rest can be /home.

My / partition is only using 3 Gb, so plenty of room left on it.

Try these commands to look at your partition and how much space is in use.
```

su
fdisk -l
df

```

---

### Post by rj686 on 2005-09-15
[QUOTE=mlomker]I go with 6 gigs on /.  1.5x memory for /swp.  The rest can be /home.

My / partition is only using 3 Gb, so plenty of room left on it.

Try these commands to look at your partition and how much space is in use.
```

su
fdisk -l
df

```[/QUOTE]
 how is swap assigned using ubuntu, i know mepis asks what partition i want to use as swap during the install....

---

### Post by cyclister on 2005-09-15
Now to a real nub question how do I know my SU password?
I have one I use to root and to other thing but I do nor remember I did a SU password.
How do I create one? :P
Or
How do I find it?

---

### Post by rj686 on 2005-09-15
[QUOTE=cyclister]Now to a real nub question how do I know my SU password?
I have one I use to root and to other thing but I do nor remember I did a SU password.
How do I create one? :P
Or
How do I find it?[/QUOTE]
 u mean sudo? ubuntu doesn't use su. Your root password is the password u use.

---

### Post by ds[de] on 2005-09-15
[QUOTE=cyclister]Now to a real nub question how do I know my SU password?
I have one I use to root and to other thing but I do nor remember I did a SU password.
How do I create one? :P
Or
How do I find it?[/QUOTE]

You can create/change your root password by typing (when logging in with your normal user account):

sudo passwd root
Then if asked for your password, enter the password for your user account with which you are still logged in, then you get
*Enter new UNIX password:* 
Here you just enter your root password and confirm it.

Regards,
ds[de]


Edit: After re-reading your post I realized that my answer might not be exactly what you were looking for, so forgive me if I was too fast  ;-)

---

### Post by cyclister on 2005-09-16
The thing is that I tried to use the commands mlomker gave me and the terminal gave me 
su:
Password: 
Or something like that but I should first log in as sudo then put in the variables that mlomker gave me.Not so easy this all the time, but I am sure that Im learning after a while, after all I am very familliar with windows not with linux but after a while its gonna be much much better and more into what the computer is all about.

Offtopic
Windows have more and better multimedia players and so forth, you can say that you have all most so god as microsoft but just allmost.Their whole system hve the most user friendly enviroment it can get, and yet that can be quite tricky.
I think that linux can get more user friendly and I do not mean fedora core I mean a good Gnu distro, that would benefit the whole unix world.More safer enviroment and better wine applikations and not so many options for the user.That would millions of people buy, for say half the price of windows like 63$.And you should be able to have more fps then Windows in every game, or just about the same.Or they will shift to MS that I can think in a near future that people will ask for, with new stuff implumted right down in the CPU, that will be a little of a destroyer to all who want to download their program illegal and try new things for free.
And you could do like 3 (like say 5 diffrent cd's) diffrent versions and one cd that locate ur settings on the motherboard, so the distro know what chipset you use and there for get the best from that one.For instance Ive heard that nforce chipset have trouble in linux with sound, and via chipset in games you cant cream out so many fps you want.So that bug is to fix, and you can have one for i chipset (i865) a pure intel version too.I do not mean that the user should choose cd's they only se now input cd bla bla.That I can say many gamers want to have, and that mouse drivers and a good java and graffical "motors" in this enviroment, so your computer  out run microsoft in every way.I think that this is not a impossible thing to do. 
If you guys do this you will be able to spend more $ I cant say when but in a near future, and lay many $ in PR so that your sure of that your distro is the one who gonna be the one that "we" gonna buy.I mean it so many distros out their, and everybody can copy, it.That is my opinon about this matter, but hey I can be wrong  \\:D/  

More offtopic
If you didnt know it and look at gnu banners and so fort and pictures and wonder why the hell a wilderbeast is their "macot"
Gnu = Wilderbeast in swedish

---

### Post by mlomker on 2005-09-17
[QUOTE=cyclister]The thing is that I tried to use the commands mlomker gave me and the terminal gave me 
[/quote]

Ubuntu's designed to use **sudo** in front of commands that need them.  The problem is that I never know which commands need it until it gives you an error message.  I also work on a variety of linux boxes of different distributions and states of install (some development and some production).  **su** always works but sudo has to be configured!

That being said, sudo is preferred because when you use it the commands get logged to a log file whereas **su**ing to root does not.  That's nice if you're the 'owner' of a server and one of the other admins does something you don't like---you've got a log file of what they did and can yell at them.   :grin: 

> 
Windows have more and better multimedia players and so forth, you can say that you have all most so god as microsoft but just allmost.Their whole system hve the most user friendly enviroment it can get, and yet that can be quite tricky.


Sure.  There are a lot of plug-ins for programs to play different types of files but they aren't automatically installed.  If you find a type of file that you can't play then just search on here or post a message: "What can I use to play ** file?" and someone will help out.

> 
applikations and not so many options for the user.That would millions of people buy, for say half the price of windows like 63$.And you should be able to have more fps then Windows in every game, or just about the same.Or they will shift to MS that I can think in a near future 


Well, distros like Xandros and Linspire are already doing that.  Perhaps there are distros focused on gamers but I haven't looked into it.  There's also the fact that a whole lot of people won't spend a penny on linux due to philisophical reasons.

There's a much bigger market $$-wise in a business desktop, so that's what the few commercial linux companies are focusing on.

---

