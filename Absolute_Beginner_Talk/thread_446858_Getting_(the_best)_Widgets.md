---
title: "Getting (the best) Widgets"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-17
I'd like to add some widgets to my desktop (Ubuntu Edgy) and I was wondering what was the best program to use?  [[COLOR="Blue"]_Gdesklets_[/COLOR]]("http://www.gdesklets.de/"), [[COLOR="Blue"]_adesklets_[/COLOR]]("http://adesklets.sourceforge.net/"), and [[COLOR="Blue"]_opera_[/COLOR]]("www.opera.com") seem to be [[COLOR="Blue"]_the only contenders_[/COLOR]]("http://en.wikipedia.org/wiki/Comparison_of_widget_engines").  

Anyone have a preference for one over the others?

---

### Post by jba6511 on 2007-05-17
newbie here to but I am using screenlets and am pleased so far.

---

### Post by swatF1RESTORM on 2007-05-17
Another n00b here as well but I've been using gDesklets and have no complaints. Not really sure yet how to get the most out of my widgets but they function correctly and look nice.

---

### Post by revealer on 2007-05-17
i'm using kubuntu right now and superkaramba works great and has a pretty large amount of widgets.

---

### Post by mojo123 on 2007-05-17
i like gdesklets its very noob friendly

---

### Post by zhinker on 2007-05-17
thanks for your answers.  So I'm trying out gdesklets, but I'm running into problems...

Is it just me or do most of these desklets seem broken?  I can't get any of the weather desklets to work for one, the time ones have error messages popping up (I can tell it to ignore them) and the Rhythmbox desklet doesnt' seem to work either (or I just haven' figured out how to configure it properly)

---

### Post by Ender Black on 2007-05-17
I have the same problems with gDesklets.  Screenlets work for the most part for me right out of the box.  The "What's Playing" screenlet works beautifully with my Banshee, the weather screenlet is simple, and the system monitor one works as advertised.  I only really use weather to keep an eye on weather back at home since I am 5000 miles away right now and system monitor so I can keep a track of my memory usage.  <-  found some apps with horrible memory leaks that way.

---

### Post by Bakerman on 2007-05-17
There is a gDesklet called GoodWeather that works ok. You have to enter your region code, which you can get from weather.com

---

### Post by Inxsible on 2007-05-17
aDesklets have very few options in terms of number of desklets available. Well I guess over time they will increase.
 
One thing you might wanna consider is the amount of resources these desklets will take.
 
I have read that aDesklets is much lighter on system resources than gDesklets. Of course it also depends on the number of desklets that you run. I could see a weather one and system monitor one coming in use for me, but the date, time etc are just eye candy as you have that information already on your OS workspace itself.

---

### Post by Ateo on 2007-05-17
superkaramba. the rest just don't compare.

---

### Post by raul_ on 2007-05-17
what about screenlets?

---

### Post by Ateo on 2007-05-17
> **raul_ said:**
> what about screenlets?

We'll talk when they make it into the repositories. But I don't manually compile on my Ubuntu box as to keep things organized (don't confused this with incompetentcy). I also wouldn't expect a newcomer to linux to compile anything either.

So, I guess this really doesn't justify my answer since I haven't really invested any time into screenlets. I take the 5th on that... =)

> **mojo123 said:**
> i like gdesklets its very noob friendly

I do agree but superkaramba now has a GUI to drag and drop / install / launch themes. It's wonderful.

---

### Post by raul_ on 2007-05-17
> **Ateo said:**
> But I don't manually compile on my Ubuntu box as to keep things organized (don't confused this with incompetentcy).

I suggest you look for "checkinstall". I also didn't compile programs, in order to keep my packages organizaed, but checkinstall allows you to create a .deb package when you're compiling the program, making it easier to remove afterwards =) just a tip, maybe you already heard of it

It's just as simples as (typically):

./configure
make
checkinstall

---

### Post by zhinker on 2007-05-17
Thanks guys, I've been looking around these forums and heard a lot of good things about screenlets.  Could someone tell me how to install them?

---

### Post by toasterofirony on 2007-05-17
Go [here]("http://hendrik.kaju.pri.ee/screenlets/")

It's pretty self-explanatory. And no need to even ./configure, as there is a repo waiting to be added to your lists!

---

### Post by zhinker on 2007-05-17
Sweet, I'll try that when I get home.  Thanks

---

### Post by zhinker on 2007-05-17
I tried following their [instructions]("http://hendrik.kaju.pri.ee/screenlets/?q=node/5") but after adding the repository when I tried doing this command 
```
wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add - && sudo apt-get update
```
I ended up with this in the terminal and it wouldn't progress any further (I could turn it off easily, but I couldn't type anything in.)
```
zain@ip68-109-35-131Zain:~$ wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add - && sudo apt-get update
Password:--17:31:56--  http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
           => `-'
Resolving hendrik.kaju.pri.ee... 195.222.13.21
Connecting to hendrik.kaju.pri.ee|195.222.13.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,353 (1.3K) [text/plain]

100%[====================================>] 1,353         --.--K/s             

17:32:00 (129.03 MB/s) - `-' saved [1353/1353]
```

Any help?

---

### Post by raul_ on 2007-05-17
sudo apt-key add F854AFD7.gpg
sudo apt-get update

---

### Post by zhinker on 2007-05-17
> **raul_ said:**
> sudo apt-key add F854AFD7.gpg
sudo apt-get update

No go:

```
zain@ip68-109-35-131Zain:~$ sudo apt-key add F854AFD7.gpg
gpg: can't open `F854AFD7.gpg': No such file or directory

```

I even tried running sudo apt-get update before that code

---

### Post by raul_ on 2007-05-17
do those commands one by one:

```
wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
sudo apt-key add F854AFD7.gpg
sudo apt-get update

```

---

### Post by icechen1 on 2007-05-17
> **zhinker said:**
> I tried following their [instructions]("http://hendrik.kaju.pri.ee/screenlets/?q=node/5") but after adding the repository when I tried doing this command 
```
wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add - && sudo apt-get update
```
I ended up with this in the terminal and it wouldn't progress any further (I could turn it off easily, but I couldn't type anything in.)
```
zain@ip68-109-35-131Zain:~$ wget http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg -O- | sudo apt-key add - && sudo apt-get update
Password:--17:31:56--  http://hendrik.kaju.pri.ee/ubuntu/F854AFD7.gpg
           => `-'
Resolving hendrik.kaju.pri.ee... 195.222.13.21
Connecting to hendrik.kaju.pri.ee|195.222.13.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,353 (1.3K) [text/plain]

100%[====================================>] 1,353         --.--K/s             

17:32:00 (129.03 MB/s) - `-' saved [1353/1353]
```

Any help?
it worked for me when i added a SUDO before the command,i have the error without adding sudo

---

### Post by MoxJet on 2007-05-17
I don't know if you can call conky a widget, but it gives the same information on your desktop, and is highly customizable.

Lots of screenshots and valuable information here:
[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+post+your](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky+post+your)

---

### Post by zhinker on 2007-05-17
Sweet, it's working now.  Thanks guys! 

This stuff looks awesome, though I've already found a bug in their program (just an annoyance, should be an easy fix) and the temperature app isnt' working.  But overall it seems great!

---

### Post by SebbeJohan on 2007-05-23
Can Superkaramba be used in Gnome?

---

### Post by brandon079 on 2007-09-28
could someone post a mirror to F854AFD7.gpg the server is always down. I've been trying for a week.

---

### Post by hadeshorn on 2007-09-29
I think he changed the link to his key.

Its here now

[http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg)

---

