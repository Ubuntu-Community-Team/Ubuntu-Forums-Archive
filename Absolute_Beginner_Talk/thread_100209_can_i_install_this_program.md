---
title: "can i install this program?"
date: 2005-12-07
forum: Absolute Beginner Talk
---

### Post by Danielle on 2005-12-07
hi, i want to install this program but it says i need these

&#183; GTK >= 1.2.x
&#183; gcc

they look abit familiar to me but i suppose that's not really good enough. can you help me?

[http://linux.softpedia.com/get/Utilities/LightSword-Alarm-Clock-6076.shtml](http://linux.softpedia.com/get/Utilities/LightSword-Alarm-Clock-6076.shtml)

---

### Post by Perfect Storm on 2005-12-07
```

sudo apt-get install gcc libgtk1.2

```

---

### Post by Danielle on 2005-12-07
thanks, AI  O:)

---

### Post by Joe_CoT on 2005-12-07
what you really want is this

```
sudo apt-get install build-essential gcc gcc-3.4 libgtk1.2 checkinstall
./configure
make
sudo checkinstall
```

that way it'll make the deb file for you so you can easily remove it later.

---

### Post by Danielle on 2005-12-07
thanks, bobfnordman. i didn't realise they were libraries. i had them both already.

i was just going to install it now but i haven't got a clue how to install it :confused: when i unpack the archive there are two folders, then when i cd to one of them and try:
./configure 

i get this error:

:~/Desktop/lsalarm-manager$ ./configure
configure: error: cannot find install-sh or install.sh in . ./.. ./../..

when i looked in the readme it says to do this:
  If the precompiled SUSE binary does not work on your system, or
if you want to change the program, you'll have to build the source
code.

Run, configure and make.

can i complie a "SUSE binary"? or should i just do something like "make install"? thanks

---

### Post by Perfect Storm on 2005-12-07
Your explaination sounds a bit confusing...but it seems there isn't a config file. Are you sure it's made for compiling and not as a dynamic binary? Can you tell me which file it contains?

---

### Post by Perfect Storm on 2005-12-07
ok, I just downloaded and ran ./configure without any problems. Which ubuntu arch are you using? (x68, pcc, am64).
You could try to download it again, it might also be a bad download.

---

### Post by Perfect Storm on 2005-12-07
Now I know what's wrong when I checked your patch, instead of browse to **lsalarm-manager** you need to go to **lsalarm** and compile. That should work :)

---

### Post by Danielle on 2005-12-07
sorry for being slow, i was reading about why everyone has been fighting with each other, i had no idea :confused: 

thanks for all your help, AI :cool: i'll try it now. IT WORKED!!! thanks again, when i first posted i was going to ask which folder i should start in, i don't know why i didn't :rolleyes:

---

