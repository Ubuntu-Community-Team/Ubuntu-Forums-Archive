---
title: "2 quick Terminal questions"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by thedevilisbad on 2006-02-20
How do I set my password for the terminal?

And

If I load GNOME PPP on a jump drive how do I install it from the terminal?

Thanks

Aaron

---

### Post by Madpilot on 2006-02-20
[QUOTE=thedevilisbad]How do I set my password for the terminal?
[/quote]

Not sure what you mean... the password when you use sudo in the terminal is the same as the one in the GUI apps - your own user password, the one you gave when you installed Ubuntu.

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)
> 
If I load GNOME PPP on a jump drive how do I install it from the terminal?


That depends what format the application is in. If it's a .deb file, you use "sudo dpkg -i <name of file>.deb". The best way to install stuff is through Synaptic or apt-get from the online repositories, though.

[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)
[https://wiki.ubuntu.com/AptGetHowto](https://wiki.ubuntu.com/AptGetHowto)

---

