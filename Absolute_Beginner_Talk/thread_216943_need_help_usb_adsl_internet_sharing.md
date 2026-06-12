---
title: "need help: usb adsl internet sharing"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by shadww on 2006-07-16
hi

today i managed to install ubuntu on my main computer
and succesfully managed to setup eciadsl to work with my lucent cellpipe ADSL modem

iam posting this using my internet connection

everything looks good

but i want to share internet with other network computers
there are 3 computers connected via a hub

can any one help a newbei like me

i tried searching on google, found similar problems but not one that can solve my problem

thanks

---

### Post by rdd on 2006-07-16
You could install Firestarter. It's a desktop firewall and it also has this routing function and you can use it to set up DHCP too.

It is in the repository.

Regards 

rdd

---

### Post by Albi on 2006-07-16
You can't route USB internet connections, your ISP will tell you that.

---

### Post by rdd on 2006-07-16
Why wouldn't you be able to route them? Aren't they treated like normal network devices?

rdd

---

### Post by [S|G] on 2006-07-16
If routing using firestarter doesn't work, you can do that by setting up a proxy on your computer using Squid.
```
sudo apt-get install squid
```
Then take a look at this guide: [http://en.tldp.org/HOWTO/TransparentProxy.html](http://en.tldp.org/HOWTO/TransparentProxy.html)

That will set up a transparent proxy (meaning you won't have to tell the browser on the remote computer that you have a proxy) that should work with virtually any kind of connecion you are using.

---

### Post by shadww on 2006-07-17
thanks for the help

i will try the methods suggested

will reply later with the results :)

*edit*
i was wondering why i get poor speed with my conection
when i use the Synaptic Package Manager or the update manager

although i got a high speed when downloading normally from sites (like 110 kB)

---

### Post by shadww on 2006-07-29
hmm i tried using firestarter but it didn't work

now iam using and ethernet modem so everything looks great

thx everyone

---

