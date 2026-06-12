---
title: "I did something stupid..."
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by ionizd on 2008-02-01
Hello everybody,
 I did something stupid, and now I must pay. I deleted all the information in the wireless connection' hosts tab. I was having trouble with a connection and I wanted to make it refresh the info, but it never did. My wireless still works, although I had to remove and re-install the networking utility to get it to work, but every time I boot my laptop I get a warning that my laptop's address cannot be found and I should enter it into my /hosts /etc file. How do I fix this?

---

### Post by emarkd on 2008-02-01
What does 

```
cat /etc/hosts
```

produce?

---

### Post by airbornemist6 on 2008-02-01
You could always ask nicely for someone to donate a default file to you. I would but I need to get home to do that. So if you don't mind waiting 2 hours I can get that for you. Or, you could also put your wireless back into roaming mode. Or, another way, do a complete uninstall of your network manager from synaptic, and then reinstall it and your configuration files should be back to default (in theory, in reality this only works about 70% of the time).

---

### Post by ionizd on 2008-02-01
> **emarkd said:**
> What does 

```
cat /etc/hosts
```

produce?

 The result is this: [COLOR="DarkRed"]# The following lines are desirable for IPv6 capable hosts[/COLOR]
 Can't I just edit the file to reflect the missing entry? How do I do it? I tried entering the following code:
"sudo gedit /etc/hosts"
 but that doesn't look right and doesn't work anyway.

---

### Post by emarkd on 2008-02-01
Well, you should at least have a 

```
127.0.0.1 localhost
```

in there.  Try editing the file and making that the first line of the file.

---

### Post by ionizd on 2008-02-01
> **emarkd said:**
> Well, you should at least have a 

```
127.0.0.1 localhost
```

in there.  Try editing the file and making that the first line of the file.

 Sooo... How do I do that? I can't remember how to open a text editor in root.

---

### Post by Dr Small on 2008-02-01
Try:
```
gksudo gedit /etc/hosts
```

---

### Post by eljalill on 2008-02-01
sudo nano /etc/hosts 

opens in nano though...

but sudo gedit /etc/hosts works for me too... different from gedit nano will just make the file, if it doesn't exist though (which is possibly what you want?)

---

### Post by ionizd on 2008-02-01
I'm using Xubuntu... is there another text editing program I need to be using? Gedit doesn't seem to work for me.

---

### Post by emarkd on 2008-02-01
I think the default there is mousepad instead of gedit

---

### Post by ionizd on 2008-02-01
Yep, mousepad is the text editor, but I added the following lines;
"127.0.0.1 localhost" with no effect. Then I tried "ionizd-laptop", which is the name of my machine and was specifically what the error advised I enter into /etc/hosts, also with no effect.

---

### Post by Tteddo on 2008-02-01
> **ionizd said:**
> Yep, mousepad is the text editor, but I added the following lines;
"127.0.0.1 localhost" with no effect. Then I tried "ionizd-laptop", which is the name of my machine and was specifically what the error advised I enter into /etc/hosts, also with no effect.

Try:
> 127.0.0.1 localhost
127.0.1.1 ionizd-laptop

That's what is in mine (with my machine's name).

---

### Post by ionizd on 2008-02-02
The problem appears to be solved. I had the network configuration utility installed, so I used it to enter the following information under Network>Wireless connection>Hosts>Properties;
"127.0.0.1" under IP address,
"localhost" under aliases, and;
"127.0.1.1" under IPaddress,
"ionizd-laptop" under aliases.
 Thank you all for your assistance!

---

