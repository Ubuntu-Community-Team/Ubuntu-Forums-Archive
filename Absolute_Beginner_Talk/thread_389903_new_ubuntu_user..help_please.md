---
title: "new ubuntu user..help please"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by k0mpresd on 2007-03-21
never thought i would say this but i installed ubuntu again last night...i installed it once before..didnt really like it but decided id give it another try due to the recent xbox360 linux boot loader

anyways..i have a couple questions to get me started

first my terminal program tells me that "C executables cannot be created" or something along those lines...i did a quick google search and i read something about gcc and something else needing to be installed..any help there?

also..anyone know of a good mp3/media player for linux? i found a couple but dont know whats good and whats not

oh..one more thing..the mail client tells that "server does not support authentication type" or again, something along those lines..i changed the log in type and it started asking for my password over and over...i can send mail..but i cant receive it :confused: 

any help is very much appreciated :)

---

### Post by profXavier on 2007-03-21
First off, you want to program in C, if so, you want to use the shell?  If you want to program in C, you probably want to have a C compiler, gcc, being one.

As for music, I personally use xmms, as its the same as winamp, which is what I mainly used in Windows.  If you want to load mps, like iTunes, onto your devices, and manage your music use Amarok.

You can perform a search in Synaptic for each of these to install.

Hope that helps

---

### Post by k0mpresd on 2007-03-21
i will search for gcc once i get home

i downloaded some software called crosstool to compile powerpc64...not sure if thats related or not..still havent gotten that to work correctly either

can you tell im a n00b? haha

i tried installing xmms via the terninal..that is one of the apps that told me executables cannot be created..thanks for the suggestion though :)

it does help..thank you

---

### Post by Tomosaur on 2007-03-21
To get rid of those compiler errors and such, you need the build-essential package. You can find it through Synaptic, or just type:

```

sudo aptitude install build-essential

```

at the command line. This will install everything necessary to compile stuff.

As for media players - I really, REALLY love Amarok, but it's primarily music, so don't expect to be watching videos with it. For a great 'all round' media player, you'll be hard pressed to beat VLC. Looks a little basic, but it will run virtually everything you throw at it, and there are skins available to make it look a bit more modern. It's got tons of features, it really is one of the best out there. Plus, it's free, so it's even better :P

---

### Post by k0mpresd on 2007-03-21
many thanks to both of you :)

i feel so bad posting such n00b ?'s but i really want to try to stick w/ ubuntu this time around so i need to get it to where i can use it everyday and have a clue what im doing

and tomosaur, i am mainly looking for a mp3 player since i just like to sit @ the comp, surf the net/work on whatever, and listen to music :guitar:

---

### Post by profXavier on 2007-03-21
Also, you might want to use Synaptic as your method to install new applications.  If you use the [Ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") it will help you go through most of the essential packages you will need, and give you practice looking at using your command line to install.

Its a long read, but it gives you everything.

---

### Post by k0mpresd on 2007-03-21
that is a long read..maybe it will give me something to do this afternoon @ work haha

---

