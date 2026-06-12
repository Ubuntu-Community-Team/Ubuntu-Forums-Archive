---
title: "Loging screen is replaced by some other window"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by maduranga on 2007-11-09
I don't get logging screen after booting ubuntu. I get some other (logging type) window instead of the ordinary logging window. It maybe remote logging or anyother thing. Can someone help me?

---

### Post by TadH on 2007-11-09
system  > administration > login window > u can make the window whatever u want to!

---

### Post by maduranga on 2007-11-09
I cant do anything like that cos I cant log in! I don't get the usual logging window. 

 the window now i get includes a text input area and an add button. And it talks about local host.

Any idea?

---

### Post by jingo811 on 2007-11-09
> **maduranga said:**
> I cant do anything like that cos I cant log in! I don't get the usual logging window. 

 the window now i get includes a text input area and an add button. And it talks about local host.

Any idea?

What's wrong with a text input login?  It' like Microsoft DOS time.  Can't you just type in your username and when it asks type in your password?

Sounds like your Graphical login manager is gone to me.  
```
$ rcconf
```

select GDM install it, reboot.  But why use GDM?  Text login makes your Ubuntu boot 2 minutes faster.

---

### Post by maduranga on 2007-11-09
> **jingo811 said:**
> What's wrong with a text input login?  It' like Microsoft DOS time.  Can't you just type in your username and when it asks type in your password?

Sounds like your Graphical login manager is gone to me.  
```
$ rcconf
```

select GDM install it, reboot.  But why use GDM text login makes your Ubuntu boot 2 minutes faster.

Ah nothing wrong with a text input login. But what I'm getting is something completely different from what you a talking about.

 It doesn't ask for a use name or password. It ask for a Local Host. and when i type my usename, it says "unable to find the local host" or something similar.

I'm not sure what it is. maybe something related with Remote Logging.

---

### Post by jingo811 on 2007-11-09
Hard to say what it is if you don't print out what your screen says.  You could use a piece of pen and paper and write down what you see.  That way ppl will know what you're talking about.

---

### Post by maduranga on 2007-11-09
> **maduranga said:**
> 

 the window now i get includes a text input area and an add button. And it talks about local host.

Any idea?

Cant print the screen. thats what i see. line quoted above says something about what i get. And it clearly says that what i get is not the usual logging screen

---

### Post by jordanmthomas on 2007-11-09
I know what screen you're referring to.  Unfortunately, I am not at a Linux box at the moment.

Try looking for a button labeled action or pressing F10 and see if you can get back to the normal screen.

---

### Post by jingo811 on 2007-11-09
Well I have never seen a PC output an error message that looks like that so I don't know.

```
the window now i get includes a text input area and an add button. And it talks about local host.
```

---

### Post by jordanmthomas on 2007-11-09
Here's the screen I think he has:
[http://flashlinux.org.uk/screenshot/034/screenshot/034/complex-xdmcp.jpg](http://flashlinux.org.uk/screenshot/034/screenshot/034/complex-xdmcp.jpg)

What happens if you click cancel?

---

### Post by maduranga on 2007-11-09
oh yeh, this is it.Thanks alot. the window appears inside the "Xnet" is what i got. But there was no selectable things like you have (Core-Server, Network-Server).

 When I click cancel, It goes to a black full screen with text on it (just like booting in non graphical mood) and then return to the above screen again.  

 I can login to my pc with recover mood, is there a way to fix this by using recover mood at the grub? :confused:

---

### Post by maduranga on 2007-11-10
> **jingo811 said:**
> Well I have never seen a **PC output an error message** that looks like that so I don't know.

```
the window now i get includes a text input area and an add button. And it talks about local host.
```

Thanks alot for your try to help me. I'm not a Linux Expert. I'm just a beginner. Of course yes, i want to solve my problem. cos it is my problem. and thats why I put this post on ubuntuforums. So what I have told about my problem is what all I can say, Once again, I'm not an Expert like you. If I'm, Then perhaps  I'll be able to fix this with my own. 

 I know there are a lot of helping people in this nice forum. So i thought that one will try to understand my problem and help me to get out of it. and jordanmthomas did it. thanks

 [http://flashlinux.org.uk/screenshot/034/screenshot/034/complex-xdmcp.jpg](http://flashlinux.org.uk/screenshot/034/screenshot/034/complex-xdmcp.jpg) 

 is what i'm getting. 


 **And things that I speaks are not PC output Error Messages**. What I have told there before is an effort to try to describe my problem. 

 thanks for helping.

---

### Post by jordanmthomas on 2007-11-10
Well, normally when you click cancel it takes you to the normal login screen.  I really don't know what your problem could be.

```
sudo dpkg-reconfigure gdm 
```
could possibly fix it back, but I really am not sure what is wrong.  :(

---

### Post by jingo811 on 2007-11-10
Did normal login work before.  Or does this happen everytime you do a fresh Ubuntu installation on your machine?

---

### Post by maduranga on 2007-11-10
It works perfectly for few weeks after the installation. I think I have done something wrong with settings. But I can't remember what I did. Anyway I guess I have change some settings with remote logging.

---

### Post by jingo811 on 2007-11-10
I don't know much about remote logins.  Does that have to do with your ISP company modem connection or is it some private remote login experiments you're doing?

Can you work on your Desktop on this problem machine?
Do you still have Internet connection with this machine?
Can you access a terminal where you can issue commands like
```
$ pwd
```?

---

