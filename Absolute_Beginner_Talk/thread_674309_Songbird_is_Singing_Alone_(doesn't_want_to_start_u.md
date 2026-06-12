---
title: "Songbird is Singing Alone (doesn't want to start up)"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by Sugi on 2008-01-21
Songbird doesn't want to start up.  I don't understand why it's not starting up or doesn't show any errors.

> LongPICKLE@LongPICKLE:~$ /opt/Songbird/songbird
LongPICKLE@LongPICKLE:~$ 

and when I go into the folder /opt/Songbird/
and click on it. Nothing happens.

Once though, and I mean Once I got Songbird to tell me that there is another instance of Songbird already open.  I couldn't see that instance of Songbird, but at least I know Songbird isn't dead.

How Do I get Songbird to start up?

---

### Post by Sugi on 2008-01-21
Songbird needs you.
##BUMP##

---

### Post by Sugi on 2008-01-22
##bump##

---

### Post by Sugi on 2008-01-24
**bump**

---

### Post by Sugi on 2008-01-28
**bump**

---

### Post by billgoldberg on 2008-01-28
Ok, I don't know how you installed it but [check this out]("http://linuxowns.wordpress.com/2008/01/16/songbird-04/") on how to install it and add it to the "sound and video" menu.

Hope this helped.

---

### Post by j.miller565 on 2008-01-28
try:

```

cd /opt/Songbird/
```

then type:

```
./songbird 
```


or try 

```
./opt/Songbird/songbird
```

remember the fullstop behind the /



hopefully this helps :)

---

### Post by cubeist on 2008-01-28
Sugi, Please remember to edit your phallic username terminal prompt when making an online post.  What you do on your own system is your business, but online communities have a wide array of members which may find your username rude and offensive.

---

### Post by Lypsis on 2008-03-07
Experienced the same problems as you Sugi. Both on X/Ubuntu and even on Zenwalk Linux. (Have to note: these problems only happened with Songbird 0.4)

What helped is simpyl copy the Songbird folder into your **home** directory and then start ./spicebird from there.

Hope this will work for you, too!


***[RIGHT]Have a nice day![/RIGHT]***

---

