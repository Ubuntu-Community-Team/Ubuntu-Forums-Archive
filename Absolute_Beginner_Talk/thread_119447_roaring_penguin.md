---
title: "roaring penguin"
date: 2006-01-19
forum: Absolute Beginner Talk
---

### Post by firefly123 on 2006-01-19
Hi Have found a driver for my usb modem
When i try to install driver it says i need roering penguin
Have tried to install but dont have c compiler set in $path

Advise please

If i get this sorted i will write about the experence of getting the BT modem asdl to run as this is supplied by aol and have noticed alot of threads on aol,usb,adsl.

---

### Post by paulmilliken on 2006-01-19
Please post the exact error message that is being reported as it is difficult to diagnose from this information alone.

Paul

---

### Post by firefly123 on 2006-01-19
hi error message is
david@dg2:~/Desktop/rp-pppoe-3.7$ ./go
Running ./configure...
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
Oops!  It looks like ./configure failed.

hope you can help
have looked for $path cant find

Yours David

---

### Post by majikstreet on 2006-01-19
sudo apt-get install build-essential

*I think that's it*

you need gcc and make, too.

---

### Post by Qrk on 2006-01-19
Did you install the build-essential from synaptic?

If not, do that

sudo apt-get install build-essential

---

### Post by firefly123 on 2006-01-19
aaaahhhhh
cant use apt as cant connect to internet via ubintu is there a web site i can go to when logged in in xp

---

### Post by majikstreet on 2006-01-19
packages.ubuntu.com can get you packages, but for something big like build-essential, I think you'd probably want to get the computer on the internet..

Are you sure there isn't a .deb for the program you need?

---

### Post by firefly123 on 2006-01-19
hi
no deb but canot get on to net without rp-pppoe will try web site post again tommorow

cheers

---

### Post by gamerchick02 on 2006-01-19
I had almost the same problem...  I'd just ditch the USB modem and get a serial one.  It's much easier.  I don't advocate giving up, but the serial modem takes about five seconds to configure.  The one I have is a Creative Blaster V.92 Serial DE5621.  It's about 60$US at BestBuy, but it's worth it in setup time and finding drivers time, as there are no drivers to find.  Also, it will work with Windows, if you're doing a dual-boot scenario, as I'm doing.

Hope that helps you a little bit!

Amy

---

### Post by firefly123 on 2006-01-24
have found a .deb and have installed it but cant find the files What command line do i use in terminal to get started????

---

### Post by twodees on 2007-03-27
> **rpgirl said:**
> I had almost the same problem...  I'd just ditch the USB modem and get a serial one.  It's much easier.  I don't advocate giving up, but the serial modem takes about five seconds to configure.  The one I have is a Creative Blaster V.92 Serial DE5621.  It's about 60$US at BestBuy, but it's worth it in setup time and finding drivers time, as there are no drivers to find.  Also, it will work with Windows, if you're doing a dual-boot scenario, as I'm doing.

Hope that helps you a little bit!

Amy

  That's good news.  In my preparation for installing Ubuntu, that's the serial modem I bought today.  If posting to an old thread bumps a topic back to the top, maybe this will help someone who is wondering which serial modem is an actual hardware modem.  I called Creative's tech support and was given a url to Creative's open source driver site:

[www.opensource.creative.com](www.opensource.creative.com)

  haven't browsed it yet, the site seemed to be down earlier.

---

