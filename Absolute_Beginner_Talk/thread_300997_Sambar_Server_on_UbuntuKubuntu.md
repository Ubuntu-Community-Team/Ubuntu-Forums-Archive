---
title: "Sambar Server on Ubuntu/Kubuntu?"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by Duffy on 2006-11-16
Has anyone out there in the community installed Sambar on Ubuntu or Kubuntu that can give me some guidance on a few issues? Mainly how to get the autostart script working on Ubuntu or Kubuntu. I'm an newbee on Linux and the install/set-up guide was written for Red Hat and there are enough differences that I cannot figure it out.

I also have some other questions that are more or less basic practices with Sambar.

You can post the solution to the scripting issue here, but for more informal chatting, please email me at duffy (at) wb8nut.com

Thanks,

Duffy

---

### Post by TorenC on 2006-11-16
So, you didn't install samba from the repositories? That really makes things easier.

---

### Post by TheWizzard on 2006-11-16
> **Duffy said:**
> Has anyone out there in the community installed Sambar on Ubuntu or Kubuntu that can give me some guidance on a few issues? Mainly how to get the autostart script working on Ubuntu or Kubuntu. I'm an newbee on Linux and the install/set-up guide was written for Red Hat and there are enough differences that I cannot figure it out.

I also have some other questions that are more or less basic practices with Sambar.

You can post the solution to the scripting issue here, but for more informal chatting, please email me at duffy (at) wb8nut.com

Thanks,

Duffy

i'm using samba, but i don't have a clue about the autostart script you're talking about. we also need more informatio:
- what did you do
- what doesn't work

---

### Post by Duffy on 2006-11-16
Guys thanks, but that did give me a little laugh. I am not talking about "samba" I am talking about "sambar" and the two are very different. (sambar.com) Sambar is an integrated web/mail/ftp/etc. server that is easier to configure than Apache and has a GUI front-end and is more than a web server. Apache is great, but over my head. So please, don't try to sell me on using Apache instead. Been there done that, did not get a t-shirt.

In any, the install is pretty easy, it's the configuration that has me a bit baffled - especially how to autostart it when the system boots.

Thanks,

Duffy

---

### Post by TorenC on 2006-11-16
hehehe. I didn't even notice the r on the end there. Well, to start things on boot usually you'd put the script to start it in /etc/init.d/, and then create symlinks (ln -s) in the correct runlevel folder (probably /etc/rc2.d, but that's just a guess...) called S??nameofapp, where the ?? are the order that you'd want it to run in, 99 is always safe. So you'd make a link called something like S99sambar. 

This is probably only mostly correct. I would suggest looking around a bit more on the forums and the wiki, and make sure that what I've told you makes sense.

---

### Post by Duffy on 2006-11-17
Yes, that's my big issue right now. I have the script in the inet.d directory, but I don't know what to do from there to create the "symbolic" link.

That's one nice thing about windoz is that you have a start-up directory to just drop the program icon into and it just works. You don't have to do anything else. I wish you could do that with Linux.

So if anyone can help me with what I need to do with the script that is currently in the inet.d directory to get it to work, that would be most appreciated.

---

### Post by TorenC on 2006-11-18
you can create links with ln. try ```
man ln
``` in a terminal. To make symbolic links, use ```
ln -s
```
If you wanted to make a symbolic link from /etc/init.d/foo to /etc/rc2.s/S99foo, you'd type 
```
ln -s /etc/init.d/foo /etc/rc2.s/S99foo
```

---

