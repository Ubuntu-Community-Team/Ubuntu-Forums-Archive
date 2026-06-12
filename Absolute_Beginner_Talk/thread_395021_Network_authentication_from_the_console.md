---
title: "Network authentication from the console"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by idain on 2007-03-27
I'm a complete newb with Ubuntu.

I just managed to get it installed yesterday have many issues - namely, I was trying to use the LiveCD, but the Xserver doesn't work on my comp (AMD64 w/ ATI x700 agp), so I had no way of installing from that.

So, I switched to the alternative CD, and got Ubuntu installed.  Xserver is still non-functional.  So I am trying to install the ATI drivers, and hopefully see if that will straighten out my issue.

The network I am on uses Cisco Clean Access for network authentication.  From linux, I should just be able to login by opening a webpage and entering my password.  But, since I have no GUI, and have to do everything from the console, I have no idea whether it is possible to enter my username and password.  If I can't get internet access, I can't use sudo apt-get update, and can't get my graphics card installed.

Does anyone know of a way for me to login through the console?

Thanks

---

### Post by Falados on 2007-03-27
I made a script to authenticate myself on a web server periodically.  It went something like this

wget --http-user=MyUsername --http-passwd=MyPassword [http://authentication_site](http://authentication_site)

You can also use wget for posting information in http (Like submitting a form)
read 'man wget' for all the info.

some text browsers are available too:

lynx
links
links2

---

### Post by idain on 2007-03-27
Thanks :)

---

### Post by cowlip on 2007-03-27
do the 'vesa' drivers not work on your card?

---

### Post by idain on 2007-03-28
vesa drivers do not work.  i managed to get xserver working with the vga drivers . . . but that has complications of its own.

---

