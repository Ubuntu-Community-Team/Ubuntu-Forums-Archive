---
title: "Kopete + Jasper + Webcams..."
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by bladefallcon on 2006-10-04
Ok...doing some looking around, I had heard that Kopete supported Webcams. This is important to me, because i view and brodcast webcams with friends and family around the country. So I installed Kopete from the "Add/Remove Programs" and tried it out. Sure enough, it would seem to have limited support for webcams. Specifically, it tries to view the cams. But when it does, it tells me this:

Jasper image conversion program not found.

jasper is required to render the Yahoo webcam images.

Please go to [http://www.ece.uvic.ca/~mdadams/jasper/](http://www.ece.uvic.ca/~mdadams/jasper/)


So, I visited that website, and downloaded it. Thing is, being new with linux, and still not very familiar with installations and such (other than just going into "Add/Remove" and doing it that way). So what I am looking for, is some help with installing this Jasper thing, and getting it to work with Kopete, so I can use web cams again. 

Before you suggest it, let me tell you this: I have Gyachi, and currently I use that for webcams. I use Gaim for chatting though. I tried using Gyachi for chatting as well, and just cant do it. I just hate the look of it..Plus its easier to have one program, running all my IMs..yahoo, aim, icq...etc..Kopete does this just as well as Gaim (looks a little better too) All I need is to find a way to get it to work with webcams.

If anyone can help out...or point me to a place with a guide for this...it would be greatly appreciated.

---

### Post by maxime94 on 2006-10-04
The instructions are in a pdf in the doc folder of the downloaded sources. It's the same as any app, ./configure, make, sudo make install.

---

### Post by bladefallcon on 2006-10-04
> **maxime94 said:**
> The instructions are in a pdf in the doc folder of the downloaded sources. It's the same as any app, ./configure, make, sudo make install.

that does not help me at all...As I said, I am new with this, and do not know  much about how to install things. saying "./configure, make, sudo make install" means nothing to me...

---

### Post by Dinerty on 2006-10-04
The basic install of any program via source is this:

Fire up the terminal batman !

Applications > Accessories > Terminal

then download the file to your desktop and

```
 cd Desktop 
``` in terminal

then

```
 cd <jasperFileNameHere> 
```

then

```
./configure 
```

then

```
make 
```

then

```
sudo make install
```

Hopefully this works, but you may recieve errors regarding dependicies (Packages which are missing which are needed to make the program works)

If you have missing dependicies, try and search for them in synaptic package manager first, then search the forum and if not make a thread

---

### Post by bladefallcon on 2006-10-04
Ok...Everything was working fine (as far as i can tell) until i got to the ```
make
```

That simply gave me 

```
blade@Blade2:~/Desktop/jasper$ make
bash: make: command not found

```

Now what?

---

### Post by Dinerty on 2006-10-04
```
sudo apt-get install build-essential
```

---

### Post by bladefallcon on 2006-10-04
thank you so much...It worked just right, and i am now viewing a web cam via kopete...now for one final question..any chance you, or someone could give me a brief explanation of what it is i just did? lol

---

### Post by Dinerty on 2006-10-04
You just compiled your first program from source, which can be a handful if dependecies all go wrong.

Welcome to the world of Ubuntu

---

### Post by bladefallcon on 2006-10-04
OK...so i understand that the sudo thing gives root privaleges to whatever command comes after it (hense having to enter my password after using it..)

but what exactly does:
```
apt-get install build-essential
```
do? or: 
```
make install
```
?

```
./configure
```
im assuming that one is just running the configuration file that is in the directory that i went to....right?

---

### Post by Dinerty on 2006-10-04
> **bladefallcon said:**
> OK...so i understand that the sudo thing gives root privaleges to whatever command comes after it (hense having to enter my password after using it..)

but what exactly does:
```
apt-get install build-essential
```
do? or: 
```
make install
```
?

```
./configure
```
im assuming that one is just running the configuration file that is in the directory that i went to....right?

```
apt-get build-essential
```

build-essential is used for debian packages and needed to compile programs

```
./configure
```

./configure is used to create the make file, it basically looks for dependecies, here it tells you if things are missing

```
make install
```

This basically installs the program you just compiled, if the package comes with a un-installer you can also uninstall it by:

```
sudo make uninstall
```

but don't be surprised if you get errors as the programmers needs to have included this

---

### Post by bladefallcon on 2006-10-04
Thank you for the explanation...I appreciate it. It is good to know someone out there is willing to not just give answers, but explain them as well. I am learning Linux slowly, but with the help of people like you, I *AM* learning it..

---

### Post by Dinerty on 2006-10-04
> **bladefallcon said:**
> Thank you for the explanation...I appreciate it. It is good to know someone out there is willing to not just give answers, but explain them as well. I am learning Linux slowly, but with the help of people like you, I *AM* learning it..

Glad I can help, this is a friendly place and most people will try there best to help

---

