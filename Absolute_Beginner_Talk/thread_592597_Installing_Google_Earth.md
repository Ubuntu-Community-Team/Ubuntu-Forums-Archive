---
title: "Installing Google Earth"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by thelugnut on 2007-10-26
I have downloaded "GoogleEarthLinux.bin.

I don't know how to install it.

Can some kind soul help me out here?

Thanks

---

### Post by maybeway36 on 2007-10-26
Do this instead:
[http://www.google.com/linuxrepositories/ubuntu704.html]("http://www.google.com/linuxrepositories/ubuntu704.html")

---

### Post by Pumalite on 2007-10-26
Right clik on the file. Make it 'executable'. Then doubleclick on it. Google does the rest

---

### Post by petegreenhorn on 2007-10-26
i think you could have just : [COLOR="Blue"]sudo apt-get install google earth [/COLOR]

---

### Post by Maestro23 on 2007-10-26
> **petegreenhorn said:**
> i think you could have just : [COLOR="Blue"]sudo apt-get install google earth [/COLOR]

Close:

> sudo apt-get install googleearth

Installing Software in Ubuntu:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by por100pre1 on 2007-10-26
> **Maestro23 said:**
> 

[B] Originally Posted by petegreenhorn  View Post
i think you could have just : sudo apt-get install google earth[/B]

Close:

```
sudo apt-get install googleearth
```

Installing Software in Ubuntu:

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository and then install as previously posted. :)

---

### Post by Maestro23 on 2007-10-26
> **por100pre1 said:**
> Add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository and then install as previously posted. :)

Thanks por100, should mentioned that as well. :)

---

### Post by thelugnut on 2007-10-27
Son-of-a gun !

Thanks for the replies.

This one worked for me, first time:

> sudo apt-get install googleearth

Great forum, great people, great answers.

---

### Post by radar654 on 2007-10-27
> **maybeway36 said:**
> Do this instead:
[http://www.google.com/linuxrepositories/ubuntu704.html]("http://www.google.com/linuxrepositories/ubuntu704.html")

yeah I did it as the guide there says and after I went to Synaptic and installed it but I cannot find google earth in any folder under 'Applications' :confused:

---

### Post by upthelum on 2007-10-27
> **radar654 said:**
> yeah I did it as the guide there says and after I went to Synaptic and installed it but I cannot find google earth in any folder under 'Applications' :confused:

I'm not sure if this will work but try typing "goggle earth" in terminal to see if that will run it. Can someone correct me if i'm wrong...

---

### Post by Maestro23 on 2007-10-27
> **upthelum said:**
> I'm not sure if this will work but try typing "goggle earth" in terminal to see if that will run it. Can someone correct me if i'm wrong...

I believe it will be: googleearth

Could be wrong though.:)

---

### Post by upthelum on 2007-10-27
> **Maestro23 said:**
> I believe it will be: googleearth

Could be wrong though.:)

I installed it with, apt-get and ran"googleearth" but it kicked me out and went back to my user logon screen, so i promptly took it back off...

---

### Post by DwnNdrty on 2007-10-28
> **radar654 said:**
> yeah I did it as the guide there says and after I went to Synaptic and installed it but I cannot find google earth in any folder under 'Applications' :confused:

It should be in the Internet sub-folder of Applications.  Are you using Ubuntu 7.10 (Gutsy) ?

---

