---
title: "Just installed Ubuntu today..."
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by wham on 2005-12-04
Hello, I am extremely new to using Ubuntu (first day) and find it's really not hard to use at all. My printer worked right away, my internet started up quick, and it's layout is really cool. 

I do have a couple questions; with Windows I was used to downloading a program from a site and then finding it and double-clicking it to install. Will it be like that with Ubuntu? I read the thread about programs that people can use that are like programs used with Windows and got curious as to if they are the same program just for Ubuntu, or are they just similar.

Thanks for any help.

---

### Post by aysiu on 2005-12-04
[QUOTE=wham]with Windows I was used to downloading a program from a site and then finding it and double-clicking it to install. Will it be like that with Ubuntu?[/QUOTE] Read the second link in my sig.

After you get used to that, you may want to take a peek at the first link in my sig.
Then, read this: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by wham on 2005-12-04
Thanks, that was very helpful. 

The only problem I'm encountering is that I searched for gtkpod, marked it for installation, and it says "Depends: libid3tag0 (>=0.15.1b) but it is not installable." I then followed the link in your signature for enabling extra repositories but when I typed in what it told me to in the terminal it asked for a password (in the terminal, not the adminastrator pw) and wouldn't let me type in anything. Now I'm lost.

On the plus side, nicotine installed with no problems.

---

### Post by Perfect Storm on 2005-12-04
Did you type in your login password? It should be the same.

---

### Post by cwaldbieser on 2005-12-04
[QUOTE=wham]Thanks, that was very helpful. 

The only problem I'm encountering is that I searched for gtkpod, marked it for installation, and it says "Depends: libid3tag0 (>=0.15.1b) but it is not installable." I then followed the link in your signature for enabling extra repositories but when I typed in what it told me to in the terminal it asked for a password (in the terminal, not the adminastrator pw) and wouldn't let me type in anything. Now I'm lost.

On the plus side, nicotine installed with no problems.[/QUOTE]
When you type the password in the terminal, it is invisible (no *'s are echoed).

---

### Post by wham on 2005-12-04
OK, it worked. All the programs I wanted were installed. I love it! Thanks.

Another question; What do I use for security? Firewalls, Anti-Virus programs?

---

### Post by Gray. on 2005-12-04
to install firewall:
```
sudo apt-get install firestarter
```
to install virus-scanner:
```
sudo apt-get install aegis-virus-scanner
```

There are other alternatives available. Just search in Synaptic (System > Administration > Synaptic Package Manager).

---

### Post by linbetwin on 2005-12-04
[quote=wham]OK, it worked. All the programs I wanted were installed. I love it! Thanks.

Another question; What do I use for security? Firewalls, Anti-Virus programs?[/quote]

You don't really need antivirus software in Linux, unless you run is as server and need to protect Windows computers that connect to your server.

---

