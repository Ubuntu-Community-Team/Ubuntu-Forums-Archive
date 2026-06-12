---
title: "Gaim"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by fidoliedo on 2006-07-08
I'm basically a Windows Tech moving to Linux. I just downloaded ubunto desktop and so far I like it. However, I am not able to make GAIM work. the version I have installed with ubuntu is 1.5x and I tried to update to BETA 2.0. I've uninstalled completely but the Beta keeps saying that it needs somre sort of SSL library. I don't have a clue what this is or where to get it.

---

### Post by teet on 2006-07-09
[https://help.ubuntu.com/community/Gaim_2.0_Beta_3_Quick_Install](https://help.ubuntu.com/community/Gaim_2.0_Beta_3_Quick_Install)

This may help.  I haven't upgraded to the beta yet myself since 1.5 works just fine for my needs.

-teet

---

### Post by fidoliedo on 2006-07-09
Hi, thanks for your help and information. I did go to the link and reloaded it through terminal. But here is the error I still get:

<diablo800@hotmail.com (MSN) was disconnecte due to an error. SSL support is needed for MSN. Please install a supported SSL library. See [http://gaim.sf.net/faq-ssl.php](http://gaim.sf.net/faq-ssl.php) for more information. the account has been disabled. Correct the error and reenable the account to connect.

---

### Post by kc5hwb on 2006-07-09
Gaim runs AIM, MNS, Yahoo and ICQ?  I thought it was just AIM?  But I am new to Ubuntu also.

---

### Post by teet on 2006-07-09
Yeah...it supports all of those...they should really change the name so it isn't quite so confusing.

Back to the original question.  I just opened up synaptic and did a search for "SSL" filtered by Name only.  It came back with a lot of stuff.  This is sort of a shot in the dark, but make sure libssl0.9.8, libssl-dev, openssl, ssl-cert, and libgnutls12 are installed.

From the terminal that would be
```
sudo apt-get install libssl0.9.8 libssl-dev openssl ssl-cert libgnutls12
```

Hope this helps.

-teet

P.S.  You may need to have the universe/multiverse repos enabled to install these things.

---

### Post by fidoliedo on 2006-07-09
I'll give it a shot and see where it takes me. I've got Yahoo running fine, just MSN doesn't seem to connect without SSL. I'll give those suggestions a try.

---

### Post by fidoliedo on 2006-07-09
Yeah, still doesn't work. I guess I'll just use two programs. it would be nice if I could get it to work but seeing as how it's beta, I guess I'll have to wait for the final. The windows alternative is Trillian and that works great. I am really liking this ubuntu stuff.

---

### Post by teet on 2006-07-09
Just to clarify...you did recompile and install GAIM again after installing the SSL libraries?  Because I think you'll need to do that, but I could be mistaken.

-teet

---

### Post by fidoliedo on 2006-07-09
Hi TEET,

Your talking to a total newb here. Ask me anything about Windows and I can help out, but I'll figure this out somehow. So, how does this compile thing work? I've seen this:

$ ./configure --enable-gnutls=yes
$ sudo make
$ sudo make install 

But it didn't work for me. I got an error on the first line. Not sure if that's for ubuntu

---

### Post by fidoliedo on 2006-07-09
I uninstalled GAIM beta 2 and reloaded the old 1.5 and performed some sort of update. suffice it to say, it's up and working. Thanks for all the help. I feel confident that with the help of all of you, maybe one day I'll be the one helping others.

---

