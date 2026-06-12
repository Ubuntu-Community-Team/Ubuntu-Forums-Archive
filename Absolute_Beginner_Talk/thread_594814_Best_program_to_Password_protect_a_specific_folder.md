---
title: "Best program to Password protect a specific folder?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by Wiebelhaus on 2007-10-28
I don't want to necessarily encrypt it , I just want to password protect Mom & Dads stash.


Thanks.

---

### Post by julian67 on 2007-10-28
Easiest way to retain privacy is to run different accounts for different users. Other users (unless they have admin access) would not be able to read your Documents folder. Fast user switching makes this very easy. If you don't want to create another account then have a look at [cryptkeeper]("http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html") which is a nice tray applet for creating password protected stashes using encryption.

[IMG]http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper/cryptkeeper1.png[/IMG]

---

### Post by Wiebelhaus on 2007-10-28
> **julian67 said:**
> Easiest way to retain privacy is to run different accounts for different users. Other users (unless they have admin access) would not be able to read your Documents folder. Fast user switching makes this very easy. If you don't want to create another account then have a look at [cryptkeeper]("http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper.html") which is a nice tray applet for creating password protected stashes using encryption.

[IMG]http://www.tomatarium.pwp.blueyonder.co.uk/cryptkeeper/cryptkeeper1.png[/IMG]

thanks.

---

### Post by Crafty Kisses on 2007-10-28
That's pretty cool, thanks!

---

### Post by daimaru on 2007-10-28
i would recommend encfs ( sudo apt-get install encfs ) very easy to use file encryption that grows as is needed. u only need to add your user to the "fuse" group (administration --> users and groups after installing it log out and back in to make it  take effect and then you can use encfs form terminal by typing encfs . first time you run it it asks you to specify the folders and stuff i used the default ones that are listed in the example so i got a "crypt folder" and a hidden " .crypt " folder in my home dir. the crypt folder is the one where your unencrypted files show up and the .crypt one is the one with the encrypted ones. so after you copy stuff into the crypt folder they get automatically encrypted and are placed in the .crypt and when u run encfs enter your password your files show up again in the crypt folder.. easy :) 

Example:

```

    encfs ~/.crypt ~/crypt

```
enter password
after your  done type 
```
fusermount -u ~/crypt
```
and your files dont show up in the crypt folder anymore

hope that helps

---

### Post by julian67 on 2007-10-28
> **daimaru said:**
> i would recommend encfs ( sudo apt-get install encfs )

cryptkeeper is a gui frontend to encfs

---

### Post by Wiebelhaus on 2007-10-28
> **julian67 said:**
> cryptkeeper is a gui frontend to encfs


makes sense , thanks.

---

### Post by daimaru on 2007-10-28
> **julian67 said:**
> cryptkeeper is a gui frontend to encfs

oh cool didn't know that thx i'll give it  a try

---

### Post by llamakc on 2007-10-28
This is a cool feature I was unaware of. Thanks for the info.

---

### Post by Chibi-Tatsu on 2007-11-27
Is there a Gutsy build for cryptkeeper, or will the Feisty one function?

---

### Post by julian67 on 2007-11-27
Feisty one works fine

---

### Post by faical117 on 2008-03-02
waw !!! thanks :lolflag:

---

