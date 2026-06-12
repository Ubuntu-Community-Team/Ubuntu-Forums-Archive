---
title: "lo? wifi0? Athos? so many choices fo0r wireless..."
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-09-27
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot.png[/IMG]

Just a bit confused... What is lo? I have both a built in intel wireless chip and a Netgear wireless PCMIA (sp?) so, those "unknown" interfaces... wifi and atho... should I use wifi instead of lo? I know that atho is my netgear card....

I've had strange problems... like... a month ago my internal wireless would not even work. its about 50% faster then my card that I am plugging in...

Should I be using the wifi0 setting?? Whats lo???

static void

edit: btw it is automatically using the lo interface

---

### Post by thomashauk on 2007-09-27
lo is the loopback, its connects your computer to itself. Don't ask me why but I'm sure it has a use.

---

### Post by nb123 on 2007-09-27
I though lo was for a modem connection?

---

### Post by nb123 on 2007-09-27
I just read something that says the following: ---

"You will notice that at least one network connection is present on your system - the "lo" interface. This is the loopback interface and is common to all systems connected to a network. The loopback interface is a virtual interface and never goes down. It 's primary function is to allow the functioning of the TCP/IP stack on the OS without the presence of a network card."

Could someone with more experience please explain what the the exact purpose of it is?

---

### Post by nb123 on 2007-09-27
Okay, found this: ---

> A loopback interface has several uses. It may be used by network client software on a computer to communicate with server software on the same computer–viz., on a computer running a web server, pointing a web browser at the URL [http://127.0.0.1/](http://127.0.0.1/) will access that computer's own web site. This can be done without the computer being connected to any network–so it is useful for testing services without exposing them to remote network access. Likewise, to ping the loopback interface is a basic test that one's IP stack is working properly.

---

### Post by staticvoid on 2007-09-27
so...
should I not connect to lo, rather to wifi0 ?

...no apache for me :)

nate

---

### Post by Malibu Illusion on 2007-09-27
You should clearly be using the wifi0 device for Wi-Fi access.

---

### Post by staticvoid on 2007-09-28
well it is using lo and it works... so clearly not? I will try stuff then mark this silly thread [SOLVED

sv]

---

