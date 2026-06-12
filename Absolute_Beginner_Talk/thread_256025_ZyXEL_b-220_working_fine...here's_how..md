---
title: "ZyXEL b-220 working fine...here's how."
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by DarkN00b on 2006-09-12
I've noticed there have been a few posts in this forum about the ZyXEL b-220 wireless USB dongle.  Most people have had a very hard time getting this thing to work in Dapper Drake.  Here's how I did it, and it is very easy.

I got my Zyxel B-220 working in Dapper Drake 6.06LTS!

Instructions:
1. Go to the [ Linux ZD1201 Sourceforge page ]("http://linux-lc100020.sourceforge.net/")and download the 0.14 firmware package.  
2. Extract this package into its own directory
3. Open a terminal window and navigate to that directory.
4. Type 'make'.  That is all I needed to do to install the firmware. The "Install" file takes care of the rest, I think.

The only problem is that at least one of the files was sent to the wrong place.  OH NOES!

No problem, that's easy to fix...
Next, go [here]("http://oase.uci.ru.nl/~bradaa/nerdnotes.org/index.php/category/nerdnotes/linux/") and scroll down to "E-Tech Wireless USB Adapter and Linux".

Basically, the guy says to install the firmware as above, then open a terminal window and navigate to the directory where you downloaded the firmware then type (still in Terminal):

```
sudo cp *fw /lib/firmware/`uname -r`
```

Type it _exactly_ like that. In fact -- copy that and paste it into Terminal and hit enter.  As soon as I did, my B-220 lit up and started searching for a connection.

Now.  Open System->Administration->Networking.  You should see a new connection called "Wireless Connection".

Now...
1. Click the new connection and then click the Properties button.
2. Enter your WLan's ESSID under "Network name (ESSID):" ****This is case sensitive!****
3. Click OK and you should be connected after the changes are made to the connection.

**This worked for me.  My wireless ZyXEL B-220 is now working!**

---

### Post by Najand on 2006-09-12
Good job dark! Sounds fantastic to me.

---

