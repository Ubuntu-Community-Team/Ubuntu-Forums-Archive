---
title: "help diagnosing vnc porb"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by il-luzhin on 2007-05-09
new to ubuntu, never used vnc before.  Trying to get access to my ubuntu home desktop from work xp sp2 machine.  

On home machine typed in 
```

sudo apt-get install vino

```

opened port 5900 on my linksys WRTSL54GS router.

Downloaded RealVNC to work pc, opened RealVNC Viewer.  Typed in 
```

MY IP:5900

```

Got everyones favorite message  Unable to connect.  (Ain't that wonderfully specific!)
Router issue? Vino issue?  MS issue?  Who can say?

Perhaps you?

---

### Post by blackened on 2007-05-09
First a couple of questions: 

Did you enable remote desktop under System -> Preferences -> Remote Desktop?
How is your network arranged? Are the internal machines using static or dynamic addressing?
By "opened port 5900" do you mean that you forwarded it to a specific internal IP or that you set up a port trigger?

---

### Post by il-luzhin on 2007-05-10
I've since gotten to a friend's pc with XP SP2 and it works fine.  Must be a NAT issue on the client side at work.  I'll talk to the <sigh> IT guy tomorrow.

I set it up as per this pages instructions.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

which include the Sytem ->Preference -> Remote Desktop settings.
and I used this page

[http://portforward.com/](http://portforward.com/)

to help set my port forward and triggering at forward/trigger vnc1-5500, vnc2-5800, vnc3-5900

---

### Post by scxtt on 2007-05-10
you don't use <your ip>:5900, you use <your ip>:0 or <your ip>:x (where x is the display # vnc is running under) ...

---

### Post by il-luzhin on 2007-05-11
It seemed to work using IP:5900  is that only because i was already logged in?

---

### Post by scxtt on 2007-05-11
the only time i've seen using port 590* would be if you're doing it through a web browser (and your vncserver has the http extensions active) ... but it still comes down to what 590X server is running ... if you're using a vnc viewer, you enter it in the form:

<host ip>:x
where x is the server connection you're connecting to, 1,2,3, etc. ...

so if you have a vnc server running on :1 and your IP is 123.456.789.10, you'd enter the following into your viewer:

123.456.789.10:1

which will use port 5901 for that IP ...

---

### Post by il-luzhin on 2007-05-14
(and your vncserver has the http extensions active)

how can I tell whether my http extensions are active?

---

### Post by scxtt on 2007-05-15
when you do a **ps -ef | grep vnc** and your result has **-httpd /usr/local/vnc/classes** in it ... also hinges on java being properly set up ...

---

