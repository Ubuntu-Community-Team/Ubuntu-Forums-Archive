---
title: "stumped"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by rocket.7777 on 2007-11-20
Hi I am a newbie. I have a zoom 56k V.92 V.90 modem that gnomeppp detects I have registered an account with uklinux entered the necessary info and.... nothing!  the modem dials then fails to authenticate? pap secrets and chap secrets?. I cannot veiw these in the file system they have a little icon by them. please help me, my eyes are square and brain is melting.

---

### Post by natehatewindows on 2007-11-20
i had the same problem after installing my linuxant driver, this fixed it for the most part but it still fails to authenicate from time to time....this means for some reason either kppp(i use kppp not gpp and you should too because there is a bug in gpp in gusty) does not send username/password or the server at the isp does not accept it...

here is how to fix you problems i think....

[http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

---

### Post by natehatewindows on 2007-11-20
oh and just for your info..

you will get mre replys to your thread if you use a descriptve name, lot of people are stumped but maybe try "stumped by blah blah blah" :)

good luck!

---

### Post by rocket.7777 on 2007-11-20
Thanks for reply not sure about the "then i repeated dialout" is that hitting connect using gnomeppp??
I'm lost here??


There cure was to (under Ubuntu)
$ sudo chmod a+rw /etc/ppp/pap-secrets
with other distros if would be
$ su - root
# chmod a+rw /etc/ppp/pap-secrets
[COLOR="Red"]Then I repeated the dialout[/COLOR], successfully,during which
there was written to  /etc/ppp/pap-secrets   a line
MyLoginName\@worldnet\.att\.net   *       MyPassword

I restored the original permissions with:
# chmod a-rw /etc/ppp/pap-secrets
# chmod u+rw /etc/ppp/pap-secrets
with result
$ ls -l  /etc/ppp/pap-secrets
-rw------- 1 root root 1827 2006-11-03 22:43 /etc/ppp/pap-secrets

---

### Post by rocket.7777 on 2007-11-20
First time I've used a forum too so thanks for the advice on thread names glaringly obvious really now i've thought about it! Cheers

---

### Post by natehatewindows on 2007-11-20
```
sudo chmod a+rw /etc/ppp/pap-secrets
```

thats all i did

the rest i didnt do.... :)

and i did this too

```
sudo chmod a=rw /etc/ppp/chap-secrets
```

to be honest im not sure this was the right thing to do but it has been working great for a couple months so i think its ok and safe.

---

### Post by natehatewindows on 2007-11-20
if gppp is not wokring try to use wvdial

go to a terminal and 
```
&wvdial
```

if it does not work copy and paste everything it says and ill see if i can help you.

if you have another connection to the computer do 
```
sudo apt-get install kppp
```

its another, better dialer

---

### Post by rocket.7777 on 2007-11-21
thanks for your help i will continue to try and sort the dialup but went through a wireless router and had no trouble connecting so I'm happy for now cheers again.:)

---

### Post by natehatewindows on 2007-11-22
anytime....

so now your just using wifi? with a dsl connection?

let me know how everything goes :)

---

### Post by rocket.7777 on 2007-11-22
Hi back again I got the kppp dialer and a new ISP phone number, configured it and it works (hurrah!) but firefox doesn't "see" the connection... I know it's connected but the computer doesn't?? is this because firefox is looking for the broadband connection? if so how do you point it elswhere?
On a another note I simply plugged then network cable in my router and got internet access straight away ! your now wondering why i want dial up right? well i'll explain...I would like my mum to be able to have a machine that can access email for minimall cost. 
cheers again.:)

---

### Post by natehatewindows on 2007-11-22
thats really strange. how do you know if you are online or not? i have never had firefox do this. see if you can ping a site...we wil get this working for your mom :)

are you going to use ubuntu too?

---

### Post by gubemton on 2007-11-22
-sorry, post by mistake- mods, please delete.

---

### Post by rocket.7777 on 2007-11-22
well i don't know i'm online but the connection is made and the timer is running, bearing in mind all i'm doing is disconnecting my router (network cable) and plugging in a usb dialup modem, to then dial up an isp.
Does firefox connect automatically to any available connection or does it need configuration? on dialup up does it simply take longer than the timeout allows for?
Also yes i'm using ubuntu too although i'm finding the learning curve quite steep so i still have windows to browse the forums whilst figuring out the other machine (probably frowned on by purists but you gotta do what you gotta do hey!)

---

### Post by rocket.7777 on 2007-11-22
oops forgot to ask - how do you ping a site??
cheers

---

### Post by natehatewindows on 2007-11-22
im not sure but it think you just go to a console and put

```
ping www.yahoo.com
```

and that will ping yahoo if your really online. 

a couple questions:

1. Did you hear the modem dial?
2. did you reboot after unplugging from the router (if not try that)
3. what kind of usb modem are you using?
please post the out come of the command below with the modem plugged into a USB port.

```
lsusb
```

the learning curve is steep, even totally vertical at times but once you start to use linux a lot you have no choice but to learn....so just keep trying :)

EDIT: and whatever you get back from the ping please post too, but just the first few lines will matter.. thanks!

---

### Post by rocket.7777 on 2007-11-22
Ok I set up a clean install loaded modem driver loaded repositories got ubuntu updates and kppp etc. dialed isp, pinged yahoo and it all worked (hurrah!) opened firefox and we were off.... brilliant! what a journey!

 PING [www.yahoo-ht3.akadns.net](www.yahoo-ht3.akadns.net) (87.248.113.14) 56(84) bytes of data.
64 bytes from f1.us.[www.vip.ird.yahoo.com](www.vip.ird.yahoo.com) (87.248.113.14): icmp_seq=1 ttl=58 time=406 ms
64 bytes from f1.us.[www.vip.ird.yahoo.com](www.vip.ird.yahoo.com) (87.248.113.14): icmp_seq=2 ttl=58 time=401 ms
64 bytes from f1.us.[www.vip.ird.yahoo.com](www.vip.ird.yahoo.com) (87.248.113.14): icmp_seq=3 ttl=58 time=388 ms
64 bytes from f1.us.[www.vip.ird.yahoo.com](www.vip.ird.yahoo.com) (87.248.113.14): icmp_seq=4 ttl=58 time=385 ms

dialup still doesn't work on my machine but i have broadband so not bothered really i'll get to it one day! thanks for your interest and help all the best,
 cheers

---

### Post by natehatewindows on 2007-11-23
sweet! congrats! good luck and i hope your linux journey gose well and i hope you mom enjoys her emails :)

---

