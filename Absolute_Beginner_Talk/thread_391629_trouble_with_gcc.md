---
title: "trouble with gcc"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by kingpoiuy on 2007-03-23
Ok I have done quite a bit of searching around the forums to figure this out but have not come across the answer yet.  

I installed ubuntu 6.06 on a spare computer at work hoping to migrate over to it completely.  It's awesome, I love it.  But when I found a program that our company does not have for unix I decided to install WINE.  When I did the ./configure for wine it said I didn't have gcc or cc.  So I went to download the latest gcc (my synaptic says i already have gcc but #whereis gcc says I don't) So i downloaded the binary and tried to compile it.  I guess I need gcc in order to install gcc.  

I'm confused at this point.  Any help out there?

thanx

---

### Post by taurus on 2007-03-23
You need the build-essential package.  From a terminal, run

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by mahy on 2007-03-23
You can install install gcc and everything related by

sudo apt-get install build-essential

But you DON'T NEED it. Just do:

sudo apt-get install wine

And you're done

---

### Post by YokoZar on 2007-03-23
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

### Post by kingpoiuy on 2007-03-23
Wow, what a reply!  Love the forums sofar. 

I guess it turns out that it is the proxy keeping me from using the get-apt stuff.  On my windows box i can put in a username and passoword to get around it and I have setup the autoproxy on ubuntu but with no success.

I will try yokozar's suggestion for now but i would be intrested in more infomation on setting up proxy stuff in ubuntu.

---

