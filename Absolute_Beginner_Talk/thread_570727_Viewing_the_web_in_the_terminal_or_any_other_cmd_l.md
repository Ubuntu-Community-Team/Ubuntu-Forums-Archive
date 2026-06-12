---
title: "Viewing the web in the terminal or any other cmd line interface"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Roen hayden on 2007-10-08
Viewing the web in the terminal or any other cmd line interface.

Hey i was wondering if there is any way to do that.  I know that you can download programs that and in in the terminal you typ the name of the program then the web site EX.

>  w3m [www.google.com](www.google.com)

but i was wondering if there is a way to access the web like this with haveing to download any program. is there a Linux Cmd that can be used on all Linux OS's to even do this? And what would be windows equivalent if you know of it.

thanks

---

### Post by Seisen on 2007-10-08
The only way to access a website from the terminal would be to use someting like links or lynx. Most of these have a very small footprint anyway so you woulnd't even really notice it.

---

### Post by Roen hayden on 2007-10-08
i not worried about it taking up room or anything. i just want to see if it can be done.  What if these programs don't exist one day? how could you do it then?

---

### Post by klange on 2007-10-08
> **Roen hayden said:**
> i not worried about it taking up room or anything. i just want to see if it can be done.  What if these programs don't exist one day? how could you do it then?
The day Lynx ceases to exist is the day no one - anywhere - uses a terminal or cares about how a website would look on the simplest of displays. I'd assume that would be never.
You could write a program yourself to communicate with an HTTP server, get a response, cut the html code out of it (or use it to some effect), and then print that to the terminal, all just using simple sockets.

---

### Post by Roen hayden on 2007-10-08
i have to say this does nerve me a little....y cant you view the web in the terminal without dl a program to do it.....

---

### Post by cmargolin on 2007-10-09
Well, you could, if you would like to send HTTP protocol text to port 80.

---

