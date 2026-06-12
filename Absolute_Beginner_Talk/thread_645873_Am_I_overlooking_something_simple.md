---
title: "Am I overlooking something simple?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by jimmj43 on 2007-12-20
Maybe I'm spoiled, having tried several different Linux OSs where as few as one mouse click on the browser icon was all it took to connect to the internet.

I'm trying to test-drive gOS on another machine (using Gutsy on this one), and I can't find a way to get connected to the internet to save my neck! Neither does there appear to be a built-in tutorial to offer guidance. To reach gOS 'Help' requires an internet connection. I'm trapped in a "Catch 22".

Please be gentle. My command of LinuxSpeak is sharply limited, so type s - l - o - w - l - y.

Thanks

---

### Post by nowshining on 2007-12-20
since ur on the net, did do any gOS googling, been to their forums,etc.. if u are using another computer try going to their forums on the working computer with a internet connection that works and ask for help there, u'll get more responses.

---

### Post by jimmj43 on 2007-12-20
Been there, done that. Even tried the "Other OS" board here. Plenty of questions posted, but very few responses.

FYI: The gOS forums can be accessed here:

[http://www.thinkgos.com/support.html](http://www.thinkgos.com/support.html)


Anybody know what "Terminal Server Client" is/does? It APPEARS to hold some promise..

---

### Post by LaRoza on 2007-12-20
Are you using the live cd?

For me, gOS (on a live cd) made connecting to the internet easy. 

Post the output of 

```

ifconfig

```

(What are you using to connect? Wireless, ethernet, etc?)

(Running the following commands might work (it will renew your ip address from DHCP))

```

sudo dhcpcd -k
sudo ifup eth0

```

---

### Post by jimmj43 on 2007-12-20
I've got it installed and wanting to connect to my hardwired cable connection.

1. I don't know how to run the command (?) you offered. I tried "run command" and typed it into the window and hit 'Enter'. Except for an ocassional wink from the HD LED, nothing happened.

2. But even if I did get some collection of hash, I'd have no way of getting it onto this machine to forward to the board.

---

### Post by nowshining on 2007-12-20
can u open up a terminal, i don't know what terminal or howtwo on gOS so u'll have to find it and then enter ur password with sudo if gOS uses sudo, and if so u may not see the password typed out as u type as this is a security issue, just type it out as normally and then hit the enter key.

if using gnome

in run try typing

gnome-terminal

---

