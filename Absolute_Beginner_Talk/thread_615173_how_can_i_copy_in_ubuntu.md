---
title: "how can i copy in ubuntu??"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by kokophone on 2007-11-16
hi all

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

in this web!!!

i want to copy it but I  can't....

sudo cp ~/downloads/alsa* .>>this line..

my download folder is in my current Desktop...

how can I do??:( helo!!!!!:(

---

### Post by Inxsible on 2007-11-16
> **kokophone said:**
> hi all

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

in this web!!!

i want to copy it but I  can't....

sudo cp ~/downloads/alsa* .>>this line..

my download folder is in my current Desktop...

how can I do??:( helo!!!!!:(you have to first cd into the directory. Did you execute the command just before the line which says ```
cd /usr/src/alsa
```

---

### Post by spiderbatdad on 2007-11-16
Not sure what it is you are trying to do. You can save the page under the file tab. If you want to copy the lines of code, do so by selecting them, ( dragging your cursor with the left mouse button depressed) then right click on the selected text and choose copy. Go to the command line and paste the code where you want it.

---

### Post by Gazneth on 2007-11-16
Not sure exactly what you need,  you can copy the line by highlighting it and right click then copy, then paste it into a text program of your choice.  I use Tomboy notes for this, it is installed already.  Simply right click on one of your panels and click add to panel, at the dialog drag Tomboy notes back to your panel.  This will allow you to save terminal codes for later and copy and paste as needed.

---

### Post by kokophone on 2007-11-16
how do i copy my download file to
usr/sr/alsa???
i can't for it

---

### Post by taurus on 2007-11-16
> **kokophone said:**
> how do i copy my download file to
usr/sr/alsa???
i can't for it

```
sudo cp **filename** /usr/src/alsa
```

p.s.  I see that you have another thread asking the same thing.

---

### Post by santiagoward2000 on 2007-11-16
> **kokophone said:**
> how do i copy my download file to
usr/sr/alsa???
i can't for it

I think you have to use sudo privileges. Just open a terminal and type:
```
sudo nautilus
```

Just be careful of what you do.

---

### Post by taurus on 2007-11-16
> **santiagoward2000 said:**
> I think you have to use sudo privileges. Just open a terminal and type:
```
**sudo nautilus**
```

Just be careful of waht you do.

```
gksudo nautilus
```
should be better.

---

### Post by santiagoward2000 on 2007-11-16
> **taurus said:**
> ```
gksudo nautilus
```
should be better.

HI!
Could you explain the difference, please?

---

### Post by Inxsible on 2007-11-16
> **santiagoward2000 said:**
> HI!
Could you explain the difference, please?
here you are

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by taurus on 2007-11-16
> **santiagoward2000 said:**
> HI!
Could you explain the difference, please?

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by santiagoward2000 on 2007-11-16
> **Inxsible said:**
> here you are

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

> **taurus said:**
> [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Thank you both! :)

---

### Post by kokophone on 2007-11-16
thank you all 
now it is ok for copy
:popcorn:

---

