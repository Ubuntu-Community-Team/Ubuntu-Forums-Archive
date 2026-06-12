---
title: "Good web server for Gutsy"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by dbraniff on 2007-12-25
Hello, I am looking at setting up a home server mainly for personal use, and am wondering what a good web server would be? Some one mentioned Lamp? Can I use Gutsy personal or do I need the server edition installed?

---

### Post by TidusBlade on 2007-12-25
I would recommend you install the Server Edition. Heard it would be better for a full time server for any use.

---

### Post by fatality_uk on 2007-12-25
> **dbraniff said:**
> Hello, I am looking at setting up a home server mainly for personal use, and am wondering what a good web server would be? Some one mentioned Lamp? Can I use Gutsy personal or do I need the server edition installed?

You can use Gutsy as your backbone for LAMP  **L**inux **A**pache **M**ySql **P**HP. In some respects it's easier as the server version of Ubuntu does not by default have a GUI.

All are available through the Synaptic Package Manager **System->Administration->Synaptic Package Manager**

Hope this helps

---

### Post by yknivag on 2007-12-25
Launch a terminal and type:

```
sudo apt-get install apache2
```

this should give you a working web server.

It will run using the desktop kernel, there's no need to install the server one.  However as TidusBlade says, if you're planning on running it full time then it's recomended.

---

### Post by Capricori on 2007-12-25
The 'personal' (I guess you mean Desktop?) and server editions are technically the same thing, but with different packages installed. As far as I know, the server edition is the same as the desktop, but it doesn't have X Windows installed (so command line only), and it does have LAMP (apache, mysql, php) installed. The desktop version does have X Windows installed (so you have a GUI), but it doesn't have LAMP installed.

You can easily start from one and add/remove packages to get what you want. If you're fairly new to Linux, you might be better with a Desktop installation, so you can get used to it, before you have to use the command line.
If you are fairly competent, you can then remove all the GUI stuff, since the GUI uses a load of CPU cycles, and you probably want them for your server :)

Regards, 

Capricori

---

### Post by fatality_uk on 2007-12-25
> **Capricori said:**
> The 'personal' (I guess you mean Desktop?) and server editions are technically the same thing, but with different packages installed. As far as I know, the server edition is the same as the desktop, but it doesn't have X Windows installed (so command line only), and it does have LAMP (apache, mysql, php) installed. The desktop version does have X Windows installed (so you have a GUI), but it doesn't have LAMP installed.

You can easily start from one and add/remove packages to get what you want. If you're fairly new to Linux, you might be better with a Desktop installation, so you can get used to it, before you have to use the command line.
If you are fairly competent, you can then remove all the GUI stuff, since the GUI uses a load of CPU cycles, and you probably want them for your server :)

Regards, 

Capricori

Yeah what I just said :lolflag:

---

### Post by Capricori on 2007-12-25
> **fatality_uk said:**
> Yeah what I just said :lolflag:
I know, but it took me a while to type, you got there first :) Congrats :P

---

### Post by fatality_uk on 2007-12-25
> **Capricori said:**
> I know, but it took me a while to type, you got there first :) Congrats :P

No worries. I bow to your post as it was far more detailed! :)
Having drunk and etaen like a whale today, I was just being lazy! :lolflag:

---

### Post by Capricori on 2007-12-25
Wasn't really more detailed, I just take more words to say the same thing :)

> **fatality_uk said:**
> Having drunk and etaen like a whale today, I was just being lazy! :lolflag:

Tis the season! :)

---

### Post by dbraniff on 2007-12-26
AThanks all for the advice. Yeah I am just playing with linux for the time being. In the end I want to set it up as a media center. but right now just getting the hang of it

---

### Post by louieb on 2007-12-26
I got a P4 2.1gHz 1GB men. After installing Ubuntu, I used this to install a Lamp server
[ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Took a little tweaking  but the result is this:  [Lou's Home Server Stuff]("http://louieb.isa-geek.net/")

:guitar:Running the lamp server doesn't seem to slow the desktop down any. Of course my little web playground doesn't get hit hard.

---

### Post by dbraniff on 2007-12-26
After I installed apache I went to test it out just by typing apache2 in the terminal and I et this error 

> $ apache2
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs


after I added ServerName localhost to httpd.conf 

By teh way httpd.conf was empty.

Is there somethign i am doing wrong

---

### Post by louieb on 2007-12-26
The file you want is /etc/apache2/apache2.conf.

---

