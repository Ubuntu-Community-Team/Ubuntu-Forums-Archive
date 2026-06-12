---
title: "public key problem with Easyubuntu"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by moshuptrail on 2006-11-06
After installing Easyubuntu (following the directions on the website) when I try to run it I get:

```
Reading package lists...

error: 
error: 
error: 
W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
error: 
error: 
error: 
W: GPG error: http://easyubuntu.cafuego.net main Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 580E2519969F3F57
error: 
error: 
error: 
W: You may want to run apt-get update to correct these problems
```


I tried running sudo apt-get update, but it returns:

```
W: GPG error: http://easyubuntu.cafuego.net main Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 580E2519969F3F57
W: You may want to run apt-get update to correct these problems
```

aaarrghh!

](*,)

suggestions?

---

### Post by Ecthelion on 2006-11-06
They say you need to do

```
wget http://easyubuntu.cafuego.net/969F3F57.gpg -O - | sudo apt-key add -
```

after installing easyubuntu...

Did you do this?

Info found on [this page]("http://easyubuntu.freecontrib.org/get.html")

---

### Post by moshuptrail on 2006-11-06
Well yes, but...
When I would run that command it would stop and not complete.  So I was hitting enter and it would come back to the prompt.  Tonight I tried again just for grins, and when it stopped I typed "qwerty" and it didn't echo, and when I hit enter, it said "sudo: 1 incorrect password attempt".  BINGO! - It's not prompting for password.
So I entered the correct password and it said "OK".

That seems to fix it.  Thanks!

---

