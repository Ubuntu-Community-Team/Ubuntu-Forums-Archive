---
title: "Can't connect to msn network"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Delaylama on 2007-09-19
Hello

Since yesterday i'm having problems connecting to the msn network by any client ... (until yesterday it worked fine and then: i couldn't write to any contact. i tried to reconnect and couldn't even connect to the server anymore and i'm (quite) sure i didn't change anything)
The Error msg is just: "connection time out."  I read some posts about moblock. and other posts. I tried to fix it with these but i noticed that i don't have any moblock files. I even don't know what it is :) ... I' using a direct connection to the internet (not wlan) and firefox and the other stuff using the internet is working fine. (i wrote this post in ubuntu). i checked if there are new versions of the msn clients. Everything i tried didn't help -.-
In windows (on the same machine) it worked fine to connect to msn.

Could anyone give me an advice (I'm nearly goin' crazy)
Thank you.
Regards

---

### Post by kerry_s on 2007-09-19
i'm not sure i understand.

try using firefox in safe mode and see if that works.
press alt+f2 type>  **firefox -safe-mode **

---

### Post by Delaylama on 2007-09-19
yes that worked

---

### Post by Delaylama on 2007-09-19
What do you think you didn't understand? Maybe i can help you to help me :)

---

### Post by atria on 2007-09-19
This is weird stuff. Pidgin works perfectly here.

I'm not exactly sure what would help in your case but i would clear the existing preferences and do a complete reinstall of the client.

It might be also due to an offending firewall rule; try disabling the firewall to test if msn works?

---

### Post by Delaylama on 2007-09-19
Ok i will try to reinstall every messenger ... 
I don't think it's a firewall problem because i tried it in windows on the same machine and same network and it worked fine... but if it is then i think i can't do anything because i'm in the business network ^^ and they mangage the firewall so i couldn't disable it 

but anyway thank you for your help

---

### Post by lode on 2007-09-19
I've got the same problem: Pidgin won't connect to the MSN network on my laptop (running Gutsy) or on the family PC (running Feisty). Both times it says 'e-mail@adress.internet disconnected: Connection error from Notification server: Unable to connect'.

Until yesterday everything worked as to be expected, on both computers (so it's not a temporary Gutsy thing).

Could anyone please explain the modlock thing so I can give it a shot? (This is Absolute Beginner Talk, if I'm not mistaking :P)

---

### Post by Delaylama on 2007-09-19
i still got no reason for this -.-
reinstalling hasn't changed anything (btw, how can I delete everything? the gaim profiles were still there when i reinstalled gaim) 
my nerves are really messed up right now -.- anything i tried didn't work...

---

### Post by tenjin1 on 2007-09-19
If you have Moblock installed then it most certainly is blocking connection to MSn because same thing happened to me. Try:

   1. ```
sudo gedit /etc/moblock/MoBlock-nfq.sh
```
   2. Found the line: WHITE_TCP_OUT=”http https”
   3. Added 1863 (MSN Port #) to that line, like this: WHITE_TCP_OUT=”http https 1863&#8243;
   4. Saved the file and closed it.
   5.  ```
sudo /etc/init.d/moblock-nfq restart
```

In Gaim, you can see what port its using to connect to msn. Also you can add any other ports there in that line if you feel they are being blocked too.

---

### Post by tenjin1 on 2007-09-19
> **Delaylama said:**
> i still got no reason for this -.-
reinstalling hasn't changed anything (btw, how can I delete everything? the gaim profiles were still there when i reinstalled gaim) 
my nerves are really messed up right now -.- anything i tried didn't work...

You can completely remove left over folders that are out there somewhere by searching for each folder and deleting them:

```
sudo find / -name gaim
```

then,

```
rm -rf each of the gaim folders.
```

---

### Post by Delaylama on 2007-09-19
Ok it works now.. but i don't know exactly why :D yesterday i made a ubuntu system update and maybe since this update the connection failed because not all package dependencies were updateted too or anything else. A friend of mine told me to excecute apt-get update and after that gaim was connected ^^
I think that was the problem. Sry about your costs and thanks for the help


tenjin1: Thank you. Although this commands are useful for me :)

---

### Post by tenjin1 on 2007-09-20
> **Delaylama said:**
> tenjin1: Thank you. Although this commands are useful for me :)

Your welcome. Let me know if you have anymore problems :)

---

