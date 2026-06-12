---
title: "Privoxy and modifying a file"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by seshomaru samma on 2005-11-12
I'm trying to install Tor and Privoxy and have followed the instructions[ here ]("http://tor.eff.org/cvs/tor/doc/tor-doc-unix.html"): (step two)
which asks me to add a line to a Privoxy file. I change the ownership of  the 'config' file from root to user because the file was read-only and it didn't let me modify it . I can now modify the file but it still wont let me save the changes saying “Error: could not save the file”
Any suggestions?

---

### Post by apjone on 2005-11-12
first off change the ownership back to root.the reason you could not save after taken ownership is although you have access to that file , the folder it is in still belongs to root and you do nothave right access to the folder. Then as i think you are using gedit not vi, so open a terminal

1) type 'sudo bash'
2) put your password in
3) 'cd' to the directory where the config file is 
4) gedit configfile

---

### Post by seshomaru samma on 2005-11-12
it worked thanks

---

### Post by apjone on 2005-11-12
cool , i started using linux in febuary . but you learn stuff like that quik enough

---

### Post by EvilBill on 2005-11-22
I installed tor and Privoxy, with Synaptic Package Manager. I cannot seem to find either one.

> 3) 'cd' to the directory where the config file is 

huh?:???: 

I have installed a couple things with the terminal, [Java, Codecs] but I'm not having much luck here.

Does anyone know what the comand lines would be, where I can find these things to do whatever it is I have to do?

---

### Post by cdhotfire on 2005-11-25
[quote=EvilBill]I installed tor and Privoxy, with Synaptic Package Manager. I cannot seem to find either one.



huh?:???: 

I have installed a couple things with the terminal, [Java, Codecs] but I'm not having much luck here.

Does anyone know what the comand lines would be, where I can find these things to do whatever it is I have to do?[/quote]

what are you not finding?

to start them up, just do

```

$ sudo /etc/init.d/tor start
$ sudo /etc/init.d/privoxy start

```

to edit config file for tor do

```

$ sudo gedit /etc/tor/torrc

```

for privoxy go to your browser and type

[http://config.privoxy.org/](http://config.privoxy.org/)

---

### Post by EvilBill on 2005-11-27
I got the 2 started but everytime I try the link for Privozy it says

> Privoxy is not being used

The fact that you are reading this page shows that Privoxy was not used in the process of accessing it. Had the request been made through Privoxy, it would have been intercepted and you would be looking at Privoxy's web-based user interface now.

This is very frustrating. I put the #'s in like they said, but no luck. I have been working on this for days, off & on. I am batting .000 :( 

[http://tinypic.com/hv74f8.png](http://tinypic.com/hv74f8.png)

---

### Post by poptones on 2005-11-27
Did you set your browser to use a proxy server? Edit>preferences>connections>connection settings. "Specify a proxy server" and Make sure it says "localhost" in the boxes on the left, 8118 in the boxes on the right.

---

### Post by EvilBill on 2005-11-27
[QUOTE=poptones]Did you set your browser to use a proxy server? Edit>preferences>connections>connection settings. "Specify a proxy server" and Make sure it says "localhost" in the boxes on the left, 8118 in the boxes on the right.[/QUOTE]

[This is what I have now](http://tinypic.com/hv8g9l.png), following your post as best as I can understand it. I even re-booted before trying it out.

---

### Post by towsonu2003 on 2005-11-27
change "local host" to this: 
127.0.0.1

that should work... its ip# of your "localhost"

---

### Post by EvilBill on 2005-11-27
[This is what that gives me](http://tinypic.com/hv9bmd.png)

---

### Post by EvilBill on 2005-11-27
Anyone have any tips or suggestions as to what files, I need to modify or whatever, to get this seemingly impossible to work item to actually work? ;) 

I am going to keep trying to get this thing to work if it takes me 6 months of tinkering around. :eek:

---

### Post by EvilBill on 2005-11-28
I got it to work...........:p

---

