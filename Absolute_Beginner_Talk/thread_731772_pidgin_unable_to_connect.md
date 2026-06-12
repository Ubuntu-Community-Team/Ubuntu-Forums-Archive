---
title: "pidgin unable to connect"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by hellomoto on 2008-03-22
hey, i don't norm start new posts but have been unable to find a solution to my problem via searching the forums.

problem: im trying to use pidgin 2.2.1 on MSN protocol but its failing to connect.


I know I am correctly connected to my WiFi network, I have also disabled IPv6 but this hasn't helped. My pidgin settings are as follows:

```
Protocol: MSN
Screen name: My email address.
Password: My password
Server: messenger.hotmail.com
Port: 1863
Proxy type: No proxy
```

When I try to connect with these settings Pidgin trys to connect for about 2 mins, then appears to time out and i get the following error:

```
''Connection error from Notification server:
Unable to connect''
```

Any ideas why it isn't working?

many thanks

---

### Post by jan quark on 2008-03-22
try this:

[https://answers.launchpad.net/ubuntu/+question/13016](https://answers.launchpad.net/ubuntu/+question/13016)

---

### Post by hellomoto on 2008-03-22
hi this hasn't worked im afraid, any other surgestions?

---

### Post by timbounceback on 2008-03-22
if it hasnt worked, be sure to put your permissions back but with a + instead of a -

---

### Post by hellomoto on 2008-03-22
thankyou...  thats now answered a very embarrassing post in networking and wireless!


any other idea about how to get pidgin to work?

---

### Post by hellomoto on 2008-03-23
I still am unable to get pidgin to connect. I have noticesd that the only software that to be able to connect to the internet is firefox and thats after i diasabled IPv6.

Is anything in network settings under the host tab stopping other apps connecting? 

or is there some other firewall control on ubuntu?
or is this a settings apps settings issue?

---

### Post by koptastic on 2008-03-25
Im not sure if this will help as im new to the whole Ubuntu world. However i found i could not connect and had all the right details as do you have entered. Then found i had firestarter installed and that the port for msn was not on the allowed and outgoing lists. Once i added the correct port i could sign in, this may be of no relevance to you but thought i would share what i found out in case its to some use for somebody.

---

