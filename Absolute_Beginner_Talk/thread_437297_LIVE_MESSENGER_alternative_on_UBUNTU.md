---
title: "LIVE MESSENGER alternative on UBUNTU?"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by croxi on 2007-05-08
I´m a big fan of using IM and I wonder if there is a program on UBUNTU 7.04 that means I can use video and sound like on Live Messenger 8.0 

I know some of you will say "why don't you just use M$oft and stop bothering us with such silly questions?!" but I want to know if there is a way for me to be able to make it work so I don't have to ever use Windoze again. 

Also, is there a program that I can use that will enable me to control a network. I own and run a cybercafe and I am sick of having to keep turning off certain programs on my network so that others can open their webpages on the same network. I know some P2P programs hog the bandwidth and that means that others can't get a smelling of the net. 

If there is anything out there, that would make my life that little bit easier.

---

### Post by Iceni on 2007-05-08
" I know some of you will say "why don't you just use M$oft and stop bothering us with such silly questions?!" but I want to know if there is a way for me to be able to make it work so I don't have to ever use Windoze again."

I doubt you'll get that answer here :)

And I belive aMSN can do the video chat thing.

---

### Post by mikewhatever on 2007-05-08
Have you tried aMSN yet? You cat add with Add/Remove function. I don't think it has video support though, not quite sure about that.

---

### Post by Mazza558 on 2007-05-08
> **mikewhatever said:**
> Have you tried aMSN yet? You cat add with Add/Remove function. I don't think it has video support though, not quite sure about that.

The very latest Nightly build has video chat IIRC.

---

### Post by croxi on 2007-05-08
is that on synaptic?

---

### Post by Iceni on 2007-05-08
> **croxi said:**
> is that on synaptic?

Not the very last nightly build, no :)

You'll have to download the latest development SVN snapshot:
[http://amsn-project.net/download.php](http://amsn-project.net/download.php)

and probably compile it yourself. Compiling sounds scary, but it's easy:)

---

### Post by croxi on 2007-05-08
well, I don't want to sound really THICK but I don't even know what "compile" means, as you can probably tell by my current bean count. 

I really haven't a clue how to compile anything, let alone anthing more than a random thought pattern!!

---

### Post by moredhel on 2007-05-08
compiling it should be simple.

I don't have to time fully explain so any other people on here please extend this ;)

First, download the file (probably either .tar.bz2 or .tar.gz)

find this (downloading it to the desktop would be simplest) and right click on it, then click extract here.

then go to:

applications > accessories > terminal

and type:

cd Desktop (remember the capital D)

then type cd msn (it should of extracted it to a folder called msn automatically)

then type:

./configure

wait for that to finish

then type:

make

wait for that

then type:

make install.


It will most probably say some error in the ./configure part, but i don't have time to help you with that part, so hope someone else will ;) Just post what it says and someone will.

---

### Post by gigaferz on 2007-05-08
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

how to install things in ubuntu

---

### Post by Iceni on 2007-05-08
Okai, that was annoying:) I just went thru the installation and compiling, here are the steps:

1. Downloading the latest SVN: [http://amsn-project.net/download.php](http://amsn-project.net/download.php)
- Unpack it into your home directory

Now open a terminal. Remember to paste something in the terminal you have to use ctlr+shift+v

2. Installing annoying dependencies:
```
sudo apt-get install tcl8.4-dev tk8.4-dev libpng12-dev libjpeg62-dev
```

3. go to the directory:
```
cd msn
```

4. Installing things for compiling:
```
sudo apt-get install build-essential
```

5. Compiling!
```
./configure
```
*Lots of text scrolling by. If you get errors post them here. If not, proceed*

```
make
```
*If no errors be happy and proceed*

```
sudo make install
```
*type "amsn" to run it now *


Hope this helps!

---

### Post by t3roriz3r on 2007-05-08
Im goin to try and install this now myself......fingers crossed!! :)

---

### Post by t3roriz3r on 2007-05-08
I was doing fine until the last point then i got this error: -

