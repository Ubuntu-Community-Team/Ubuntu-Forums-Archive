---
title: "Installing Software"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by U-b-u-n-t-u on 2008-02-17
Hi

I have downloaded Flash 4 Linux and extracted it but I cannot figure out how to install it!

Can you help.

Thanks

---

### Post by timbounceback on 2008-02-17
fire up a terminal and run ```
sudo apt-get install build-essential
```; change into the directory with ```
cd
```, and post the contents of the directory via ```
ls
```

---

### Post by U-b-u-n-t-u on 2008-02-17
Thanks for the quick reply, not I'm how to "fire up a terminal"???

Thanks

---

### Post by Joeb454 on 2008-02-17
Applications>Accessories>Terminal :)

---

### Post by zerhacke on 2008-02-17
> **timbounceback said:**
> fire up a terminal and run ```
sudo apt-get install build-essential
```; change into the directory with ```
cd
```, and post the contents of the directory via ```
ls
```

Ther'es no need to install build-essential to install the flash plugin.

Either go to Adobe's site and download the tar.gz file, unziip it, open the terminal, cd to the appropriate directory and then ./flashplayer-installer, or

sudo apt-get install flashpugin-nonfree

---

### Post by Aurora@FleetBuzz on 2008-02-17
Did you try the Synaptic Package Manager?  It does the "heavy lifting" by downloading & installing.  Do a search and see if it's available there.

---

### Post by U-b-u-n-t-u on 2008-02-17
Thanks for your help, I don't want Flash Player I want the Program 'Flash 4 Linux':)  

I did try that thing but it is a little weired!  Is there an easy way to do it?

Thanks

---

### Post by kaiju on 2008-02-17
i did a quick seach for it, but it doesn't seem to be in the repositories.
in this case you either find a .deb package of it and install that with dpkg, or you'll have to compile it yourself from the source code available on the project's homepage.
so i'm afraid that the answer to your question is: no, there is no "easy" way to do it.
but don't give up, you will need the 'build-essential' package, and the rest is usually specified in the readme file of the source code.

---

### Post by zvacet on 2008-02-17
It is f4l-0.2.1.tar.bz2 isn´t it?Right click on package and select unpack here.That will make folder.Go to that folder and find **install file**.In that file are instructions how to installl it.If right click for unpacking doesn´t work for you type in terminal

```
sudo apt-get install rar unrar p7zip p7zip-full
```

---

### Post by U-b-u-n-t-u on 2008-02-17
Thanks allot for your help, I can find that file but the instructions are a bit over my head!  I will have to get a book on linux or something!

Thanks for your help.

---

### Post by wolfen69 on 2008-02-17
nice name btw. i'm surprised no one had taken it already.

and welcome to the forums.  :-)

here is a good place to start. [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/) take your time with it.

---

### Post by U-b-u-n-t-u on 2008-02-17
Thanks, and thanks for the link:)

I will see what I can do.

Thanks

Adam

---

### Post by uberlube on 2008-02-17
If you would like to learn how to install ANYTHING in ubuntu check this out:

[http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

It has it all! Enjoy! :)

---

### Post by legend2440 on 2008-02-18
Here are instructions for compiling f4l
[http://www.uira.org/gpl/f4l/debian.php](http://www.uira.org/gpl/f4l/debian.php)

However, haxe seems to be a better or at least newer option for creating swf files you can embed in web pages and it is already in Synaptics under name haxe

Here is haxe web page with tutorials
[http://haxe.org/](http://haxe.org/)

---

