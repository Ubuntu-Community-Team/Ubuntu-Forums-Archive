---
title: "X-Chat IRC"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by Sonlc on 2006-04-07
Hi there.  I'm pretty new to linux, and have been getting great help from everyone in the Ubuntu channel.  The problem I have is that the X-Chat application quit today, and will no longer start up.  I think I was trying to change the default colour of the chat box at the time, and when I made a change, it shutdown.  When I try to start it up again, nothing happens. 

I've tried uninstalling it through the add/remove function, and then reinstalling it again, but it makes no difference.

Can anyone help at all?

Thanks alot!

---

### Post by Kindred on 2006-04-07
Odd, might be worth deleting the .xchat (or similarly named) folder in your home directory and trying again.

(it's a hidden folder)

---

### Post by Juippisi on 2006-04-07
And if the problem continues you could open terminal and try to start X-Chat from there. I think the command is something like "xchat2". Just type "xcha" and press the tabulator. Then paste error-message here.

---

### Post by Sonlc on 2006-04-07
hehe, thanks for the quick reply.  I've enabled hidden folders view in my preferences, but I'm having trouble tracking down the file you suggested I remove.  I've tried /home/ and /home/sonic.  I dont see anything in there at all to do with xchat.  Sorry if I'm being dumb.

---

### Post by Sonlc on 2006-04-07
[QUOTE=Juippisi]And if the problem continues you could open terminal and try to start X-Chat from there. I think the command is something like "xchat2". Just type "xcha" and press the tabulator. Then paste error-message here.[/QUOTE]


Ahh, thanks, I tried what you suggested with this.  This is the error I recieved:

```
The program 'xchat-gnome' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 291 error_code 17 request_code 129 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```   :-k

---

### Post by mangz74 on 2006-04-07
you can also search if from you terminal

just open terminal and type

sudo cd ~/.xchat2
ls 

thats should list the files in the xchat2 hidden directory, thats if xchat is installed and delete what u need to delete.

Better yet, why not just reinstall xchat after deleting that folder?

---

### Post by Sonlc on 2006-04-07
```
sonic@Ghost:~$ sudo cd ~/.xchat2
sudo: cd: command not found

```

:(

---

### Post by barebones on 2006-04-07
Try using that command without using sudo, I've never needed root privilages to change directories.

---

### Post by Juippisi on 2006-04-08
Okay, now you could trying to delete your ~/.xchat2 directory. 

After that, open up a terminal and type "sudo apt-get remove xchat-gnome" and when that's finished, type "sudo apt-get install xchat xchat-common". I've heard that xchat-gnome doesn't work properly so you could try installing "the real" X-Chat.

---

### Post by Rekiem on 2007-05-01
Hello people...

Well I'd been reading all about the details described in here, and right now I'm behind a proxy connection.
I made all the settings, and well I checked them.
> 
irc_whois_front..............: OFF
 net_auto_reconnect...........: ON
 net_auto_reconnectonfail.....: OFF
 net_bind_host................: 
 net_ping_timeout.............: 0
 net_proxy_auth...............: OFF
 net_proxy_host...............: 3.34.221.71
 net_proxy_pass...............: 
 net_proxy_port...............: 80
 net_proxy_type...............: 4
 net_proxy_use................: 0
 net_proxy_user...............: 
 net_reconnect_delay..........: 10


I got this writing a /set on the status window.

And well this proxy as you may suppose doesn't has authentication neither password it is a simple HTTP-Proxy for the company.
The funny thing is that still with this, the xchat-gnome ignores that and, just cant go out to reach the server...
And this is what I got...

> 
Equipo desconocido. ¿Quizá se ha equivocado?
 Ciclando al siguiente servidor en DALnet...
 Desconectado ().
 irc.dal.net
 Equipo desconocido. ¿Quizá se ha equivocado?
 Ciclando al siguiente servidor en DALnet...
 Desconectado ().
 irc.eu.dal.net
 Equipo desconocido. ¿Quizá se ha equivocado?


Sorry about the Spanish, but I have my Ubuntu in Spanish language.
The thing in here (translated) says "
Host unknown, Maybe you made a mistake?
Looping to the next server in DALnet...
Disconnected().
irc.eu.dal.net
Host unknown. Maybe... bla bla

So... do you think that I miss something?
Please help me out.

Thanks in advance!

As mexican people says "Viva Ubuntu" =)

---

