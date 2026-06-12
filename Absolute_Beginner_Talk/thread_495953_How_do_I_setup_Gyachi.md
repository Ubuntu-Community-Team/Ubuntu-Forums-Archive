---
title: "How do I setup Gyachi?"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by babya on 2007-07-08
Hi, 

I just installed Gyachi (ver 1.0.5-1) from my Synaptic, but not sure how to set it up.

On the login box it shows:

> Username:
Password:
Room:  Linux, FreeBSD, Solaris:1
Server:                 
5050



1. Do I just use my Yahoo IM name/pass?

2. What is the "Room"?  Just leave it to what it's already selected to?

3. Do I need to choose a server?  If so, which one?

4. What is the "5050" and do I just leave it at that?

5. Last, when I downloaded it, it showed no Icon in the apps list.  How boring is that?  Can I give it the purple penguin (or whatever it is) icon?  If so, how?


I want it to replace Yahoo Messenger.

[Edit]

6.  How do I set up my webcam?

---

### Post by overdrank on 2007-07-08
> **babya said:**
> Hi, 

I just installed Gyachi (ver 1.0.5-1) from my Synaptic, but not sure how to set it up.

On the login box it shows:




1. Do I just use my Yahoo IM name/pass?

2. What is the "Room"?  Just leave it to what it's already selected to?

3. Do I need to choose a server?  If so, which one?

4. What is the "5050" and do I just leave it at that?

5. Last, when I downloaded it, it showed no Icon in the apps list.  How boring is that?  Can I give it the purple penguin (or whatever it is) icon?  If so, how?


I want it to replace Yahoo Messenger.
HI and 
1. yes your user yahoo id and password
2. is the chat room that it logs you into
3.Yahoo im
4.yes just leave it 
5. Yes boring and cant help you there
Good luck:lolflag:

---

### Post by babya on 2007-07-08
> **overdrank said:**
> 
3.Yahoo im

5. Yes boring and cant help you there
3. Well I just choose the 1st option and it worked!
5. Nooooooooooo!

---

### Post by corney91 on 2007-07-08
> **babya said:**
> 
5. Last, when I downloaded it, it showed no Icon in the apps list.  How boring is that?  Can I give it the purple penguin (or whatever it is) icon?  If so, how?


You can edit menus with alacarte:

```
sudo alacarte
```

---

### Post by overdrank on 2007-07-08
> **corney91 said:**
> You can edit menus with alacarte:

```
sudo alacarte
```

Thanks ):P

---

### Post by babya on 2007-07-08
Ok, so how do I get my webcam to work?

I see a line in the "setup" tab that says:

> Webcam Device:   /dev/video0

Do I have to set it to something different if my webcam doesn't seem to appear?  My cam worked with Kopete.

---

### Post by loell on 2007-07-08
> **babya said:**
> Ok, so how do I get my webcam to work?

I see a line in the "setup" tab that says:



Do I have to set it to something different if my webcam doesn't seem to appear?  My cam worked with Kopete.

the default should work, mostly ;)  

just plug your webcam , then in "Actions menu" ---> "start my webcam"
then see if your webcam shows up..

---

### Post by babya on 2007-07-08
My cam is not working for some reason.  My friend's cam works though (they're using Yahoo IM btw).  Any thoughts to why mine's not?  It worked fine with Kopete.

---

### Post by loell on 2007-07-08
whats the name of your webcam? 
probably the webcam is V4L2 compatible only, hence it worked in kopete..

---

### Post by babya on 2007-07-08
> **loell said:**
> whats the name of your webcam? 
probably the webcam is V4L2 compatible only, hence it worked in kopete..
It's a Logitech QuickCam Chat.

---

### Post by loell on 2007-07-08
hmm, according to the spca5xx page its also v4l1 compatible , its not yet confirmed though. they are still testing it.

> Logitech 	119 	0x046d 	0x08a3 	QuickCam Chat 	  	zc030x 	???? 	Test 	Jpeg 	spca5xx/LE gspca v4l1/v4l2 	*

---

### Post by babya on 2007-07-08
> **loell said:**
> hmm, according to the spca5xx page its also v4l1 compatible , its not yet confirmed though. they are still testing it.
Dang.  You have link to that so I can see which cams are compatible?

---

### Post by loell on 2007-07-08
[http://mxhaard.free.fr/spca5xx.html]("http://mxhaard.free.fr/spca5xx.html")

its a long list :popcorn:

---

