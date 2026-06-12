---
title: "Sudo problem"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by Xyus on 2006-08-24
Hi,

Whenever I type a Sudo command it asks for a password? 
If I type my login password in it tells me "incorrect" , I didn't have this in ubuntu so what's the issue?

Plz help me, 
xyus

---

### Post by aysiu on 2006-08-24
Are you in the *admin* group?

Type ```
groups
``` and see if *admin* shows up in the list.

---

### Post by Catewilliams on 2006-08-24
> **Xyus said:**
> Hi,

Whenever I type a Sudo command it asks for a password? 
If I type my login password in it tells me "incorrect" , I didn't have this in ubuntu so what's the issue?

Plz help me, 
xyus


First, check and make sure you don't have caps lock on. It gets the best of us. ><'; 

Second, possibly try changing your password? I know I've seen this come up somewhere else, and I can't remember what was done to fix the problem. D: Ah, Best of luck!

Edit: Aysiu beat me to it, also, that should work. ^^ Bleh, Good luck! Hope it works!

---

### Post by aysiu on 2006-08-24
Catewilliams brings up a good point--it is case-sensitive.
You may also just want to make sure you're typing your password correctly. The terminal gives no feedback, so you won't know unless you type very slowly.

---

### Post by Xyus on 2006-08-24
Hi,

If I type

```
 group 
```

admin shows up at the end, 
And I will change my password, maybe it will work.

btw how do I turn off autospelling?

Xyus

---

### Post by Xyus on 2006-08-24
Ok, 

it doesn't ask for a pass anymore it justs gives me immediately an error. :( 

if I type this command:
```
sudo chmod +x /usr/lib/amarok/install-mp3 
```

I get this error

```
can not get acces to `/usr/lib/amarok/install-mp3': unknown file
``` (I translated it from dutch to eng)

I get the feeling I'm the only one experiencing all these problems :( 
why doesn't it just work??

xyus

---

### Post by aysiu on 2006-08-24
Can you type ```
cd /usr/lib/amarok
ls
``` and post the output back here?

---

### Post by Xyus on 2006-08-24
Hiya

```
amarokapp  amarok_xmmswrapper2
```


whatever this means? 

xyus

---

### Post by aysiu on 2006-08-24
It means there's no file called *install-mp3* in that directory, so the *unknown file* error makes sense.

---

### Post by neotrumatrix on 2006-08-24
> **Xyus said:**
> Hiya

```
amarokapp  amarok_xmmswrapper2
```


whatever this means? 

xyus

ls just lists all the files in th directory u specify or pwd(present wrkin dir):)

---

### Post by Xyus on 2006-08-24
Ok,

I am trying to install MP3 play function on amarok and I got information of this page:

[http://amarok.kde.org/wiki/MP3_on_Kubuntu_6.06](http://amarok.kde.org/wiki/MP3_on_Kubuntu_6.06)

unless anyone else knows a good guide?

xyus

---

### Post by aysiu on 2006-08-24
> #

Kubuntu 6.06 LTS (Dapper Drake)

    *

      Install libxine-extracodecs.
    *

      To add mp3 support to K3b, install libk3b2-mp3.
    *

      To add mp3 support to JuK, install libakode2-mpeg and libarts1-mpeglib.
    *

      Video thumbnails in Konqueror -- install libarts1-xine. You can turn this functionality on and off through Konqueror's menu View->Preview->Video files.
    *

      Audio Previewing -- The Kubuntu file manager Konqueror can preview sound files if you hover your mouse pointer over the file (this can be enabled in Konqueror's menu under View->Preview->Sound files). If you would like to add this functionality for use with mp3 files, install libarts1-mpeglib. You'll need extra repositories:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources) will help you with that.

Then ```
sudo aptitude update
sudo aptitude install libxine-extracodecs
```

---

### Post by Xyus on 2006-08-24
Hi,

I totally deleted everything in the sources.list and just pasted the text on that website you supplied me. ok?

and thank allot!!

xyus

---

