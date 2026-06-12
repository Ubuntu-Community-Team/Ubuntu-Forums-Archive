---
title: "Synaptic Package Manager - Repositories"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by lifemaximum on 2006-09-17
Hi all

I am new ubuntu user,A while ago i added this apt link to my repositories to download stuff from , but it didn't work cause it says the link was closed or something, and now i can not use my Synaptic package manager anymore , cause everytime i start it off, i get error, and it seems there is no way to by pass that error, i tried editing the repositories list, but the thing i added is not there, Either it is not there or i am looking in a wrong place, Sumbody  help me with this how am i suppose to remove it..


[COLOR="Red"]*" The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences."*[/COLOR]   that is the error msg that i get



and after that it shows this
[COLOR="Red"][I][I]
"E: Type 'deb [http://pkg-gnome.alioth.debian.org/debian/](http://pkg-gnome.alioth.debian.org/debian/) experimental main' is not known on line 22 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: Type 'deb [http://pkg-gnome.alioth.debian.org/debian/](http://pkg-gnome.alioth.debian.org/debian/) experimental main' is not known on line 22 in source list /etc/apt/sources.list
E: Unable to lock the list directory"[/I][/I][/COLOR]

I have no clue what it is talking about...

the link that i entered was 

[COLOR="Red"]*'deb [http://pkg-gnome.alioth.debian.org/debian/](http://pkg-gnome.alioth.debian.org/debian/) experimental main'*[/COLOR]

So i feel like ](*,)  ...

i would appericate it , if someone thought me how to get rid of it.

---

### Post by Najand on 2006-09-17
Edit /etc/apt/sources.list:
```

sudo nano /etc/apt/sources.list

```
Delete the link or just comment it using #.
Then run:
```

sudo aptitude update && sudo aptitude upgrade

```

---

### Post by lifemaximum on 2006-09-17
Dude thanks for the help....

I tried what u said but i didn see any link there to delet or to comment it to...so i figured somehow it must have gotten deleted or something i updated still get the same error ..

u got any idea what is wrong??

---

### Post by Najand on 2006-09-17
Hmm, you couldn't find it there? Can you post your file here?
And also can you check the spelling again, too?

---

### Post by ramcosca on 2006-09-17
I know this post won't be of any help but...

You forgot to mention Ubuntu on the poll.
There's also some other versions of Ubuntu... Nubuntu, for example. Only one that came to mind, lol.

---

### Post by lifemaximum on 2006-09-17
actually jus now i find the link the source list... i tried to send it to u..but it doesn't let me upload it here...got upload error...anyway i found the link i just cannot change the stuff in it cause it says u dun have the premission to change the file..i am the admin i should be able to change it rite?

---

### Post by Najand on 2006-09-17
Well, maybe becuase you did not use "sudo"!
Use terminal at
Applications -> Accessories -> Terminal
And type:
```

sudo gedit /etc/apt/sources.list

```

---

### Post by lifemaximum on 2006-09-17
yea u are rite sorry i forgot to mention ubuntu itself... i am pretty new to the whole new linux world and stuff.:-\"

---

### Post by Najand on 2006-09-17
It is Ok...
I was like you when I first started it.

---

### Post by lifemaximum on 2006-09-17
Dude your awsome...

It worked... hahah

Thanks alot man...

Respect, You are good

---

### Post by lifemaximum on 2006-09-17
Dude...Do u have any idea how to get the MP3 files played in ubuntu... how to get the codecs and install it ...

---

### Post by furste on 2006-09-17
word, i was having the same problem it for days and this fixed it!

thanks.

---

### Post by Najand on 2006-09-17
What player do you wanna use? I recommend totem + xine.... (The default is totem + gstreamer and it sucks)
If you want to install it:
```

sudo aptitude install totem-xine totem-xine-firefox-plugin xine-ui libxine-extracodecs libxine1c2 libxinerama1

```

---

### Post by lifemaximum on 2006-09-17
alrite ..

Did that

and i got

E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

i guess i can only install it after done using synaptic to install packages

---

### Post by Najand on 2006-09-17
You cannot use more than one package manager at the same time.... Close synaptic and try again.

---

