---
title: "Wireless Network Key Required"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by kjhud on 2008-02-03
I have Ubuntu running on my external HDD. Whenever its not plugged in, I can access my internet fine through Vista on my Laptop (which I use ubuntu on) and through XP on my desktop.

I have a 10 digit code and I have  put it in many times and when i click connect, it comes back after a few minutes it comes back and then from there it just tries to connect.

Im clicking the icon in the upper right tray and i put:

Network Name: Name
Wireless secruity: WEP 64/128-bit Hex
Key: **********
Authentication: Open System



I know that during the setup I didn't select anything due to me being lazy but code the external HDD be the problem or my drivers? My sound says it's not setup

---

### Post by spiderbatdad on 2008-02-03
you may need wpa-supplicant from synaptic package manager. Also, essid may need to be in quotes.

---

### Post by kjhud on 2008-02-03
Here is what i have

Dell Wireless 1390 WLAN Mini-Card

and I am not doing it in terminal but I will try the quotes

---

### Post by spiderbatdad on 2008-02-03
have you installed wpa-supplicant? also you could post```
sudo lshw -C net
```

---

### Post by kjhud on 2008-02-03
What is the supplicant?

---

### Post by spiderbatdad on 2008-02-03
it is a tool in synaptic package manager, I am 99% certain, you need in order to able to connect to an encrypted network. It negotiates the key with the authenticator.

---

### Post by kjhud on 2008-02-03
[IMG]http://i28.tinypic.com/2aklgtx.png[/IMG]

---

### Post by spiderbatdad on 2008-02-03
good persistence there! the command "ls" is used in many combinations. It basically means "list" So, we were asking for lshw, or, list hardware. (at least that's my understanding.) lspci will list all your pci bridges and connected devices. ls by itself will list the contents of whatever directory you happen to be in. cat will display the contents of a file. So your first command: "sudo /etc/network/interfaces" should have been "cat /etc/network/interfaces." Though that only shows what must always be configured.

---

### Post by kjhud on 2008-02-03
> **spiderbatdad said:**
> good persistence there! the command "ls" is used in many combinations. It basically means "list" So, we were asking for lshw, or, list hardware. (at least that's my understanding.) lspci will list all your pci bridges and connected devices. ls by itself will list the contents of whatever directory you happen to be in. Anyway...Anyway...? ll Are you ut of ideas? If so thx for the attempt

---

### Post by st33med on 2008-02-03
Have you tried this yet?
[http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")

---

### Post by spiderbatdad on 2008-02-03
no no, far from it...the page did not refresh for sometime. I was waiting for you to tell me you had installed wpa-supplicant. correctly entered the essid. and enabled the network through the network monitor applet.

---

### Post by kjhud on 2008-02-03
> **st33med said:**
> Have you tried this yet?
[http://ubuntuforums.org/showthread.php?t=297092]("http://ubuntuforums.org/showthread.php?t=297092")

Thx a bunch! A long but worthy process. Too bad I had no clue what I was doing lol but hopefully with internet now i can learn some stuff..maybe.

---

### Post by kjhud on 2008-02-03
> **spiderbatdad said:**
> no no, far from it...the page did not refresh for sometime. I was waiting for you to tell me you had installed wpa-supplicant. correctly entered the essid. and enabled the network through the network monitor applet.All of my info was correct, the link that the other person provided corrected my issue. Now when I click the icon it shows wireless networks in the area. So I am set now, thx.

---

