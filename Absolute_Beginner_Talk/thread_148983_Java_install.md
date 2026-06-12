---
title: "Java install"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-03-23
I am a linux n00b and have installed java re and sdk and want to install netbeans, when installing it it looks for java sdk but does not find my installed skd, can someone please advise me? Am i missing something, it starts looking for the sdk but returns nothing.....

Ta

---

### Post by paulipe on 2006-03-23
did you use synaptic to install the packages?
From where are you getting the net beans to install?
Which ubuntu version are you using?
Paste some output from the installer or whatever error messages you are getting. Not sure I can help but will try.

---

### Post by tommy1987 on 2006-03-23
No i downloaded the self extracting files myself (.bin's) it all has been okay apart from netbeans tries to locate an sdk on your machine and it fails despite the fact that its there!! im using 5.10 breezy badger,,   It starts running the installer and then displays output suggesting it is looking for the sdk then comes up sdk could not be found eventually......

---

### Post by harisund on 2006-03-23
I am guessing there is a problem with the path. 

Please write back where you installed the SDK, or even if you could explain how exactly you installed the SDK it would be fine. 

Also , post the output of
```
echo $PATH
``` here

---

### Post by tommy1987 on 2006-03-23
i installed the sdk to /Home/Java/jsdk1.5.0/                       Does that help in anyway, I dont know what i have to do with paths etc, im a bit of a linux n00b! :-s   I will be a true convert once i get java installed and up and running on ubuntu cos java is the only think keeping me going back to windoze! Please help!

Thanks

---

### Post by tommy1987 on 2006-03-23
:~$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games


is that what you wanted?

---

### Post by tommy1987 on 2006-03-23
Can anybody help with the above? desperate to get it working, im sure it is something minor,,,, ;-)thanx

---

### Post by Mr Green on 2006-03-23
Uninstall your SDK and try installing it like described here:
[http://my.opera.com/Mr%20Green/blog/show.dml/189036]("http://my.opera.com/Mr%20Green/blog/show.dml/189036")

I installed it like that and Netbeans installed without a hitch afterwards.

---