```
ian@ian-laptop:~/Desktop/msn$ make install
rm -Rf /usr/share/amsn
mkdir --parents /usr/share/amsn
mkdir: cannot create directory `/usr/share/amsn': Permission denied
make: *** [install] Error 1

```

Have i done something wrong?

Thanks

---

### Post by Iceni on 2007-05-08
> **t3roriz3r said:**
> I was doing fine until the last point then i got this error: -

```
ian@ian-laptop:~/Desktop/msn$ make install
rm -Rf /usr/share/amsn
mkdir --parents /usr/share/amsn
mkdir: cannot create directory `/usr/share/amsn': Permission denied
make: *** [install] Error 1

```

Have i done something wrong?

Thanks

```
sudo make install
```

that should do it :)

---

### Post by t3roriz3r on 2007-05-08
> **Iceni said:**
> ```
sudo make install
```

that should do it :)

Yeah thats me thanks :)

---

### Post by t3roriz3r on 2007-05-08
Got program started but says i need TLS module?

Which one do i pick?

---

### Post by Iceni on 2007-05-08
> **t3roriz3r said:**
> Got program started but says i need TLS module?

Which one do i pick?

My guess is the "tcltls" is the correct one. Check if you have that installed, otherwise install it. Weird that I didnt get that..

---

### Post by t3roriz3r on 2007-05-08
Sorted now if anyone else encounters this you need this

[http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/tcltls_1.5.0-3~neto1-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/tcltls_1.5.0-3~neto1-3v1ubuntu0_i386.deb)

---

### Post by nwadams on 2007-05-08
see, i don't know about you gusy but i'm gonna try using wine to make windows live messenger itself work...however so far i've gotten it installed but been unable to execute the program

---

### Post by Iceni on 2007-05-08
> **nwadams said:**
> see, i don't know about you gusy but i'm gonna try using wine to make windows live messenger itself work...however so far i've gotten it installed but been unable to execute the program

[http://appdb.winehq.org/appview.php?iVersionId=5264](http://appdb.winehq.org/appview.php?iVersionId=5264)

---

### Post by Homebrew on 2007-05-09
i followed the instructions posted on page one and I was able to download the source, unpack, complie and install without a hitch.  Kudos to everyone involved in making this such a painless process.

MSN working  through Linux.  Mwuahahahahahaha!

---

### Post by lethu on 2007-05-12
Why compile when you can simply apt-get it : ).
The latest aMSN version is available via the [Automatix]("http://www.getautomatix.com/wiki/index.php?title=Main_Page") repositories, in other words you can easily apt-get install it by simply following five* easy/quick steps, go [here]("http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt"), follow the steps till the fifth one if you don't want to install Automatix2 (you can install all the apps proposed by Automatix2 via regular Synaptic/apt-get) then install aMSN with your favorite package manager (you won't find the latest aMSN nor any other newly added repository apps via the Applications --> Add/Remove menu).
[COLOR="DarkOrange"]Note[/COLOR] : Scroll through the mentioned link/page above for Ubuntu versions other than Feisty.
Have a nice day : ).

---

### Post by jiminycricket on 2007-05-12
Kopete can do video chat, it's in the Ubuntu repository.

> 
Also, is there a program that I can use that will enable me to control a network. I own and run a cybercafe and I am sick of having to keep turning off certain programs on my network so that others can open their webpages on the same network. I know some P2P programs hog the bandwidth and that means that others can't get a smelling of the net.


iptables is built into the Linux kernel.  Are you running those computers as thin clients, or do you have a Linux gateway or what?

---

### Post by Noctiferis on 2007-05-16
Hi I am a noob with linux and was trying to follow your advice but it tells me it cant unpack the file...
Please Help
 Thanks!

---

### Post by Noctiferis on 2007-05-16
> **Noctiferis said:**
> Hi I am a noob with linux and was trying to follow your advice but it tells me it cant unpack the file...
Please Help
 Thanks!

Ok i fixed everything .. thx!

---

