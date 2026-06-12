---
title: "setting up proxy"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by kyury on 2006-01-25
Hy you guys,
Not only i am new to ubunto - Im olso new to linux world...
My problem is like this:
I am able to surf the net (like posting this thread), and download packeges throu the synaptic.
But when im type a command like "apt-get update" or "ping X.X.X.X" i get dont get nothin.... like im not even connected.
I am sitting behind a proxy, and i am able to send ping to other guys on my network - and they are able to do "apt-get".
The question is - do i need to define the proxy server for the "apt-get"??
If so - Then how....
If not - Then what?

Thenks!

---

### Post by alamba on 2006-01-25
Yes you do need to define the proxy server for synaptic. Not sure where it is though. 

Akshay

---

### Post by public_void on 2006-01-25
I'm behind a proxy as well, you have to edit the file /etc/apt/apt.conf, and add your proxy settings in there. Heres how in the terminal

cd /etc/apt/ (Changes the directory to /etc/apt/)
cp /etc/apt/apt.conf /etc/apt/apt.conf_backup (Copies the file apt.conf to the same directory be renames it apt.conf_backup. This is incase you make a mistake, you don't have to do that command)
sudo gedit apt.conf (Opens apt.conf in a text editor and allows you to edit it)
Add the lines

```
ACQUIRE {
http::proxy "http://[UserName]:[Password]@[ProxyAddress]:[Port]/"
}
```

If your proxy does not requires authentication then leave "[UserName]:[Password]@" out.

Save the file and exit the terminal.
Try sudo apt-get update. It should be able to connect to the respo servers and update.

Pinging another computer can fail for a couple of reasons. The target computer may not be replying to ping request. Or the target computer is replying, but your proxy doesn't forward the packets to you. You can ping other people on the network because the packets are sent across the network, with nothing intercepting them.

---

