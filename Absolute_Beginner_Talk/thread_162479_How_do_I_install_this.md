---
title: "How do I install this?"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by Russty of Oz on 2006-04-19
Hi,

I have downloaded GRadio and want to install it but as I haven't yet grasped how to install programs without Automatix or Synaptic, I am stumped!  I tried typing the following into the terminal, but it came back with an error, something about a "child 2"????  Does anyone know what I am suppose to do?


1) Untar the source code:

	$ tar xzvf gradio-VERSION-src.tar.gz

Thanks,

Russty.

---

### Post by Sutekh on 2006-04-19
Installing software from source is a big step up.  Try this link for your first port of call

[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php) (Section 4 - Installing from Source)

Have you sorted out the dependant packages yet?

---

### Post by mips on 2006-04-19
No need to install from source.

I found Gradio in Dappers repositories so it can be installed via synaptic/adept etc. if you have the correct repositories enabled.

Have you enabled your universe & multiverse repositories ??
The Gradio package can be found in the universe repositories. Once you enabled the universe repositories you can install via synaptic.

Alternatively you can download the .deb file from here, [http://rpm.rutgers.edu/repository/ubuntu/pool/universe/g/gradio/](http://rpm.rutgers.edu/repository/ubuntu/pool/universe/g/gradio/)
and install it with **sudo dpkg -i gradio_1.0.1-6_i386.deb**

---

### Post by bikeboy on 2006-04-19
GRadio can be installed via synaptic or apt-get, but it's in the Universe repository. To see how to add the Universe repo check out this link:

[https://wiki.ubuntu.com/AddingRepositoriesHowto?](https://wiki.ubuntu.com/AddingRepositoriesHowto?)

Then to install GRadio, open up Synaptic, search for gradio, right click it > mark for installation > apply. Everything will be done automatically from there.

Alternatively, if you want to use a terminal type ```
 sudo apt-get install gradio 
```

---

### Post by Russty of Oz on 2006-04-19
OH!!  I have no idea what the "universe & meltiverse repositories" are?!?!  I am not sure what "dependant packages" are either?!?!  I think I will leave all that alone for the moment.  I will have to do some reading, that link that Sutekh gave looks like what I need, so I will study it.  I guess when you get used to all this it seems easy, but for someone who has been using Windows and got used to just clicking .exe files, it is all a bit daunting.  Still, I like what I see so far, and will perservere with it.  

I will give that link that mips gave a go first.

Thanks for you help.  I will let you know what (if anything) happens.

Russty.

---

### Post by Russty of Oz on 2006-04-19
That .deb file didn't work.  

I looked in the Synaptic section and found Gradio there, so I told it to install it, and it then did its bit and said it was installed.  But I can't find it anywhere!

---

### Post by mips on 2006-04-19
try it from the command line, ie gradio.

Might have to add it to the menu manually.

---

### Post by Russty of Oz on 2006-04-19
Command line??  I typed it into the Terminal, is that what you mean?  It said "bash: gradio; comand not found"

---

### Post by bikeboy on 2006-04-19
In a terminal, try ```
sudo find / -name "gradio"
```

---

### Post by Russty of Oz on 2006-04-19
Thanks bikeboy!  That found it.

I will have to really read up on how to use this thing.  It is so much better than MS but requires one to be knowledgable in computer jargon.  What FUN!

---

